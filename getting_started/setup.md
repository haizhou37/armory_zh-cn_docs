# 安装

Armory附带了你所需要的一切。

- [下载SDK](http://armory3d.org/download.html).
- 解压`Armory_version.zip`到你喜欢的地方。*（在Windows环境下，倾向选择一条较短的路径，如`C:\Dev`或者解压[7-zip](http://www.7-zip.org)防止长路径错误并加快提取速度。）*
- 运行位于解压SDK中的Blender。*（在Windows上，您可能需要在第一次运行时单击**更多信息** - **始终运行**。在Linux上，解压文件夹并打开终端并输入 `./blender`。在macOS上，查看`instructions.txt`文件。）*

<div style="width:50%">![](/getting_started/img/winrun.png)</div>

- 若要验证所有操作是否正常，请保存`.blend`文件，切换到`Cycles`或者`Eevee`渲染引擎（使用位于标题栏中的下拉列表），然后点击位于`属性 - 渲染 - Armory播放器`面板下的`播放`（F5）按钮。 

- 继续前往[场景教程](/getting_started/playground.md)了解更多。

<iframe width="560" height="315" src="https://www.youtube.com/embed/4FPKCUYjpP0?rel=0" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## 问题排查

- 对于旧显卡，请在`Blender - 属性 - 渲染 - Armory渲染路径`中选择`低`预设。
- 在命名事物时，倾向不重音的字母`A-Z。
- 如果您希望隔离绑定的Blender的配置，请在`Armory/2.80`创建空的`config`文件夹。
- 如果你有什么困难，[让我们知道](http://armory3d.org/community.html)！

### Windows

- 若要查看错误消息，请从控制台启动Blender或按`Blender - 窗口 - 切换系统控制台`。
- `类型未找到：Main`错误 - 在一条安全路径保存你的`.blend`文件，像是`C:\Users\user_name\Documents\test`，否则，Windows可能会阻止写入文件。
- 如果你得到了丢失`.dll`的错误，请尝试安装[Visual C++ Redistributable for Visual Studio 2017](https://go.microsoft.com/fwlink/?LinkId=746572)。

### Linux

- 若要查看错误消息，请在终端使用`./blender`启动Blender。

### macOS

- 若要查看错误消息，请使用`/path/to/Armory/blender.app/Contents/MacOS/blender`。
- 由于macOS的安全因素，您可能会得到`文件损坏`的错误。尝试从终端启动Blender，如上文所述。


## 使用Armory作为插件

如果您不需要内置播放器，Armory只能在标准Blender安装中作为插件使用。然后播放器将在一个单独的窗口启动。
- [下载](http://armory3d.org/download.html)然后解压适合您平台的SDK。
- 在Blender中选择**文件** - **用户设置...** ，然后导航到**插件**选项卡。
- 点击**从文件安装...**
- 选择位于`my_unpacked_sdk/Armory/armsdk/armory/blender/addon`的`armory.py`（在macOS中它的位置在`my_unpacked_sdk/Armory/Blender.app/armsdk/armory/blender/addon`）。
- **开启** Armory插件。
- 设置**SDK路径**属性为`my_unpacked_sdk/Armory/armsdk`。
- 点击在底部的**保存用户设置**然后重启Blender。就这样！
