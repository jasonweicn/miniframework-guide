# 连接数据库

MiniFramework 目前只支持 MySQL 数据库，有手动和自动两种连接方式。

## 手动连接

```php
//如果未在页面顶部用 use 引入 Db，按照下面的写法，在 Db 前加上 \Mini\
$db = \Mini\Db::factory ('Mysql',
    array (
        'host'          => 'localhost', //主机地址
        'port'          => 3306,        //端口
        'dbname'        => 'mydbname',  //库名
        'username'      => 'myuser',    //用户名
        'passwd'        => '123456',    //密码
        'charset'       => 'utf8',      //字符编码
        'persistent'    => false        //是否启用持久连接 （ true | false ）
    )
);

//还可以通过 Config 中的 load() 方法先读取数据库配置，再创建对象
$dbConfig = \Mini\Config::getInstance()->load('database');
$db2 = Db::factory ('Mysql', $dbConfig['default']);
```

> 提示：`Config::getInstance()->load('database')` 这个方法还可以传入 `database:default` 来直接获取 `default` 中的数据（从 1.0.0 版开始支持）

## 自动连接方法

MiniFramework 自动连接数据库功能默认是关闭的，如需使用，请在你的应用入口文件 `Public/index.php` 中定义常量 `DB_AUTO_CONNECT` 的值为 `true`，来开启这个功能，例如：

```php
define('DB_AUTO_CONNECT', true);
```

同时，还需要在 `Config/database.php` 中对数据库连接进行配置，例如：

```php
$database['default'] = array (
    'host'          => 'localhost', //主机地址
    'port'          => 3306,        //端口
    'dbname'        => 'test',      //库名
    'username'      => 'root',      //用户名
    'passwd'        => '',          //密码
    'charset'       => 'utf8',      //字符编码
    'persistent'    => false        //是否启用持久连接 （ true | false ）
);
```

接下来，就可以在模型中通过 `$this->loadDb()` 方法直接加载数据库对象了，例如：

```php
namespace App\Model;

use Mini\Model;

class Info extends Model //自动连接数据库，必须继承核心类 Model
{
    public function getInfo()
    {
        //加载 key 为 default 的数据库
        $db = $this->loadDb('default');
        
        //do something...
    }
}
```

> 提示：MiniFramework 的数据库自动连接功能，采用的是惰性连接机制，只会在下达了执行 SQL 语句命令时，才会真正开始与数据库通讯建立连接，因此，你不必为开启自动连接功能而担心应用的性能问题。



