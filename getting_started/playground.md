# 场景教程

<iframe width="560" height="315" src="https://www.youtube.com/embed/H5ylSfTfNg8?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

本教程向您介绍Armory基础知识。我们将创建一个像游乐场一样的场景，逐步展示基本的功能。我们走吧。

- 获取本教程的[.blend文件](https://github.com/armory3d/armory_tutorials/releases)。

### 你好，世界

紧接着我们在 [安装教程](/getting_started/setup.md)中剩下的部分。打开Blender，保存项目并在 `属性 - 渲染`面板中选择`Cycles`或`Eevee`渲染引擎。按下`Armory播放器 - 运行（F5）`预览项目。

你能`Armory播放器`面板选择运行环境：
- 选择`Krom`快速运行场景。
- 选择`浏览器`部署HTML5网页。
- 选择`C++`部署原生项目(要求C++编译器)。

你也能在`Armory播放器`面板选择相机模式：
- 选择`场景`从活动场景摄像机的角度开始游戏。
- 选择`视口`从视口视图开始游戏。这是有用的快速场景预览，因为它也可以让你控制相机。试试看！
- 按下`Shift + F`在3D视图中浏览场景。

此外，您还可以在`尺寸 - 分辨率`调整窗口大小。若要在全屏运行，请选择`Armory项目 - 窗口模式 - 全屏`。

<a href="./getting_started/img/playground/1.jpg">![](/getting_started/img/playground/1.jpg)</a>

### 物体

我们将从一些关于如何操作场景对象的Blender基础知识开始（部分操作在Blender2.8版本之前默认有效）：

- 在3D视图中，按下`空格`并搜索`添加平面`创建平面对象(或者在3D视图标题栏点击`添加 - 网格 - 平面`)。
- 按`S`缩放平面，`R`旋转，或者`G`移动和变换。
- `右键点击`选择物体。
- 删除物体按`X`。

### 修改器

Blender搅拌器有多种修改器，它们对活动物体应用程序效果。选择立方体，导航到`修改器`选项卡并 `倒角`修改器，使立方体边缘看起来更光滑。

<a href="./getting_started/img/playground/1b.jpg">![](/getting_started/img/playground/1b.jpg)</a>

### 材质

选择立方体并切换到`节点编辑器`。转到`着色器节点`并启用`使用节点`。 现在，您可以使用默认的`Diffuse BSDF`节点来调整材质的颜色和粗糙度。

<a href="./getting_started/img/playground/2.jpg">![](/getting_started/img/playground/2.jpg)</a>

接下来，切换回`3D视图`然后选择平面。我们想在上面加个纹理。按下`Tab`进入编辑模式，按`空格`并搜索`展开`给平面创建UV坐标图。

在`材质`选项卡中，创建一个新材质。切换到节点编辑器，就像我们以前做的那样。选择`Diffuse BSDF`节点并按`X`删除它。在标题中，按`添加 - 群组 - Armory PBR` 放在画布上。连接`面`端口到`材质输出`节点。若要获得最佳结果，在Armory中使用材质时请使用`Armory PBR`节点。

![](/getting_started/img/playground/grid_base.png)
![](/getting_started/img/playground/grid_rough.png)

保存上面的图像，只需将文件拖放到Blender中的节点画布上。将`图像纹理`节点连接到`基础颜色`和`粗糙度`端口。

<a href="./getting_started/img/playground/3.jpg">![](/getting_started/img/playground/3.jpg)</a>

按照这些步骤，一个基本的场景已经形成。按下`F5`在Armory中播放场景！

<a href="./getting_started/img/playground/5.jpg">![](/getting_started/img/playground/5.jpg)</a>

### 动画

让我们创建一个旋转立方体的动画。找到`时间线`并进入第1帧。选择立方体并按下`I - 旋转`插入旋转的关键帧。接下来，进入时间线中的第60帧。选择立方体后，按下 `R`旋转它所需的数值并再一次按`I - 旋转`。

<a href="./getting_started/img/playground/6.jpg">![](/getting_started/img/playground/6.jpg)</a>

### 光照

从大纲视图中选择灯光物体并切换到`物体数据`选项卡。您可以设置灯光类型和调整灯的颜色和强度。

<a href="./getting_started/img/playground/9.jpg">![](/getting_started/img/playground/9.jpg)</a>

### 环境

世界节点用于设置环境。切换到`节点编辑器 - 世界节点`去获取节点。在本教程中，我们使用`天空纹理`节点来渲染程序化天空。如果我们要添加一个环境映射，我们将使用带有`.hdr`文件的`环境纹理`节点.

<a href="./getting_started/img/playground/10.jpg">![](/getting_started/img/playground/10.jpg)</a>

### 物理

选择对象后，导航到`物理`选项卡并按下`刚体`按钮。 在`刚体碰撞`面板设置表示对象的所需形状。

在`刚体`面板中设置质量和类型：
- 选择`活动项`用于被物理影响的物体。
- 选择`被动`用于在时间线上动画的对象。

<a href="./getting_started/img/playground/11.jpg">![](/getting_started/img/playground/11.jpg)</a>

### 导入资源

使用Blender，我们可以很容易地导入常见的资源格式。
- 选择`文件 - 导入`导入文件格式。
- 选择`文件 - 附加` 从其它的`.blend`文件中导入物体。
- 选择`文件 - 链接` 从其它的`.blend`文件中链接物体。

在本教程中，我们使用了一个来自 [mixamo](http://mixamo.com)的`.fbx` 动画模型， 用`文件 - 导入`选项导入它。

<a href="./getting_started/img/playground/8.jpg">![](/getting_started/img/playground/8.jpg)</a>

### 逻辑节点

逻辑节点提供了一种创建交互式场景的可视化方法。生成项目时，创建的节点树将自动编译为脚本。

该系统由五个基本类别组成：
- `事件` - 执行开始的节点，由所需事件触发。
- `动作` - 一旦事件被触发，这些节点就会采取行动。
- `逻辑` - 用于控制执行流的节点，使用分支、循环、门等等。
- `变量` - 用于在逻辑树中存储数据的节点。
- `值` - 用于从其他对象检索数据的节点。

我们将使用逻辑节点对圆柱体添加动画。切换到`节点编辑器` 区域并选择`逻辑`节点。按下`新建`创建一个新的节点树。

您可以通过`添加`菜单项浏览所有可用的节点或者简单地按下`Shift + A`进行搜索。

- 搜索`每帧更新`节点并放置它。这是一个事件节点，每帧都会被调用。
- 连接到`设置位置`节点。
- 添加`向量`节点并连接到`设置位置`节点。每一帧，圆柱体位置会被设置成这个向量。
- 对于`X`位置，添加`数学`节点并设置成`正弦`。
- 添加`时间`节点来控制`正弦`节点。
- 添加`数学`节点来缩放正弦输出。
- 我们会保持`Y`和`Z`的位置不变。

每个节点树都必须附加到一个对象上。选择圆柱体并在`属性 - 物体 - Armory特性`中新建特性。将类型设置为`节点`并将新创建的节点树选择至`树`属性。

<a href="./getting_started/img/playground/12.jpg">![](/getting_started/img/playground/12.jpg)</a>

注意：要查看`打印`节点的输出,要开启`Armory项目 - 调试控制台`。

### Haxe脚本

我们可以使用`Haxe`脚本语言直接编程物体特性。让我们创建一个特性，在按下键后产生一个盒子。

在场景中创建一个空对象（`空格 - 添加空物体`）。这个物体的位置将作为生成点。在`属性 - 物体 - Armory特性`中创建一个新的特性.将类型设置为 `Haxe`并按下`新建脚本`按钮。

按下`编辑脚本`在Kode Studio中打开脚本文件。Kode Studio是一个包含代码完成和调试支持的专用代码编辑器。

```haxe
package arm;

import iron.object.Object;
import iron.system.Input;
import iron.Scene;
import armory.trait.physics.RigidBody;

class SpawnBox extends iron.Trait {
	public function new() {
		super();
		// We want to get notified every frame
		notifyOnUpdate(update);
	}

	function update() {
		// f key was pressed
		if (Input.getKeyboard().started("f")) {
			// Spawn Box object
			Scene.active.spawnObject("Box", null, boxSpawned);
		}
	}

	// Box just got spawned
	function boxSpawned(o:Object) {
		// Translate cube to the location of empty object
		var traitOwner = object;
		o.transform.loc.setFrom(traitOwner.transform.loc);
		// Box object has a rigid body trait
		// Notify physics system to take new location into effect!
		o.getTrait(RigidBody).syncTransform();
	}
}
```

<a href="./getting_started/img/playground/13.jpg">![](/getting_started/img/playground/13.jpg)</a>

### 绑定脚本

Armory附带了一组预先创建的绑定脚本。与常规脚本类似，绑定脚本可以作为特性附加到物体上。在本教程中，我们将使用`物理拖拽`特性。当这个特性附加到启用物理功能的物体上时，它允许我们使用鼠标拖动这个物体。

<a href="./getting_started/img/playground/14.jpg">![](/getting_started/img/playground/14.jpg)</a>

### UI画布
为了构建游戏界面，使用了专用的ArmorUI工具。

除了物体，场景本身也可以包含特征。这是一个很好的UI特性。切换到`场景`选项卡并在`Armory特性`面板中添加一个新特性。将特性类型设置为`UI`然后按下`新画布`按钮。之后，按下`编辑画布`按钮会启动ArmorUI。

在`ArmorUI`中按下`Text`按钮生成文本对象。在`属性`面板调整文本然后点击`保存`。如果你现在启动游戏，画布就会显示出来。

<a href="./getting_started/img/playground/15.jpg">![](/getting_started/img/playground/15.jpg)</a>

### 渲染路径

Armory由可编程渲染路径系统驱动。导航到`渲染 - Armory渲染路径`面板来获取设置。有几个可用于简单配置的预置。

可以创建多个渲染路径。导出项目时，可以使用最适合目标硬件的渲染路径。

如果你在现代GPU上运行（OpenGL 4.5+），选择`最大（游戏）`预设启用更先进的效果，如基于体素的环境遮挡。请注意，VoxelAO需要在独立窗口中运行-只需按`F5` 即可启动。

<a href="">![](/getting_started/img/playground/16.png)</a>

### 导出器

当我们准备发布我们的项目时，`属性 - 渲染 - Armory导出器`做这份工作。

您可以创建多个导出预置，每个都指定一个目标平台、图形API、渲染路径和启动场景。选择所需的平台并点击`发布`按钮。一旦完成，点击`三角形 - 打开文件夹`查看导出的文件。

<a href="">![](/getting_started/img/playground/17.png)</a>

- 继续前往[坦克教程](/getting_started/tanks.md)
- 继续前往[车辆教程](/getting_started/vehicle.md)
