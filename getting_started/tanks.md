# 坦克游戏

<iframe width="560" height="315" src="https://www.youtube.com/embed/5b97eR5_fQI?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

我们来做个小游戏吧！它将包括2名玩家操纵坦克并且互相战斗。我们建造了一个有障碍物和两辆坦克模型的小操场。每个物体都有一个刚体。一些障碍是动画的时间线，以使游戏更有活力。照明设置基于[场景教程](/getting_started/playground.md).

![](/getting_started/img/tanks/1.jpg)

红色坦克充当玩家1。我们允许键盘和游戏手柄控制，但为了简单起见对实际使用的键位采用硬编码。在**Player1Controls**节点树中, 键盘或游戏手柄上的左键被设置发送名为 **'turn_left'** 的事件。稍后，我们使用这个事件来旋转玩家控制的坦克。
![](/getting_started/img/tanks/2.jpg)

对所有的键位做同样的事 - 左，右，向前和向后。

![](/getting_started/img/tanks/3.jpg)

蓝色坦克充当玩家2。我们定义相同的控制，但是将键位映射到WSAD和第二个连接的游戏手柄。
In a **TankTree**, we listen to the events and perform actions to actually control the tank. The reason this node tree is separate is that we attach it to both tanks, preventing duplicated node trees.

**On Event** node is set to listen to the **'turn_left'** event. For player 1, this event is triggered when left key is pressed. For player 2, it happens on the A key press. **On Event** node is connected to the **Rotate Object** node, with **Vector Z** value set to a small positive value controlling the rotation speed. Playing the game now, pressing the left key rotates the tank! 

![](/getting_started/img/tanks/4.jpg)

We do the same for the **'turn_right'** event, however the **Vector Z** value is set to a negative value to rotate in the opposite direction.

On to the handling **'forward'** event. To figure out which direction should the tank move in, **Vector from Transform** node is used with type set to **Look**. This vector is then scaled down using **Vector Math** node to slow down tank speed moving forward. Resulting vector is passed into **Translate Object** node.

![](/getting_started/img/tanks/5.jpg)

As before, we do the same for **'backward'** event with translate vector reversed.

Now that the tanks are fully controllable, we make them shoot bullets. To keep scene clear, bullet object is placed in the second scene layer with **Render disabled**. This ensures object will be exported but not visible on its own.

![](/getting_started/img/tanks/6.jpg)

Selecting the red tank, an empty object is added as a child - the location of this object defines where to shoot bullets from. A new logic tree is added to this empty object. M key or gamepad cross/a key emits a **'fire'** event. We do the same for blue tank.

![](/getting_started/img/tanks/7.jpg)

We attach another logic tree - handling response to the **'fire'** event. We spawn a new object - our bullet model from layer 2, and set its location to the logic tree owner - in this case a bullet spawn point - defined as an empty object placed as a child of tank.

![](/getting_started/img/tanks/8.jpg)

Playing the scene now, we discover the bullets fall from the cannon down to the ground. We need some fire powder!

![](/getting_started/img/tanks/a.jpg)

**Apply Impulse** node fixes that. Similar to moving the tank forward, we acquire the forward vector and scale it up.

![](/getting_started/img/tanks/9.jpg)

Even though Armory culls out of screen objects, it is important to keep resources used down to a minimum. We remove each bullet after 2 seconds of lifetime. To do this, **Array(Object)** node is placed and all fired bullets are stored in this array using the **Array Add** node. We wait 2 seconds with **Sleep** node and call **Remove Object** node. **Array Shift** node feeds the first element from bullet array into the **Remove Object** node, and also removes this element from array itself.

![](/getting_started/img/tanks/10.jpg)

That's it - feel free to experiment further! Get the full blend for this tutorial:

- https://github.com/armory3d/armory_tutorials/tree/master/tanks
