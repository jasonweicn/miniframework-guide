# 日志存入数据库

---

开发者可通过定义 `LOG_MODE`、 `LOG_DB_CONFIG` 和 `LOG_TABLE_NAME` 三个常量来实现将日志存入文件，例如：

```php
// 首先要激活日志功能（默认值为：false）
const LOG_ON = true;

// 定义日志的存储模式（默认值为：1，1为文件，2为数据库）
const LOG_MODE = 2;

// 定义日志存储所使用的数据库配置
const LOG_DB_CONFIG = 'database:default';

// 定义日志存储的数据表名
const LOG_TABLE_NAME = 'myapp_log';
```
