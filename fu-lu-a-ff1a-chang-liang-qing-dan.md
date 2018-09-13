# 附录A：常量清单

---
aaa

| 常量 | 用途 | 类型 | 默认值 |
| :---: | :---: | :---: | :---: |
| APP\_NAMESPACE | 定义应用的命名空间名称 | string | "App" |
| APP\_PATH | 定义应用路径 | string |  |
| CACHE\_PATH | 定义缓存文件存储路径 | string |  |
| CONFIG\_PATH | 定义配置文件读取路径 | string |  |
| DB\_AUTO\_CONNECT | 数据库自动连接功能开关 | boolean | FALSE |
| DS | 定义系统目录分隔符 | string |  |
| HTTP\_CACHE\_CONTROL | 定义 HTTP 缓存指令 | string | "private" |
| LAYOUT\_ON | 布局功能开关 | boolean | FALSE |
| LAYOUT\_PATH | 定义布局文件读取路径 | string |  |
| LIB\_PATH | 定义框架核心类库读取路径 | string |  |

APP\_NAMESPACE

用途：定义应用的命名空间名称

类型：boolen

默认值：

MiniFramework 从 1.2.0 版本开始，新增了支持通过自带的 Upload 类实现文件的上传保存。

示例代码如下：

```php
// 实例化 Upload 类
$upload = new \Mini\Upload();

// 调用 save 方法，将要保存的文件作为参数传入
$res = $upload->save($_FILES['file']);

// 保存成功时 $res 中的返回值为保存路径和文件名，失败时值为 false
if (! $res) {
    $errmsg = $upload->getErrorMsg();
    echo $errmsg;
} else {
    dump($res);
}
```

> 提示：保存失败时，可以通过 `getErrorMsg()` 方法获取错误信息。

在实例化 Upload 类时，可传入一个数组类型的参数，对文件保存路径、大小和类型进行设定，例如：

```php
// 配置数组
$config = array(

    // 文件保存的根目录
    'rootPath'  => PUBLIC_PATH . DS . 'uploads',

    // 文件的大小限制（单位：Byte）
    'maxPath'   => 512000,

    // 允许的类型
    'allowType' => 'bmp,gif,jpg,jpeg,png'

);

// 实例化 Upload 类时，将配置数组作为参数传入
$upload = new \Mini\Upload($config);
```

> 提示：上面示例代码中，配置项可有选择的进行设定，没有设定的，框架会使用默认值处理。


