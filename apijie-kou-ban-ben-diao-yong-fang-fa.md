# API接口版本调用方法

---

MiniFramework 从 1.0.8 版本开始，新增了对于 REST 模式的 API 接口的版本调用方法。可以在发出请求时，向 HEADER 中添加一个名为 `Ver` 的参数，作用是声明调用的目标接口的版本，其值应为一个整数。MiniFramework 在接到这个请求时，会按 HEADER 中给出的版本号参数 `Ver` 调用对应的 API 接口文件。

当某个 API 接口需要增加新版本时，开发者需要将对应的接口文件和类名增加后缀 `_VX` （X代表版本号），例如：`Info_V2.php`

> 提示：最新的 MiniFramework 源代码包中，已经提供了关于 API 接口版本调用的 demo 文件，分别是 Info.php 和 Info\_V2.php



