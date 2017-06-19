# 开启 REST 模式的 API 接口功能

---

MiniFramework 从 1.0.0 版开始，增加了对 RESTful 的支持，可以在入口文件 `Public/index.php` 中，定义常量 `REST_ON` 的值为 `true` 开启 REST 模式的 API 接口功能，例如：

```php
define('REST_ON', true);
```

开启 REST 后，可以访问应用案例中附带的一个名为 Version 的 Api 接口 demo 进行测试。

文件位于 `App/Api/Version.php`，访问方式为：`http://你的域名/api/version` 访问后，正常情况下会得到如下输出结果：

`{"code":200,"msg":"success","data":"1.0.0"}`

需要特别注意的是：如果你的项目中有使用 `Api` 命名的 Controller，将会因 REST 开启而失效，所有向 `Api` 的请求均会被指向 `App/Api` 目录。

> 提示：MiniFramework 的 REST 接口支持输出 JSON 和 XML 两种数据格式，附带的 demo 中已经进行了演示。



