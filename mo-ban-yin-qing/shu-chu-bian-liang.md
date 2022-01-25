# 输出变量

---

开发者可以在 View 和 Layout 中通过特定的标记符号对变量进行标记，模板引擎通过对开发者编写的标记符号，编译后，实现在 View 和 Layout 中按指定的位置输出变量的值，例如：

在 Controller 中向 View 传递变量

```php
// 向 View 传递一个名为 title 的变量
$this->view->assign('title', '这里是标题文本');

// 渲染并显示View
$this->view->display();
```

在 View 中标记变量

```php
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>{$title}</title>
<link rel="stylesheet" type="text/css" href="{$baseUrl}/css/default.css">
</head>
```

> 提示：上述代码中，{$baseUrl}是一个框架默认的变量，用于输出基础路径。



