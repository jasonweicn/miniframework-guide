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

## {const:常量名}

示例代码：

```php
<p>这是一个常量：{const:APP_NAME}</p>
```

编译输出：

```php
<p>这是一个常量：MiniFramework</p>
```

> 提示：如果常量存在，会直接将值输出

## {layout:布局}

示例代码：

```php
{layout:header}
<body>
    {layout:content}
</body>
{layout:footer}
```

编译输出：

```php
<?php echo $this->_layout->header; ?>
<body>
    <?php echo $this->_layout->content; ?>
</body>
<?php echo $this->_layout->footer; ?>
```



