# 附录B：模板标签清单

---

## {$变量名}

示例代码：

```php
<p>{$info}</p>
```

编译输出：

```php
<p><?php echo $this->info; ?></p>
```



## {$数组名.元素}

示例代码：

```php
<p>姓名：{$user.name}</p>
<p>性别：{$user.sex}</p>
```

编译输出：

```php
<p>姓名：<?php echo $this->user["name"]; ?></p>
<p>性别：<?php echo $this->user["sex"]; ?></p>
```



## {$对象名.属性}

示例代码：

```php
<p>姓名：{$user.name}</p>
<p>性别：{$user.sex}</p>
```

编译输出：

```php
<p>姓名：<?php echo $this->user->name; ?></p>
<p>性别：<?php echo $this->user->sex; ?></p>
```





