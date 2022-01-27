# 模板缓存

---

在开启模板引擎的状态下，MiniFramework 会将 View 和 Layout 的文件进行解析编译，并将编译后的代码以缓存文件的形式，保存在常量 `CACHE_PATH`_ _定义的缓存目录中。

开发者修改 View 和 Layout 文件后，模板引擎会比对文件最后修改时间，并对缓存文件进行更新。
