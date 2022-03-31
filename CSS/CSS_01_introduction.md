# Cascading Style Sheets

层叠样式表

CSS 可以用于给文档添加样式 —— 比如改变标题和链接的颜色及大小。它也可用于创建布局 —— 比如将一个单列文本变成包含主要内容区域和存放相关信息的侧边栏区域的布局。它甚至还可以用来做一些特效，比如动画。

```CSS
h1 {
    color: red;
    font-size: 5em;
}
```

语法由一个<strong>选择器(selector)</strong>起头。 它选择(selects) 了我们将要用来添加样式的 HTML 元素。 在这个例子中我们为一级标题（主标题&lt;h1&gt; (en-US)）添加样式。

接着输入一对大括号{ }。 在大括号内部定义一个或多个形式为<strong>属性(property):值(value)</strong>; 的声明(declarations)。每个声明都指定了我们所选择元素的一个属性，之后跟一个我们想赋给这个属性的值。

冒号之前是属性，冒号之后是值。不同的 CSS 属性(properties) (en-US) 对应不同的合法值。在这个例子中，我们指定了 color 属性，它可以接受许多颜色值；还有 font-size 属性，它可以接收许多 size units 值。

## 模块

CSS 由许多<em>模块(modules)</em> 构成

## 链接CSS和HTML

为了把 styles.css 和 index.html 连接起来，可以在 HTML 文档中，&lt;head&gt; 语句模块里面加上下面的代码：

```HTML
<link rel="stylesheet" href="styles.css">
```

## 改变浏览器的默认行为

```CSS
li {
  list-style-type: none;
}
```

移除了列表元素li的浏览器定义的默认样式

## 使用类名

给HTML元素添加class属性

```HTML
<ul>
  <li>项目一</li>
  <li class="special">项目二</li>
  <li>项目 <em>三</em></li>
</ul>
```

在 CSS 中，要选中这个 special 类，只需在选择器的开头加个西文句点（.）。

```CSS
.special {
  color: orange;
  font-weight: bold;
}
```

有时你会发现选择器中，HTML 元素选择器跟类一起出现：

```CSS
li.special {
  color: orange;
  font-weight: bold;
}
```

这个意思是说，“选中每个 special 类的 li 元素”。还可以加上&lt;span&gt;元素，如下面例子

```CSS
li.special,
span.special {
  color: orange;
  font-weight: bold;
}
```

## 根据元素在文档的位置确定样式

```CSS
li em {
  color: rebeccapurple;
}
```

该选择器将选择&lt;li&gt;内部的任何&lt;em&gt;元素（&lt;li&gt;的后代）。

在 HTML 文档中设置直接出现在标题后面并且与标题具有相同层级的段落样式，为此需在两个选择器之间添加一个 + 号 (成为 相邻选择符)

```CSS
h1 + p {
  font-size: 200%;
}
```

## 根据状态确定样式

当我们修改一个链接的样式时我们需要定位（针对） <a> （锚）标签。

取决于是否是未访问的、访问过的、被鼠标悬停的、被键盘定位的，亦或是正在被点击当中的状态，这个标签有着不同的状态。

可以使用CSS去定位或者说针对这些不同的状态进行修饰，下面的CSS代码使得没有被访问的链接颜色变为粉色、访问过的链接变为绿色以及鼠标悬浮在链接上的时候移除下划线。

```CSS
a:link {
  color: pink;
}

a:visited {
  color: green;
}

a:hover {
  text-decoration: none;
}
```

## 同时使用选择器和选择符

```CSS
/* selects any <span> that is inside a <p>, which is inside an <article>  */
article p span { ... }

/* selects any <p> that comes directly after a <ul>, which comes directly after an <h1>  */
h1 + ul + p { ... }

body h1 + p .special {
  color: yellow;
  background-color: black;
  padding: 5px;
}
```

上面的代码为以下元素建立样式：在`<body>`之内，紧接在`<h1>`后面的`<p>`元素的内部，类名为 special。

> 区分`body h1{`和`h1, li {`，前者为body之内的h1，后者为h1 和 li
