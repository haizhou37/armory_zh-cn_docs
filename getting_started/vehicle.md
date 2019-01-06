# 车辆设置

这个文档是基于[Panda3D Bullet Vehicle Doc](https://www.panda3d.org/manual/index.php/Bullet_Vehicles)，同过提供了更多的主题来讨论一些常见的面临的问题。

本文讨论了基于光线投射的车载开箱式Bullet Physics实现。这种车辆的优点是比约束型车辆更容易实现。

这种方法在一些街机游戏中使用。

下面的文章详细介绍了车辆模板实现的高级别，并提供了一些可选的建议(因为这些建议并不是在每种实现类型中都是泛型的)。

最初的车辆模板设置可以在[Armory3D模板](https://github.com/armory3d/armory_templates)

在`vehicle`物体上有个脚本和它密切联系。

### 设置车辆

下面的代码是这样做的，根据它们的名字，在场景中获取所有的轮子对象，并将它们推入一个数组中。
```
for (n in wheelNames) {
    wheels.push(iron.Scene.active.root.getChild(n));
}
```
用`vehicle`物体下的网格作为复合设置车辆车身

```
var wheelDirectionCS0 = BtVector3.create(0, 0, -1);
var wheelAxleCS = BtVector3.create(1, 0, 0);

var chassisShape = BtBoxShape.create(BtVector3.create(transform.dim.x / 2, transform.dim.y / 2, transform.dim.z / 2));

var compound = BtCompoundShape.create();

var localTrans = BtTransform.create();
localTrans.setIdentity();
// set to much lower value
// https://pybullet.org/Bullet/phpBB3/viewtopic.php?t=12112
localTrans.setOrigin(BtVector3.create(0, 0, 1));

compound.addChildShape(localTrans, chassisShape);

carChassis = createRigidBody(chassis_mass, compound);
```

创建车辆物理对象，根据车辆的当前信息将车身和车轮连接在一起。

*注意：重要的是要注意的是，虽然车辆演示使用父母/子女关系，一旦他们成为物理世界的一部分，他们就不再是父子关系(除非通过物理约束)。例如，车轮可能从原来的父/子位置滑落到基于物理相互作用的“车辆”物体。*

```
//创造车辆
var tuning = BtVehicleTuning.create();
var vehicleRayCaster = BtDefaultVehicleRaycaster.create(physics.world);
vehicle = BtRaycastVehicle.create(tuning, carChassis, vehicleRayCaster);

//永远停用车辆
carChassis.setActivationState(BtCollisionObject.DISABLE_DEACTIVATION);

//选择坐标系
var rightIndex = 0;
var upIndex = 2;
var forwardIndex = 1;
vehicle.setCoordinateSystem(rightIndex, upIndex, forwardIndex);

//添加车轮
for (i in 0...wheels.length) {
	var vehicleWheel = new VehicleWheel(i, wheels[i].transform, object.transform);

	vehicleWheel.isFrontWheel = true;
	if (i >= wheels.length - 2) {
	    vehicleWheel.isFrontWheel = false;
	}

	vehicle.addWheel(vehicleWheel.getConnectionPoint(), wheelDirectionCS0, wheelAxleCS, suspensionRestLength, vehicleWheel.wheelRadius, tuning,
           vehicleWheel.isFrontWheel);
}

//安装车轮
for (i in 0...vehicle.getNumWheels()) {
    var wheel:BtWheelInfo = vehicle.getWheelInfo(i);
    wheel.m_suspensionStiffness = suspensionStiffness;
    wheel.m_wheelsDampingRelaxation = suspensionDamping;
    wheel.m_wheelsDampingCompression = suspensionCompression;
    wheel.m_frictionSlip = wheelFriction;
    if (i >= wheels.length - 2) {
        wheel.m_frictionSlip = wheelFriction * 1.2;
    }
    wheel.m_rollInfluence = rollInfluence;
}
		
physics.world.addAction(vehicle);
```

#### 防止车辆翻车

*注：这是一项可供选择的建议*

取决于游戏类型，可能有一些情况下，人们不希望车辆翻转，即使在高速驾驶。

开箱即用的汽车实现是朝着更现实的行为，其中转向更高的速度(或硬角/较轻的车身等.)就像翻车。

有多种方法来防止它，下面是一种可能的方法[Bullet Forum Discussion](https://pybullet.org/Bullet/phpBB3/viewtopic.php?t=8153)

在添加`vehicle`到物理世界之前，在`carChassis`后面加上：
```		
// https://pybullet.org/Bullet/phpBB3/viewtopic.php?t=8153
// prevent vehicle from flip over, by limit the rotation  on forward axis
carChassis.setAngularFactor(new BtVector3(0,0,1));
		
physics.world.addAction(vehicle);
```

以上的角度因子限制了x轴和y轴上的旋转，因此车辆将无法旋转，因为底盘物体将平衡翻转力。

这可能会使车辆变得不太现实，因为即使在高速急转弯时，它也始终是稳定的。

### 加速

为了加速，应用发动机给(也可以想出一种类似的扭矩)车轮`i`施加力。
该索引是根据车轮被添加到车辆的顺序来确定的。
```
 vehicle.applyEngineForce(engineForce, i);
```

发动机转速负值最终会导致车辆倒车，也可以用来减速车辆。

##### 寻找当前车速

*注：这是一个可选的建议*

在某些情况下，可能需要找到当前的车速，可以通过以下操作：
```
var speed = Math.round(vehicle.getCurrentSpeedKmHour());
```
以每小时公里为单位的更容易的开箱即用方式。

以下是另一种得到和上面相似的值的方式，通过使用车轮旋转差值得到车辆移动的速度。
```
var speed = Math.round(((backendWheelInfo.m_deltaRotation / Time.step) * backendWheelInfo.m_wheelsRadius * 3.6));
```

##### 限制最高速度

*注：这是一项可供选择的建议*

如果在车轮上继续施加力，车辆的速度会不断增加，在某些情况下这可能并不理想，因为理论上说，车辆速度存在瓶颈。

在这种情况下，您可以执行以下操作：
```
var speed = Math.round(vehicle.getCurrentSpeedKmHour());
if (speed < MAX_SPEED)
{
    engineForce = maxAcceleration * chassis_mass * accel;
}
else 
{
    engineForce = 0;
}
```

以上计算出车辆的当前速度，然后不再允许更多的发动机力提高速度。
这种方法可能不会100%地阻止车辆以最大速度行驶，但它应该限制该区域的速度。

### 刹车

为了减速，应用制动给(也可以想出一种类似扭矩)车轮`i`添加力。
该索引是根据车轮被添加到车辆的顺序来确定的。
```
vehicle.setBrake(breakingForce, i);
```

相反的引擎力`-1 * engineForce`也可用于减速车辆。但制动/负动力的行为可能适合不同的情况。

请随时进行实验，并找到最佳的合适方法。

刹车将导致车辆最终在0停止，而负发动机的力量将开始逆转。

### 转向

转向值在0到1之间，并适用于车轮响应的车轮`i`。
该索引是根据车轮被添加到车辆的顺序来确定的。

```
vehicle.setSteeringValue(vehicleSteering, i);
```

#### 前后轮

*这是一个可选的建议。*
模板使用直接编号来映射车轮，但是如果目标是前轮将是唯一旋转的，一种方法是使用`m_bIsFrontWheel`变量。
```
if (wheelInfo.m_bIsFrontWheel)
{
    // apply front wheel logic
    vehicle.setSteeringValue(vehicleSteering, i);
}
else
{
    // apply backend wheel logic
	vehicle.applyEngineForce(engineForce, i);
	vehicle.setBrake(breakingForce, i);
}
```

### 用物理模拟更新图形

以上加速/转向改变物理世界车辆位置。
但是需要将这种反馈应用于图形

跟踪所有车轮，应用必要的转向/加速，并使用物理位置/旋转来更新图形位置/旋转。

```
for (i in 0...vehicle.getNumWheels()) {
   // update accelration/brake/steering
...

    vehicle.updateWheelTransform(i, true);
            			
    var trans = vehicle.getWheelTransformWS(i);
    var p = trans.getOrigin();
    var q = trans.getRotation();
    wheels[i].transform.localOnly = true;
    wheels[i].transform.loc.set(p.x(), p.y(), p.z());
    wheels[i].transform.rot.set(q.x(), q.y(), q.z(), q.w());
    wheels[i].transform.dirty = true;
...
}
```

也适用于底盘和相机。

```
var trans = carChassis.getWorldTransform();
var p = trans.getOrigin();
var q = trans.getRotation();
transform.loc.set(p.x(), p.y(), p.z());
transform.rot.set(q.x(), q.y(), q.z(), q.w());
var up = transform.world.up();
transform.loc.add(up);
transform.dirty = true;

// TODO: fix parent matrix update
if (camera.parent != null)
    camera.parent.transform.buildMatrix();
camera.buildMatrix();
```

#### 车轮/底盘在高速期间关闭

*这是一个可选的建议。*

开箱即用的车辆模板，如果一个人以非常高的速度移动车辆，人们可能会注意到车轮的转动速度比底盘慢(至少是图形化的)。

虽然它可能适用于某些游戏，但可能不适用于其他游戏。

造成这种现象的原因是由于物理轮物理计算逻辑似乎发生在另一个线程上，因此实际车轮转动/位置响应与底盘物理计算之间存在一定的延迟。

为了强制车轮，需要改变上面的一个逻辑

`On updateWheelTransform`为车轮`i`更新为假。

```
// 使车轮与底盘世界Transform同步
// update the second parameters to false to let the wheel stay at chasis
 vehicle.updateWheelTransform(i, false);
```

还有更优雅的回调实现方法，但在本文编写时，HaxeBullet还不支持车辆车轮的自定义回调方法。

就这样-你可以自由地做进一步的实验了！获得本教程的全部Blend内容：

- https://github.com/armory3d/armory_templates

