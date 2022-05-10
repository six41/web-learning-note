# 样式化链接

## 链接状态

- <strong>Link</strong> (没有访问过的): 这是链接的默认状态，当它没有处在其他状态的时候，它可以使用`:link` 伪类来应用样式。

- <strong>Visited</strong>: 这个链接已经被访问过了(存在于浏览器的历史纪录), 它可以使用 `:visited` 伪类来应用样式。

- <strong>Hover</strong>: 当用户的鼠标光标刚好停留在这个链接，它可以使用 `:hover` 伪类来应用样式。

- <strong>Focus</strong>: 一个链接当它被选中的时候 (比如通过键盘的 Tab  移动到这个链接的时候，或者使用编程的方法来选中这个链接 HTMLElement.focus() (en-US)) 它可以使用 `:focus` 伪类来应用样式。

- <strong>Active</strong>: 一个链接当它被激活的时候 (比如被点击的时候)，它可以使用 `:active` 伪类来应用样式。

## 链接默认的样式

- 链接具有下划线。
- 未访问过的 (Unvisited) 的链接是蓝色的。
- 访问过的 (Visited) 的链接是紫色的.
- 悬停 (Hover) 在一个链接的时候鼠标的光标会变成一个小手的图标。
- 选中 (Focus) 链接的时候，链接周围会有一个轮廓，你应该可以按 tab 来选中这个页面的链接 (在 Mac 上, 需要使用*Full Keyboard Access: All controls* 选项，然后再按下 Ctrl + F7 ，这样就可以起作用)
- 激活 (Active) 链接的时候会变成红色 (当你点击链接时，请尝试按住鼠标按钮。)

## 将样式应用到链接

```css
body {
  width: 300px;
  margin: 0 auto;
  font-size: 1.2rem;
  font-family: sans-serif;
}

p {
  line-height: 1.4;
}

a {
  outline: none;
  text-decoration: none;
  padding: 2px 1px 0;
}

a:link {
  color: #265301;
}

a:visited {
  color: #437A16;
}

a:focus {
  border-bottom: 1px solid;
  background: #BAE498;
}

a:hover {
  border-bottom: 1px solid;
  background: #CDFEAA;
}

a:active {
  background: #265301;
  color: #CDFEAA;
}
```

- 第三个规则使用了 `a` 选择器，取消了默认的文本下划线和链接被选中（focus）时的轮廓 （outline）（不同浏览器的默认行为可能不同），并为每个链接添加了少量的内边距（padding），所有这一切将在之后变得明确。
- 接着，使用`a:link`和`a:visited`选择器来设置未访问（unvisited）链接和访问过（visited）的链接的一点颜色上的变化，然后就能分辨开来了。
- 下面两条规则使用 `a:focus` 和 `a:hover` 来设置选中（focus）和悬停（hover）的链接为不同的背景颜色，再加上一个下划线，使链接更加突出。这里有两点需要注意：
  - 下划线是使用 [`border-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom) 创造的, 而不是 [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration)，因为前者比后者有更好的样式选项， 并且绘制的位置会稍微低一点，所以不会穿过字母 (比如 字母 g 和 y 底部).
  - [`border-bottom`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-bottom)的值被设置为`1px solid`，没有指定颜色。这样做可以使边框采用和元素文本一样的颜色，这在这样的情况下是很有用的，因为链接的每种状态下，文本是不同的颜色。
- 最后, `a:active` 用来给链接一个不同的配色方案，当链接被激活 (activated) 时，让链接被激活的时候更加明显。

## 链接中包含图标

```css
a[href*="http"] {
  background: url('https://mdn.mozillademos.org/files/12982/external-link-52.png') no-repeat 100% 0;
  background-size: 16px 16px;
  padding-right: 19px;
}
```

- 使用了 [`background`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background) 简写，而不是分别使用多个属性。设置了想要插入的图片的路径，指定了 `no-repeat` ，这样只插入了一次图片，然后指定位置为100%，使其出现在内容的右边，距离上方是0px。

- 使用 [`background-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size) 来指定要显示的背景图像的大小，为了满足响应式网站设计的需要，在图标更大，需要再重新调整它的大小的时候，这样做是很有帮助的。

- 在链接上设置 [`padding-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding-right) ，为背景图片留出空间，这样就不会让它和文本重叠了。

## 样式化链接为按钮

```css
body,html {
  margin: 0;
  font-family: sans-serif;
}

ul {
  padding: 0;
  width: 100%;
}

li {
  display: inline;
}

a {
  outline: none;
  text-decoration: none;
  display: inline-block;
  width: 19.5%;
  margin-right: 0.625%;
  text-align: center;
  line-height: 3;
  color: black;
}

li:last-child a {
  margin-right: 0;
}

a:link, a:visited, a:focus {
  background: yellow;
}

a:hover {
  background: orange;
}

a:active {
  background: red;
  color: white;
}
```

- 第二条规则删除了 [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul) 元素的默认的 [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding)，然后设置了它的宽度是外部容器  [`<body>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/body) (在这次条件下) 的 100% 。
- [`<li>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/li) 元素通常默认是块元素 ，意味着它们各自会占用一行。在这个例子中，创建了一组水平列表的链接，所以在第三条规则中，设置了属性为 inline，这会导致列表中的每项内容都会一起出现在同一行，它们现在表现得就像内联元素。
- 第四条规则，主要是 [`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素的样式，这里比较复杂; 让我们一步一步来看：
  - 和前面的例子一样，我们首先关掉了 [`text-decoration`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/text-decoration) 和 [`outline`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/outline)。
  - 接着，设置 [`display`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 为 `inline-block` ，[`<a>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a) 元素默认为内联元素，而且不希望它们像值为 `block` 时一样，线条超出自己的内容，我们确实想要控制它们的大小`inline-block` 允许我们这样做。
  - 接着是尺寸的设置! 要填满整个 [`<ul>`](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/ul) 的宽度，为按钮之间留一些间距 (margin)  (但不是右边边缘的间距)。按钮的大小应该一样。为了做到这一点，设置 [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 为 19.5%，然后 [`margin-right`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin-right) 为 0.625%. 所有宽度加起来是 100.625%, 这样会让最后一个按钮溢出 `<ul>` ，然后显示到下一行中。但是，我们使用了下一条规则让它恢复到了 100%，这条规则选中了列表中的最后一个 `<a>`元素，然后删除了它的间距 (margin)。完成!
  - 最后三条声明就比较简单了，主要是为链接各个状态添加了颜色。居中了每个链接中的文本，设置 [`line-height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/line-height) 为 3， 让按钮有一些高度 (这也具有垂直居中文本的优点)，并设置文本的颜色为黑色。
