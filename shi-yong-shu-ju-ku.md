# 连接数据库

---

MiniFramework 目前只支持 MySQL 数据库，有手动和自动两种连接方式。

## 手动连接（工厂模式）

```php
// 如果未在页面顶部用 use 引入 Db，按照下面的写法，在 Db 前加上 \Mini\Db\
$db = \Mini\Db\Db::factory ('Mysql',
    array (
        'host'          => 'localhost', // 主机地址
        'port'          => 3306,        // 端口
        'dbname'        => 'mydbname',  // 库名
        'username'      => 'myuser',    // 用户名
        'passwd'        => '123456',    // 密码
        'charset'       => 'utf8',      // 字符编码
        'persistent'    => false        // 是否启用持久连接 （ true | false ）
    )
);

// 还可以通过 Config 中的 load() 方法先读取数据库配置，再创建对象
$dbConfig = \Mini\Base\Config::getInstance()->load('database');
$db2 = Db::factory ('Mysql', $dbConfig['default']);
```

> 提示：`Config::getInstance()->load('database')` 这个方法还可以传入 `database:default` 来直接获取 `default` 中的数据（从 1.0.0 版开始支持）

## 直接调用 MySQL 类

MiniFramework 从 2.0 开始支持直接调用 MySQL 类，这样做的好处是便于让 IDE 对类的方法进行提示，为开发者编码提供便利。

```php
use Mini\Base\Config;
use Mini\Db\Mysql; // 引入 MySQL 类

$dbParams = Config::getInstance()->load('database:default');
$db = new Mysql($dbParams);
```

## 自动连接方法

MiniFramework 自动连接数据库功能默认是关闭的，如需使用，请在你的应用入口文件 `Public/index.php` 中定义常量 `DB_AUTO_CONNECT` 的值为 `true`，来开启这个功能，例如：

```php
define('DB_AUTO_CONNECT', true);
```

同时，还需要在 `Config/database.php` 中对数据库连接进行配置，例如：

```php
$database['default'] = array (
    'host'          => 'localhost', // 主机地址
    'port'          => 3306,        // 端口
    'dbname'        => 'test',      // 库名
    'username'      => 'root',      // 用户名
    'passwd'        => '',          // 密码
    'charset'       => 'utf8',      // 字符编码
    'persistent'    => false        // 是否启用持久连接 （ true | false ）
);
```

接下来，就可以在模型中通过 `$this->loadDb()` 方法直接加载数据库对象了，例如：

```php
namespace App\Model;

use Mini\Base\Model;

class Info extends Model // 自动连接数据库，必须继承核心类 Model
{
    public function getInfo()
    {
        // 加载 key 为 default 的数据库
        $db = $this->loadDb('default');

        // do something...
    }
}
```

> 提示：MiniFramework 的数据库自动连接功能，采用的是惰性连接机制，只会在下达了执行 SQL 语句命令时，才真正开始与数据库通讯建立连接，因此，你不必为开启自动连接功能而担心应用的性能问题。

## 连贯操作查询数据

MiniFramwork 从 1.2.0 版本开始，支持在 Model 模型类中，通过“连贯操作”方式查询数据，例如：

```php
namespace App\Model;

use Mini\Base\Model;

class User extends Model // 继承 Model 模型类
{
    public function getUser()
    {
        // 设置当前使用的数据库（这里的 default 是数据库连接对象的名称）
        $this->useDb('default');

        // 示例1：连贯操作方式向名为 user 的表中插入一条数据纪录
        $data1 = array('id' => 1, 'name' => '张三');
        $this->table('user')->data($data1)->add();

        // 示例2：向 user 表中一次插入多条纪录
        $data2 = array(
            array('id' => 2, 'name' => '李四'),
            array('id' => 3, 'name' => '王五')
        );
        $this->table('user')->data($data2)->add();

        // 示例3：修改 user 表中 id 为 3 的记录
        $this->table('user')->data(array('name' => '赵六'))->where('id=3')->save();

        // 示例4：查询 user 表中 id 为 1 的记录
        $res = $this->table('user')->where('id=1')->select();

        // 输出查询结果
        dump($res);
    }
}
```



