# 参考

## 逻辑

### 交替

当它被重新激活时，在其激活的输出之间交替通过它的输入.

![](/assets/Alternate.JPG)


### 数组循环

它循环遍历数组中分配的每个项。`Value`给出由索引值指定的项。`Done`在遍历数组时调用连接器。

![](/assets/array-loop.JPG)


### 分支

激活时，根据插入布尔值的状态，激活其`Ture`或`False`输出。

![](/assets/Branch.JPG)


### 闸门

逻辑节点执行`if`语句的方法。激活时，它将比较它的两个输入是相等的、大的相等的、小于等于的还是不相等的，而不管变量类型如何，如果SET状态是这样的话，则通过红色输入。

`And`或`Or`仅用于布尔，当两个布尔为true（and）或至少一个（or）时，通过输入。

![](/assets/Gate.JPG)


### 相反

布尔会变成对立面，真会变假，假会变成真。

![](/assets/Inverse.JPG)


### 是真或假

根据节点的说法，只有当插入的布尔值为`True`或`False`时，才能通过它的激活。

![](/assets/Is-true_false.JPG)


### 是空值

给出NULL的布尔值，也就是说，如果它是NULL，那么它的输出为`True`(没有值)，如果它不是NULL，那么它输出`False`(有值)。

![](/assets/is-none.JPG)


### 不是空值

给出相反的NULL值，即如果它不是NULL，那么它的输出为`True`(有值)，如果它是NULL，那么它输出`False`(没有值)。

![](/assets/is-not-none.JPG)


### 循环

它是基本的(i in from...to)循环。`Index`给出由索引值指定的值。`Done`在循环完成时被调用。

![](/assets/Loop.JPG)


### 循环终止

Loop Break终止包含它的循环。 

![](/assets/loop-break.JPG)


### 合并

“New”按钮创建新输入，“X”按钮删除最底层的输入。如果它从任何一个输入接收激活，它将激活它的输出。

![](/assets/Merge.JPG)


### 否定

反转插入的布尔值，因此如果输入为`True`，则输出`False`。

![](/assets/Not.JPG)


### 序列

其调用输出按顺序排列。

![](/assets/Sequence.JPG)


### 切换

检查输入`in`上的值，当输入值与`case 1、case 2`或`case 3`值匹配时，它将触发相应的`case 1、case 2`或`case 3`。单击`New`以添加更多的`Case`。

![](/assets/Switch.JPG)


### 转成布尔

在输入中没有事件时为`False`，当输入上有事件时为`True`。

![](/assets/to-bool.JPG)


### 在……期间

它的循环只要在`Condition`中指定的bool是相同的(i.e., like  while(jumping == true){do domething})。

![](/assets/While.JPG)


### 休眠

在它被激活后的秒内激活节点与其输出连接后的浮点值。

![](/assets/sleep.JPG)


## 事件

### 事件

激活连接到其他节点树中指定的`Sent Event`或`Sent Global Event`的节点。

![](/assets/on-event.JPG)


### 初始化

激活在游戏的第一帧上连接到它的节点。

![](/assets/On-Init.JPG)


### 计时器

从游戏开始时，在计时器倒计时之后，激活连接到的节点，当方框打勾时重复。

![](/assets/On-Timer.JPG)


### 每帧更新

激活每个帧连接到它的节点。

![](/assets/On-Update.JPG)


### 体积触发器

下面的对象输入至Volume，上面的对象输入作为和它进入/离开/重叠的物体。 

进入模式：激活对象进入体积的帧上的连接节点，而在所有其他帧上，它不会激活。

离开模式：激活对象离开体积的帧上的连接节点，而在所有其他帧上，它不会这样做。

重叠模式：激活对象与体积重叠的帧上的连接节点，在所有其他帧上不激活。

![](/assets/on-volume-trigger.JPG)


## 触发器


### 鼠标

根据设置的不同，启动、按住或释放设置鼠标按钮时，激活连接到它的节点。

![](/assets/On-Mouse.JPG)


### 键盘

启动、按住或释放设置键盘按钮时，激活连接到它的节点，具体取决于设置。

![](/assets/On-Keyboard.JPG)



## 状态

### 鼠标

如果设置按钮当前正在启动，则输出布尔，按住、释放、移动（True）或不移动（False)。

![](/assets/Mouse.JPG)


### 鼠标坐标

将屏幕鼠标的X，Y位置及其运动输出为向量，如果滚动轮向上移动（1）或向下移动（-1），则输出整数。

![](/assets/Mouse-Cords.JPG)


### 键盘

如果设置按钮当前正在启动，则输出布尔，按住，释放（True）或不释放（False）。

![](/assets/Keyboard.JPG)


### 得到变换

输出设置对象的当前变换。对象变换由想量组成，用于全局定位、旋转和缩放。

![](/assets/get-transform.JPG)


### 得到位置

将设置对象的当前全局位置作为向量输出。

![](/assets/get-location.JPG)


### 得到旋转

将设置对象的当前旋转输出为向量。

![](/assets/get-rotation.JPG)


### 得到缩放

将设置对象的当前标度作为向量输出。

![](/assets/get-scale.JPG)


### 得到物体

搜索场景中具有设置名称的对象并输出它。

![](/assets/get-object.JPG)


### 得到可见性

根据当前可见性设置输出一个布尔值。如果是不可见的，则为假，如果可见，则为真，即使该物体现在不在摄像机上。

![](/assets/get-visible.JPG)


### 得到子类

使用当前为设置对象的子对象的设置名称搜索对象并输出该对象。

![](/assets/get-child.JPG)


### 得到所有子类

将设置对象的所有当前子对象输出为对象数组。

![](/assets/get-children.JPG)


### 得到父类

输出设置对象的当前最近父级。

![](/assets/get-parent.JPG)


### 得到群组

搜索一组具有设置名称的对象，并将其作为对象数组输出。

![](/assets/get-group.JPG)


### 群组

以数组的形式输出集合组中的所有对象。

![](/assets/group.JPG) 


### 得到距离

将两个集合对象之间的当前距离作为浮点类型输出。

![](/assets/get-distance.JPG)


### 得到特性

搜索具有设置名称的特性，该属性应用于设置对象并输出它。

![](/assets/get-trait.JPG)


### 得到已激活相机

Outputs the current active Camera in your game as object.

![](/assets/active-camera.JPG)


### 得到已激活场景

Outputs the currently active scene in your game.

![](/assets/active-scene.JPG)


### 得到体积触发器状态

较低的对象-输入为体积，上部的作为对象-输入，进入/离开/与之重叠的对象。

进入模式：在对象进入体积的帧上输出True，在所有其他帧上输出False。

离开模式：在对象离开体积的帧上输出True，在所有其他帧上输出False。

重叠模式：在对象与体积重叠的帧上输出True，在所有其他帧上输出False。

![](/assets/Volume-trigger.JPG)


## 值

### 得到属性

可以用来接收其他对象的属性，这些对象是通过[`设置属性`](/logic-nodes/set-property.md)节点设置的。属性名称和对象必须与此节点的输入相匹配。

![](/assets/Get-property.JPG)


## 变量

### 动作


![](/assets/Action.JPG)


### 布尔

存储布尔值。布尔值只有两种状态：True和False。

![](/assets/boolean.JPG)


### 颜色

存储RGB/HSV/HEX格式的颜色值。
 
![](/assets/Colour.JPG)

 
### 动态

 
![](/assets/Dynamic.JPG)  


### 浮点型

存储浮点值。浮点变量是一个小数有限的数字。如果你的数字有超过3个小数，所显示的值将被四舍五入，但当你点击它时，你仍然可以看到整个数字，这也将在游戏中使用。

![](/assets/float.JPG)


### 全局对象

提供对全局对象的访问，该对象可用于在不同特性之间共享信息。

![](/assets/global-object.JPG)


### 群组

以数组形式获取存储在组(`物体`选项卡下)中的值。

![](/assets/Group.JPG)


### 整型

存储整数值。这些是整数。

![](/assets/Integer.JPG)


### 材质

获取任何指定对象的材质。

![](/assets/Material.JPG)


### 网格

获取指定网格的引用。

![](/assets/Mesh.JPG)


### 物体

获取指定物体的引用。

![](/assets/Object.JPG)


### 四元数

存储四元数值。

![](/assets/Quaternion.JPG)


### 场景

获取指定场景的引用。

![](/assets/Scene.JPG)


### 根场景


![](/assets/scene-root.JPG)


### 字符串

存储字符串值。

![](/assets/String.JPG)


### 特性

获取制定特性的引用。

![](/assets/Trait.JPG)


### 变换

以变量形式存储位置、旋转、缩放值。

![](/assets/Transform.JPG)


### 向量

将X，Y，Z值存储在向量中。

![](/assets/Vector.JPG)


## 动作

### 设置变量

激活后，将插入的第一个变量更新为第二个变量的值。自动转换某些变量类型。

![](/assets/set-variable.JPG)


### 移动物体

根据给定的向量每帧移动设置的物体。

![](/assets/translate-object.JPG)

### 设置属性

激活时，将以其字符串输入命名的给定对象的属性设置或更新为其常规变量INPUT\(绿色输入)的值。您不必担心变量类型，您可以插入除激活之外的所有内容。

This node can be used to share Variables between different Traits. If the trait\(s\) you want to access the variable with are on different objects, use the "[Global Object](/logic-nodes/global-object.md)" node to store the data. Every trait can access this one.

![](/assets/set-property.JPG)


## Physics

### Apply Force

This apply force to the object assigned, where "Force", is direction force is applied in term of Vector.

![](/assets/apply-force.JPG)


### Apply Force at Location

This applies force to the object assigned, where "Force", is direction force is applied in term of Vector, and where "Location", is the location of the object where force is applied from in term of Vector.

![](/assets/apply-force-at-location.JPG)


### Apply Impulse

This apply impulse to the object assigned, where "Impulse", is direction force is applied in term of Vector.

![](/assets/apply-impulse.JPG)


### Apply Impulse at Location

This applies force to the object assigned, where "Impulse", is direction force is applied in term of Vector, and where "Location", is the location of the object where force is applied from in term of Vector.

![](/assets/apply-impulse-at-location.JPG)


### Cast Physics Ray

This cast physics ray from vector assigned to "From", to vector assigned to "To". "Hit" give the location of an object(object assigned to "Object") it hit to in term of vector.

![](/assets/cast-physics-ray.JPG)


### Get Contacts

This Get contacts of the object with item in the array.

![](/assets/get-contacts.JPG)


### Get First Contact

This Get contact of the object with another object that is assigned with the connector.

![](/assets/get-first-contact.JPG)


### Get Gravity

This Get gravity of an object in term of vector.

![](/assets/get-gravity.JPG)


### Get Velocity

This Get Linear and Angular velocity of an object in term of vector.

![](/assets/get-velocity.JPG)


### Has Contact

This gives bool value of contact between two objects that are assigned,i.e., If both objects contact each other than this gives True, and if not it gives False.

![](/assets/has-contact.JPG)


### On Contact

Contact between two objects that are assigned to:
1) Overlaps - When this two object completely overlap each other, then the "Out" connector is called.
2) End - When this two objects contact ends, then the "Out" connector is called.
3) Begins - When this two objects first contact, then the "Out" connector is called.

![](/assets/on-contact.JPG)


### Pick Object

When the object that is assigned to is in "Screen Coords" (Screen coord is coordination of screen in (X, Y) in term of vector. Note: "Z" is not used and should be ignored because we don't have 3D screen.) and then "Hit" is called to do something to it.

![](/assets/pick-object.JPG)

### Set Gravity

On activated, this set gravity in term of vector.

![](/assets/set-gravity.JPG)


### Set Velocity

On activated, this set:
1) The linear velocity of the object that is assigned to.
2) Linear Factor velocity of the object that is assigned to.
3) The angular velocity of the object that is assigned to.
4) Angular Factor velocity of the object that is assigned to.
In term of vector.

![](/assets/set-velocity.JPG)


## Sound

Note: Different between Pause Speaker and Stop Speaker, is that Pause speaker will just pause the speaker and can be resumed by Play Speaker. While Stop Speaker will completely stop it and cannot be resumed by Play Speaker, on doing so the speaker will play sound/music from start.

### Pause Speaker

On activating this pause speaker(Object that is assigned to as speaker) from playing sound.

![](/assets/pause-speaker.JPG)


### Play Sound

On activated this play sound/music that is assigned to.

![](/assets/play-sound.JPG)


### Play Speaker

On activated this start speaker(Object that is assigned to as speaker) to play sound.

![](/assets/play-speaker.JPG)


### Stop Speaker

On activated this stop speaker(Object that is assigned to as speaker) to stop playing sound.

![](/assets/stop-speaker.JPG)


## Canvas

Note: To get the canvas, be sure that the node\(s\) and the canvas(UI) is attached to the same object.

### Canvas Set Text

On activated it changes the text of element(button, label, etc.).

![](/assets/canvas-set-text.JPG)
