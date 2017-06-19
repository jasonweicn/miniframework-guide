# 全局函数

---

MiniFramework 在初始化时，会自动加载一个全局函数库，你可以随时调用里面的全局函数，例如：

```php
$test = array('a', 'b', 'c');

//调用全局函数 pushJson() 输出一个 JSON 串并终止程序运行
pushJson($test);
```

> 提示：全局函数库位于 `Mini/Functions/Global.func.php`



