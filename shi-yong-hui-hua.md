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





