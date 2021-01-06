# 日志存入文件

---

开发者可通过定义 `LOG_MODE` 和 `LOG_PATH` 两个常量来实现将日志存入文件，例如：

```php
// 首先要激活日志功能（默认值为：false）
const LOG_ON = true;

// 定义日志的存储模式（默认值为：1，1为文件，2为数据库）
const LOG_MODE = 1;

// 定义日志的存储路径
const LOG_PATH = '/data/htdocs/myapp/logs';
```

通过上边的代码，便实现了将日志以文件的形式存储到指定的路径下。当开发者编写的代码运行遇到错误时，MiniFramework 会将捕获到的错误信息按 `yyyy-mm-dd.log` 的文件命名方式进行存储，例如：

> /data/htdocs/**myapp/logs/2021-01-06.log**
