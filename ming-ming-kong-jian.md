# 命名空间

---

从 1.0.0 版开始，MiniFramework 已全面启用命名空间，其中：

`Mini` 对应的框架核心

`App` 对应你的应用，可以通过在应用的入口文件中，定义常量 `APP_NAMESPACE` 的值来改变应用的命名空间，例如：

```php
define('APP_NAMESPACE', 'MyApp'); //建议与应用目录名保持一致
```

创建控制器时，请在页面顶部放置用于声明命名空间的代码，例如：

```php
namespace App\Controller; //声明当前页的命名空间

use Mini\Action; //引入Action，因为Action是框架核心文件，所以前面要加Mini\

class Index extends Action
{
    function indexAction()
    {
        //...
    }
}
```

创建模型时，同样要在页面顶部放置用于声明命名空间的代码，例如：

```php
namespace App\Model; //声明当前页的命名空间为 App\Model

use Mini\Model; //引入框架核心文件

class Info extends Model
{
    public function getInfo()
    {
        //...
    }
}
```



