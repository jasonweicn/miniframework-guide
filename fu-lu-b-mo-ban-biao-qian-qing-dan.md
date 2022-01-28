# 附录B：模板标签清单

---

## {$变量名}

用途说明：标记输出一个通过 $this-&gt;view-&gt;assign\(\) 方法传入 View 的变量。

示例代码：

```php
<p>{$info}</p>
```

编译输出：

```php
<p><?php echo $this->info; ?></p>
```

## {$数组名.元素}

用途说明：标记输出一个通过 $this-&gt;view-&gt;assign\(\) 方法传入 View 的数组元素。

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

用途说明：标记输出一个通过 $this-&gt;view-&gt;assign\(\) 方法传入 View 的对象属性。

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

用途说明：标记输出一个常量。

示例代码：

```php
<p>这是一个常量：{const:APP_NAME}</p>
```

编译输出：

```php
<p>这是一个常量：MiniFramework</p>
```

> 提示：如果常量存在，会直接将值输出

## {layout:布局名}

用途说明：标记加载布局

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

> 提示：模板引擎会检查并渲染 Layout

## {beginBlock:代码块名} 和 {endBlock:代码块名}

用途说明：标记一个代码块区域

示例代码：

```js
{beginBlock:myblock}
<script>
/*
这是一个 Block 的示例
  通常我们会希望 js 代码放到页面底部运行，
  在使用布局的情况下，可以在 View 中通过 beginBlock 和 endBlock 预定义一个代码块，
  在 Layout 文件中，可以通过 inserBlock 将对应的代码块插入到需要的地方。（请见 Layout/default.php）
*/
console.log('this is block');
</script>
{endBlock:myblock}
```

编译输出：

```php
<?php $this->beginBlock("myblock"); ?>
<script>
/*
这是一个 Block 的示例
  通常我们会希望 js 代码放到页面底部运行，
  在使用布局的情况下，可以在 View 中通过 beginBlock 和 endBlock 预定义一个代码块，
  在 Layout 文件中，可以通过 inserBlock 将对应的代码块插入到需要的地方。
*/
console.log('this is block');
</script>
<?php $this->endBlock("myblock"); ?>
```

> 提示：结束代码块可以省略名称简写为 {$endBlock}

## {insertBlock:代码块名}

用途说明：标记插入指定名称的代码块区域的代码。

示例代码：

```php
<html>
    <body>
        <p>如果这里是 Layout，可以将在 View 中定义的代码块插入到当前的 Layout 中。</p>
    </body>
</html>
{insertBlock:myblock}
```

编译输出：

```php
<html>
    <body>
        <p>如果这里是 Layout，可以将在 View 中定义的代码块插入到当前的 Layout 中。</p>
    </body>
</html>
<?php $this->insertBlock("myblock"); ?>
```



