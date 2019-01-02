# 参考

## 逻辑

### Alternate

当它被重新激活时，在其激活的输出之间交替通过它的输入.

![](/assets/Alternate.JPG)


### Array loop

它循环遍历数组中分配的每个项。`Value`给出由索引值指定的项。`Done`在遍历数组时调用连接器。

![](/assets/array-loop.JPG)


### Branch

激活时，根据插入布尔值的状态，激活其`Ture`或`False`输出。

![](/assets/Branch.JPG)


### Gate

逻辑节点执行`if`语句的方法。激活时，它将比较它的两个输入是相等的、大的相等的、小于等于的还是不相等的，而不管变量类型如何，如果SET状态是这样的话，则通过红色输入。

`And`或`Or`仅用于布尔，当两个布尔为true（and）或至少一个（or）时，通过输入。

![](/assets/Gate.JPG)


### Inverse

布尔会变成对立面，真会变假，假会变成真。

![](/assets/Inverse.JPG)


### Is True/False

根据节点的说法，只有当插入的布尔值为`True`或`False`时，才能通过它的激活。

![](/assets/Is-true_false.JPG)


### Is None

给出NULL的布尔值，也就是说，如果它是NULL，那么它的输出为`True`(没有值)，如果它不是NULL，那么它输出`False`(有值)。

![](/assets/is-none.JPG)


### Is Not None

给出相反的NULL值，即如果它不是NULL，那么它的输出为`True`(有值)，如果它是NULL，那么它输出`False`(没有值)。

![](/assets/is-not-none.JPG)


### Loop

它是基本的(i in from...to)循环。`Index`给出由索引值指定的值。`Done`在循环完成时被调用。

![](/assets/Loop.JPG)


### Loop Break

Loop Break终止包含它的循环。 

![](/assets/loop-break.JPG)


### Merge

“New”按钮创建新输入，“X”按钮删除最底层的输入。如果它从任何一个输入接收激活，它将激活它的输出。

![](/assets/Merge.JPG)


### Not

反转插入的布尔值，因此如果输入为`True`，则输出`False`。

![](/assets/Not.JPG)


### Sequence

其调用输出按顺序排列。

![](/assets/Sequence.JPG)


### Switch

检查输入`in`上的值，当输入值与`case 1、case 2`或`case 3`值匹配时，它将触发相应的`case 1、case 2`或`case 3`。单击`New`以添加更多的`Case`。

![](/assets/Switch.JPG)


### To Bool

在输入中没有事件时为`False`，当输入上有事件时为`True`。

![](/assets/to-bool.JPG)


### While

它的循环只要在`Condition`中指定的bool是相同的(i.e., like  while(jumping == true){do domething})。

![](/assets/While.JPG)


### Sleep

在它被激活后的秒内激活节点与其输出连接后的浮点值。

![](/assets/sleep.JPG)


## 事件

### On Event

激活连接到其他节点树中指定的`Sent Event`或`Sent Global Event`的节点。

![](/assets/on-event.JPG)


### On Init

激活在游戏的第一帧上连接到它的节点。

![](/assets/On-Init.JPG)


### On Timer

从游戏开始时，在计时器倒计时之后，激活连接到的节点，当方框打勾时重复。

![](/assets/On-Timer.JPG)


### On Update

激活每个帧连接到它的节点。

![](/assets/On-Update.JPG)


### On Volume Trigger

下面的对象输入至Volume，上面的对象输入作为和它进入/离开/重叠的物体。 

进入模式：激活对象进入体积的帧上的连接节点，而在所有其他帧上，它不会激活。

离开模式：激活对象离开体积的帧上的连接节点，而在所有其他帧上，它不会这样做。

重叠模式：激活对象与体积重叠的帧上的连接节点，在所有其他帧上不激活。

![](/assets/on-volume-trigger.JPG)


## 触发器


### On Mouse

根据设置的不同，启动、按住或释放设置鼠标按钮时，激活连接到它的节点。

![](/assets/On-Mouse.JPG)


### On Keyboard

启动、按住或释放设置键盘按钮时，激活连接到它的节点，具体取决于设置。

![](/assets/On-Keyboard.JPG)



## States

### Mouse

Outputs a bool if the set button is being currently started, hold down, released, moved \(true\) or not \(false\).

![](/assets/Mouse.JPG)


### Mouse Cords

Outputs the X, Y location of the mouse of screen and its movement as Vector, and an integer if the scroll wheel es been moved up \(1\) or moved down \(-1\) this frame.

![](/assets/Mouse-Cords.JPG)


### Keyboard

Outputs a bool if the set button is being currently started, hold down, released, \(true\) or not \(false\).

![](/assets/Keyboard.JPG)


### Get Transform

Outputs the current transform of the set object. An objects Transform consists out of Vectors for its global location, rotation, and scale.

![](/assets/get-transform.JPG)


### Get Location

Outputs the current global location of the set object as vector.

![](/assets/get-location.JPG)


### Get Rotation

Outputs the current rotation of the set Object as a Vector.

![](/assets/get-rotation.JPG)


### Get Scale

Outputs the current scale of the set object as vector.

![](/assets/get-scale.JPG)


### Get Object

Searches for an object with the set name in the scene and outputs it.

![](/assets/get-object.JPG)


### Get Visible

Outputs a Boolean Value according to the objects current visibility setting in the Outliner. False if invisible, True if visible, even if the Object is not on camera right now.

![](/assets/get-visible.JPG)


### Get Child

Searches for object with the set name that is currently a child of the set object and outputs it.

![](/assets/get-child.JPG)


### Get Children

Outputs all current children of the set object as array of objects.

![](/assets/get-children.JPG)


### Get Parent

Outputs the current closest parent of the set object.

![](/assets/get-parent.JPG)


### Get Group

Searches for a group of objects with the set name and outputs it as an array of objects.

![](/assets/get-group.JPG)


### Group

Outputs all objects in the set group as array.

![](/assets/group.JPG) 


### Get Distance

Outputs the current distance between the two set objects as float.

![](/assets/get-distance.JPG)


### Get Trait

Searches for a Trait with the set name which is applied on the set object and outputs it.

![](/assets/get-trait.JPG)


### Active Camera

Outputs the current active Camera in your game as object.

![](/assets/active-camera.JPG)


### Active Scene

Outputs the currently active scene in your game.

![](/assets/active-scene.JPG)


### Volume Trigger

The lower object-input is used as Volume, the upper one as object-input for the object that enters/leaves/overlaps with it.

Enter-mode: Outputs true on the frame the object enters the volume, on all other frames it outputs false.

Leave-mode: Outputs true on the frame the object leaves the volume, on all other frames it outputs false.

Overlap-mode: Outputs true on the frames the object overlaps with the volume, on all other frames it outputs false.

![](/assets/Volume-trigger.JPG)


## Values

### Get Property

Can be used to receive Properties of other objects, which were set with the "[Set Property](/logic-nodes/set-property.md)" node. The properties name and object have to match the inputs of this node.

![](/assets/Get-property.JPG)


## Variables

### Action

TBD

![](/assets/Action.JPG)


### Boolean

Stores a Boolean value. A Boolean value has just two states: True and False.

![](/assets/boolean.JPG)


### Colour

Store colour value in RGB/HSV/HEX format.
 
![](/assets/Colour.JPG)

 
### Dynamic

TBD
 
![](/assets/Dynamic.JPG)  


### Float

Stores a Float value. A Float variable is a number with a limited number of decimals. If your number has more than 3 decimals, the value displayed will be rounded, but when you click on it you can still see the whole number, which will also be used in the game.

![](/assets/float.JPG)


### Global Object

Gives access to an global Object, which can be used to share information between different Traits.

![](/assets/global-object.JPG)


### Group

Get value stored in a group (Under Object tab) in Array form.

![](/assets/Group.JPG)


### Integer

Stores an integer value. These are whole numbers.

![](/assets/Integer.JPG)


### Material

Get material of any object specified.

![](/assets/Material.JPG)


### Mesh

Get reference of mesh specified.

![](/assets/Mesh.JPG)


### Object

Get reference any object specified.

![](/assets/Object.JPG)


### Quaternion

Store quaternion value.

![](/assets/Quaternion.JPG)


### Scene

Get reference of scene specified.

![](/assets/Scene.JPG)


### Scene Root

TBD

![](/assets/scene-root.JPG)


### String

Store string value.

![](/assets/String.JPG)


### Trait

Get reference of trait specified.

![](/assets/Trait.JPG)


### Transform

Store Location, Rotation, Scale value in vector form.

![](/assets/Transform.JPG)


### Vector

Store X, Y, Z value in vector.

![](/assets/Vector.JPG)


## Actions

### Set Variable

When activated, updates the first plugged in Variable to the Value of the second. Automatically converts some variable types.

![](/assets/set-variable.JPG)


### Translate Object

Moves the set object every frame it is activated by the given Vector.

![](/assets/translate-object.JPG)

### Set Property

When activated, sets or updates a Property of the given object named after its string input to the Value of its general Variable input \(the green one\). You do not have to worry about the variable type, you can plug everything it apart from activations. 

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
