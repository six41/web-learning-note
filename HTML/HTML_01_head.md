# &lt;head&gt;元素

## 元数据

```HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="author" content="Siyi Liao">
    <meta name="description" content="Just a simple example.">
    <!-- meta元素为元数据 -->
    <link rel="icon" href="example.ico" type="image/x-icon">
    <!--在元数据中添加对自定义图标的引用 -->
    <title>我的HTML文档</title>
  </head>
  <body>
    <p>这是一个段落</p>
  </body>
</html>
```

## 应用CSS和JavaScript

使用 CSS 让网页更加炫酷，使用JavaScript让网页有交互功能

```HTML
<link rel="stylesheet" href="my-css-file.css">
```

&lt;link&gt; 元素经常位于文档的头部。这个link元素有2个属性，rel="stylesheet"表明这是文档的样式表，而 href包含了样式表文件的路径。

```HTML
<script src="my-js-file.js"></script>`
```

&lt;script&gt;元素一般不放在文档头部，放在尾部（在 &lt;/body&gt;标签之前）会更好。

这样可以确保在加载脚本之前浏览器已经解析了HTML内容

### 为HTML文档设定主语言

```HTML
`<html lang="zh-CN">`
```

**作用**

> HTML文档就会被搜索引擎更有效地索引，对于那些使用屏幕阅读器的视障人士也很有用。

将文档的分段设置为不同的语言。

```HTML
`<p>日语实例: <span lang="jp">ご飯が熱い。</span>.</p>`
```