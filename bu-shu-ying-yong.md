# 部署应用

MiniFramework 支持主程序和WEB站点根目录分离部署的特性。你下载的 MiniFramework 源代码包中，已经附带包含了一个用于演示的应用demo，目录名为 `App`（查阅：[目录结构](/chapter1.md)），请将 Apache 或 Nginx 的站点根目录指向 `App` 中的 `Public` 目录。

`http://你的域名/index.php?c=index&a=index`

如果，你可以通过浏览器访问类似上面这样的URL地址，并获得一个显示有“Hello World!”的页面，这说明你已经部署成功了。

