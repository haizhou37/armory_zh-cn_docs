# 特性

Armory用特性（组件）系统将逻辑附加到Blender物体然后让他们交互。特性可以附加到场景物体或场景本身。若要检查场景中的特性，请切换到`大纲编辑器 - 群组`查看。

![](/essentials/img/traits_groups.png)

这里有几种特性类型：
- `Haxe脚本` - 用Haxe从头写脚本。
- `绑定脚本` - 处理普通的东西，如字符控制器，和Armory绑定。
- `逻辑节点` - 可视化集合游戏逻辑。
- `画布` - 使用用户界面。

对于脚本，可以直接从Blender传递参数或设置脚本属性。

![](/essentials/img/traits_panel.png)

## 特性事件

特性暴露事件 - 这样就有可能得到关于其生命周期的通知。

- `Trait.notifyOnAdd()` - 特性被添加到物体。
- `Trait.notifyOnInit()` - 特性所属的物体被添加到场景。
- `Trait.notifyOnRemove()` - 特性所属的物体从场景被移除。
- `Trait.notifyOnUpdate()` - 在这里更新游戏逻辑。
- `Trait.notifyOnRender()` - 在这里更新渲染。

当场景被异步构建时，`onInit`事件可以在尚未出现所有场景物体的情况下调用。如果特性构造依赖于其他场景对象，请使用`Scene.active.notifyOnInit()`事件，该事件在场景完全构造后立即调用。
