# 日志

---

MiniFramework 从 1.4.0 版本开始，新增了日志功能，开发者可通过在应用的入口文件中定义 `LOG_ON` 为 `true` 来开启日志功能。

示例代码如下：

```php
// 开启日志（生产环境建议关闭）
const LOG_ON = true;
```

> 提示：如果在入口文件中未对常量 LOG\_ON 进行声明，则其默认值为 false。

目前，MiniFramework 日志的存储，支持文件和数据库两种存储模式，具体实现方式可参见如下章节：

链接1：[日志存入文件](/ri-zhi/ri-zhi-cun-ru-wen-jian.md)

链接2：[日志存入数据库](/ri-zhi/ri-zhi-cun-ru-shu-ju-ku.md)
