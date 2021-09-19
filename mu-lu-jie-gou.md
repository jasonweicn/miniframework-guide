# 目录结构

---

```
|--- App/                        应用案例
|    |--- Api/                   REST模式的API
|    |--- Cache/                 缓存
|    |--- Config/                配置
|    |    |--- database.php      数据库配置文件（生产环境）
|    |    |--- database-dev.php  数据库配置文件（开发环境）
|    |    |--- database-test.php 数据库配置文件（测试环境）
|    |
|    |--- Controller/            控制器
|    |--- Layout/                布局
|    |--- Model/                 模型
|    |--- Public/                站点根目录
|    |    |--- css/              css
|    |    |--- img/              图片
|    |    |--- js/               js
|    |    |--- uploads/          上传文件存储目录
|    |    |--- index.php         应用入口文件（生产环境）
|    |    |--- index-dev.php     应用入口文件（开发环境）
|    |    |--- index-test.php    应用入口文件（测试环境）
|    |
|    |--- View/                  视图
|
|--- MiniFramework/              框架核心目录
     |---Base/                   基础类库
     |---Bootstrap.php           引导程序
```

> 提示：MiniFramework 从 2.0 版开始，对框架核心进行了重构，大部分基础类库已移入 `Base` 目录下。
