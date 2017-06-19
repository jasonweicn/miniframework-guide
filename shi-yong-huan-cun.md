# 使用缓存

---

MiniFramework 支持三种缓存方式，分别是：Memcached、Redis 和 File（磁盘文件存储）。

## Memcached缓存

```php
$cache = \Mini\Cache::factory ('Memcache',
    array (
        'host'      => 'localhost', //主机
        'port'      => 11211        //端口
    )
);

//写入一个名为 test 的缓存，值为 abc，有效时间为 3600 秒
$cache->set('test', 'abc', 3600);

//读取名为 test 的缓存
$test = $cache->get('test');
```

> 提示：可以通过 `getMemcacheObj()` 来获得 Memcache 对象，以调用未在框架中封装的 Memcache 更多的方法。

## Redis缓存

```php
$cache = \Mini\Cache::factory ('Redis',
    array (
        'host'      => 'localhost', //主机
        'port'      => 11211,       //端口
        'passwd'    => ''           //密码
    )
);

//写入一个名为 test 的缓存，值为 abc，有效时间为 3600 秒
$cache->set('test', 'abc', 3600);

//读取名为 test 的缓存
$test = $cache->get('test');
```

> 提示：可以通过 `getRedisObj()` 来获得 Redis 对象，以调用未在框架中封装的 Redis 更多的方法。

## File缓存

```php
$cache = \Mini\Cache::factory ('File');

//写入一个名为 test 的缓存，值为 abc，有效时间为 3600 秒
$cache->set('test', 'abc', 3600);

//读取名为 test 的缓存
$test = $cache->get('test');
```

> 提示：使用 `File` 类型的缓存时，缓存文件会存储在默认路径 `App/Cache/` 中，你可以在应用入口文件 `App/ublic/index.php` 中，定义常量 `CACHE_PATH` 的值来改变存储路径。



