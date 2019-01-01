# 物理

Armory是为任何物理引擎设计的。在内部，编写了一个胶水代码来绑定物理模拟。这让你选择最合适的物理引擎取决于项目的需要，并使得Armory不会过时。

如果现场没有发现刚体，Armory会跳过物理模块，以节省空间和性能。若要强制物理模块，请设置`Armory项目 - 物理`从`自动`改为`开启`。

默认情况下，Armory使用功能齐全的[Bullet物理](https://github.com/armory3d/haxebullet)。如果轻量引擎够用， 我们也提供[Oimo physics](https://github.com/armory3d/oimo_module)。在OIMO中，三角形网格形状是用近似凸壳的。

若要设置有效的物理引擎，请设置`Armory项目 - 物理引擎`属性。
