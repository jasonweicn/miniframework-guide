# 应用入口

---

使用 MVC 开发模式时，通常需要为应用准备一个入口文件，所有对应用的访问请求都应指向这个入口文件，MiniFramework 也不例外。

在附带的应用案例中，找到 App/Public/index.php，这就是一个入口文件，其代码如下：

```php
// 应用命名空间（请与应用所在目录名保持一致）
const APP_NAMESPACE = 'App';

// 是否显示错误信息（默认值：false）
const SHOW_ERROR = true;

// 是否开启日志（生产环境建议关闭，默认值：false）
const LOG_ON = false;

// 是否启用布局功能（默认值：false）
const LAYOUT_ON = true;

// 是否开启REST模式的API接口功能（默认值：false）
const REST_ON = true;

// 引入 MiniFramework 就是这么简单
require dirname(dirname(__DIR__)) . DIRECTORY_SEPARATOR . 'miniframework/Bootstrap.php';
```

在上边的代码中，最为关键的是最后一行，通过 `require` 命令引入 MiniFramework 的引导程序 `Bootstrap.php` 。

在引入引导程序前，你还可以像案例中一样，通过 `const` 命令定义一些 MiniFramework 的关键常量，例如用于显示报错信息的常量 `SHOW_ERROR` 。

> 提示：MiniFramework 运行所需的全部常量可以在引导程序 `Bootstrap.php` 中找到（1.0.0 版之前引导程序名为 Mini.php）。



