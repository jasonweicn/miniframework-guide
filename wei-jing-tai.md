# 伪静态

---

MiniFramework 在设置了 Rewrite 规则后，可实现类似下面这种伪静态访问方式：

`http://localhost/Controller/Action/param1/value1/param2/value2`

## 运行于 Apache 的设置方法

向 Public 目录中添加一个 .htaccess 文件（附带的应用案例中已提供），内容如下：

```
RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^ index.php [L]
```

## 运行于 Nginx 的设置方法

在 nginx.conf 中，找到对应的站点，向 server{} 中添加如下设置：

```
location / {
    index  index.html index.php;
    if (!-e $request_filename) {
        rewrite ^/(.*)$ /index.php last;
    }
}
```

> 提示：MiniFramework 从 1.0.10 版本开始，支持使用下划线作为 URL 分隔符，和支持以 .html 结尾的伪静态 URL ，例如：  
> `http://localhost/Controller/Action/param1_value1_param2_value2.html`



