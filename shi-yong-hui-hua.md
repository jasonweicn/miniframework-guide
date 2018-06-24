# 使用会话

---

MiniFramework 从 1.0.12 版本开始，新增了 Session 会话类。

示例代码如下：

```php
namespace App\Controller;

use Mini\Session;

class Example extends Action
{
    function sessionAction()
    {
        // 开启会话
        Session::start();

        // 写入一个名为 test 的会话，对应的值为 abc
        Session::set('test', 'abc');

        // 读取名为 test 的会话
        $test = Session::get('test');

        dump($test);
        die();
    }
}
```

Session 会话类还支持在开启时传入针对 SESSION 的设定参数，例如：

```php
// 开启会话
\Mini\Session::start(array(
    
    // 设定 SESSION 存储于 Memcached
    'save_handler'  => 'memcache',
    
    // Memcached 主机地址和端口
    'save_path'     => '127.0.0.1:11211'
    
));
```



