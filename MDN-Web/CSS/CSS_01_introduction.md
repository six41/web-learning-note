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

---

# 如何构建CSS

## 内部样式表

内部样式表是指不使用外部CSS文件，而是将CSS放在HTML文件&lt;head&gt;标签里的&lt;style&gt;标签之中。

```HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>Hello World!</h1>
    <p>This is my first CSS example</p>
  </body>
</html>
```

## 内联样式表

内联样式表存在于HTML元素的style属性之中。其特点是每个CSS表只影响一个元素：

```HTML
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My CSS experiment</title>
  </head>
  <body>
    <h1 style="color: blue;background-color: yellow;border: 1px solid black;">Hello World!</h1>
    <p style="color:red;">This is my first CSS example</p>
  </body>
</html>
```

> **不要这么做！**
> 
> 1. 难以阅读
> 2. 将文档结构和文档表现混合

## CSS的专一性

CSS语言有规则来控制在发生碰撞时哪条规则将获胜--这些规则称为**级联规则**和**专用规则**。

`<p class="special">What color am I?</p>`

```CSS
<!--first sample-->
p {
  color: red;
}

p {
  color: blue;
}

<!--second sample-->
.special {
  color: red;
}

p {
  color: blue;
}
```

在第一个例子中，special类的&lt;p&gt;会被设置成蓝色。

因为将其设置为蓝色的声明将出现在样式表的后面，而稍后的样式将覆盖以前的样式。这就是起作用的<strong>级联规则</strong>。

第二个例子中，special类的&lt;p&gt;会被设置成红色。因为同时使用了类选择器和元素选择器，而一个类被描述为比元素选择器更具体，或者具有更多的特异性，这里起作用的就是**专用规则**。

## CSS的属性和值

### 属性

人类可读的标识符，指示您想要更改的样式特征(例如font-size, width, background-color) 你想改变。

### 值

每个指定的属性都有一个值，该值指示您希望如何更改这些样式特性(例如，要将字体、宽度或背景色更改为。)

## 函数

`<div class="outer"><div class="box">The inner box is 90% - 30px.</div></div>`

### calc函数

支持在CSS中进行简单的计算

```CSS
.outer {
  border: 5px solid black;
}

.box {
  padding: 10px;
  width: calc(90% - 30px);

  /*要求box的宽度是框宽的的90%再减去30像素*/

  background-color: rebeccapurple;
  color: white;
}
```

### rotate函数

```CSS
.box {
  margin: 30px;
  width: 100px;
  height: 100px;
  background-color: rebeccapurple;
  transform: rotate(0.8turn)
}
```

## @规则

at-rules是一些特殊的规则，为 CSS提供了一些关于如何表现的指导。

将额外的样式表导入主CSS样式表，可以使用@import:

`@import 'styles2.css';`

#### @media规则

允许使用**媒体查询**来应用CSS，仅当某些条件成立(例如，当屏幕分辨率高于某一数量，或屏幕宽度大于某一宽度时)。

```CSS
body {
  background-color: pink;
}

@media (min-width: 30em) {
  body {
    background-color: blue;
  }
}
```

给 <body> 元素一个粉红色的背景色。但是，随后使用@media创建样式表的一个规则，该部分仅适用于视口大于30em的浏览器。如果浏览器的宽度大于30em，则背景色将为蓝色。

## 速记属性

一些属性，如 font, background, padding, border, and margin 等属性称为速记属性--这是因为它们允许在一行中设置多个属性值，从而节省时间并使代码更整洁。

```CSS
/*第一个例子*/
/* In 4-value shorthands like padding and margin, the values are applied
   in the order top, right, bottom, left (clockwise from the top). There are also other
   shorthand types, for example 2-value shorthands, which set padding/margin
   for top/bottom, then left/right */
padding: 10px 15px 15px 5px;

/*上面这一行代码效果等价于下面这四行*/

padding-top: 10px;
padding-right: 15px;
padding-bottom: 15px;
padding-left: 5px;

/*第二个例子*/

background: red url(bg-graphic.png) 10px 10px repeat-x fixed;

/*上面这一行代码效果等价于下面这五行*/

background-color: red;
background-image: url(bg-graphic.png);
background-position: 10px 10px;
background-repeat: repeat-x;
background-attachment: fixed;
```

# CSS如何工作

1. 浏览器载入HTML文件（比如从网络上获取）。
2. 将HTML文件转化成一个DOM（Document Object Model），DOM是文件在计算机内存中的表现形式。
3. 接下来，浏览器会拉取该HTML相关的大部分资源，比如嵌入到页面的图片、视频和CSS样式。
4. JavaScript则会稍后进行处理。
5. 浏览器拉取到CSS之后会进行解析，根据选择器的不同类型（比如element、class、id等等）把他们分到不同的“桶”中。浏览器基于它找到的不同的选择器，将不同的规则（基于选择器的规则，如元素选择器、类选择器、id选择器等）应用在对应的DOM的节点中，并添加节点依赖的样式（这个中间步骤称为渲染树）。
6. 上述的规则应用于渲染树之后，渲染树会依照应该出现的结构进行布局。
7. 网页展示在屏幕上（这一步被称为着色）。

<img src='https://media.prod.mdn.mozit.cloud/attachments/2015/10/14/11781/ab96f980498d7c46fe26f6df06b9acfc/rendering.svg'>

## about DOM

一个DOM有一个树形结构，标记语言中的每一个元素、属性以及每一段文字都对应着结构树中的一个节点（Node/DOM或DOM node）。

节点由节点本身和其他DOM节点的关系定义，有些节点有父节点，有些节点有兄弟节点（同级节点）。

```HTML
<p>
  Let's use:
  <span>Cascading</span>
  <span>Style</span>
  <span>Sheets</span>
</p>
```

上面的HTML代码对应的DOM树

```
P
├─ "Let's use:"
├─ SPAN
|  └─ "Cascading"
├─ SPAN
|  └─ "Style"
└─ SPAN
   └─ "Sheets"
```