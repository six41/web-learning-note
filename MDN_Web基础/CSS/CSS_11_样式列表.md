# 样式列表

#### 一个默认的列表

```html
<h2>Shopping (unordered) list</h2>

<p>Paragraph for reference, paragraph for reference, paragraph for reference,
paragraph for reference, paragraph for reference, paragraph for reference.</p>

<ul>
  <li>Humous</li>
  <li>Pitta</li>
  <li>Green salad</li>
  <li>Halloumi</li>
</ul>

<h2>Recipe (ordered) list</h2>

<p>Paragraph for reference, paragraph for reference, paragraph for reference,
paragraph for reference, paragraph for reference, paragraph for reference.</p>

<ol>
  <li>Toast pitta, leave to cool, then slice down the edge.</li>
  <li>Fry the halloumi in a shallow, non-stick pan, until browned on both sides.</li>
  <li>Wash and chop the salad.</li>
  <li>Fill pitta with salad, humous, and fried halloumi.</li>
</ol>

<h2>Ingredient description list</h2>

<p>Paragraph for reference, paragraph for reference, paragraph for reference,
paragraph for reference, paragraph for reference, paragraph for reference.</p>

<dl>
  <dt>Humous</dt>
  <dd>A thick dip/sauce generally made from chick peas blended with tahini, lemon juice, salt, garlic, and other ingredients.</dd>
  <dt>Pitta</dt>
  <dd>A soft, slightly leavened flatbread.</dd>
  <dt>Halloumi</dt>
  <dd>A semi-hard, unripened, brined cheese with a higher-than-usual melting point, usually made from goat/sheep milk.</dd>
  <dt>Green salad</dt>
  <dd>That green healthy stuff that many of us just use to garnish kebabs.</dd>
</dl>
```

-  `<ul>` 和 `<ol>`元素设置`margin`的顶部和底部: 16px(1em) 0;和 padding-left: 40px(2.5em); （在这里注意的是浏览器默认字体大小为16px）。
- `<li>`默认是没有设置间距的。
- `<dl>`  元素设置 margin的顶部和底部: 16px(1em) ，无内边距设定。
- `<dd>`元素设置为： `margin-left` `40px` (`2.5em`)。
- `<p>`元素设置 margin的顶部和底部: 16px(1em)，和其他的列表类型相同。

## 处理列表间距

创建样式列表时，需要调整样式，使其保持与周围元素相同的垂直间距（例如段落和图片，有时称为垂直节奏））和相互间的水平间距

```css
/* General styles */

html {
  font-family: Helvetica, Arial, sans-serif;
  font-size: 10px;
}

h2 {
  font-size: 2rem;
}

ul,ol,dl,p {
  font-size: 1.5rem;
}

li, p {
  line-height: 1.5;
}

/* Description list styles */


dd, dt {
  line-height: 1.5;
}

dt {
  font-weight: bold;
}

dd {
  margin-bottom: 1.5rem;
}
```

- 第一条规则集设置一个网站字体，基准字体大小为10px。 页面上的所有内容都将继承该规则集。
- 规则集2和3为标题、不同的列表类型和段落以及设置了相对字体大小（这些列表的子元素将会继承该规则集），这就意味着每个段落和列表都将拥有相同的字体大小和上下间距,有助于保持垂直间距一致。
- 规则集4在段落和列表项目上设置相同的 line-height ，因此段落和每个单独的列表项目将在行之间具有相同的间距。 这也将有助于保持垂直间距一致。
- 规则集5-7适用于描述列表 - 我们在描述列表的术语和其描述上设置与段落和列表项相同的行高，以及 margin-bottom 为1.5 rem（与段落（p）和列表项目（li））相同。 

## 列表特定样式

举例一些特定样式

### 符号样式

`list-style-type`：设置用于列表的项目符号的类型，例如无序列表的方形或圆形项目符号，或有序列表的数字，字母或罗马数字。

在有序列表上设置了大写罗马数字：

```css
ol {
  list-style-type: upper-roman;
}
```

<img src = "https://mdn.mozillademos.org/files/12962/outer-bullets.png">

### <a href= "https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Styling_text/Styling_lists#%E9%A1%B9%E7%9B%AE%E7%AC%A6%E5%8F%B7%E4%BD%8D%E7%BD%AE">项目符号位置</a>

`list-style-position` ：设置在每个项目开始之前，项目符号是出现在列表项内，还是出现在其外。

```css
ol {
  list-style-type: upper-roman;
  list-style-position: inside;
}
```

默认值为 outside，这使项目符号位于列表项之外。

如果值设置为 inside，项目条目则位于行内。

### 使用自定义的项目符号图片

`list-style-image` ：允许您为项目符号使用自定义图片，而不是简单的方形或圆形。

```css
ul {
  list-style-image: url(star.svg);
}
```

#### 样式化列表例子

```css
ul {
  padding-left: 2rem;
  list-style-type: none;
}

ul li {
  padding-left: 2rem;
  background-image: url(star.svg);
  background-position: 0 0;
  background-size: 1.6rem 1.6rem;
  background-repeat: no-repeat;
}
```

- 将 &lt;ul&gt; 的 padding-left 从默认的 40px设置为 20px，然后在列表项上设置相同的数值。 这就是说，整个列表项仍然排列在列表中，但是列表项产生了一些用于背景图像的填充。 如果我们没有设置填充，背景图像将与列表项文本重叠，这看起来会很乱。
- 将 list-style-type 设置为none，以便默认情况下不会显示项目符号。 我们将使用 background 属性来代替项目符号。
  为每个无序列表项插入项目符号，其相应的属性如下：
- background-image: 充当项目符号的图片文件的参考路径
- background-position: 这定义了所选元素背景中的图像将出现在哪里 - 在我们的示例中设置 0 0，这意味着项目符号将出现在每个列表项的最左上侧。
- background-size: 设置背景图片的大小。 理想条件下，我们想要项目符号与列表项的大小相同（比列表项稍大或稍小亦可）。 我们使用的尺寸为1.6rem（16px），它非常吻合我们为项目符号设置的 20px  的填充， 16px 加上 4px 的空格间距，可以使项目符号和列表项文本效果更好。
- background-repeat：默认条件下，背景图片不断复制直到填满整个背景空间，在我们的例子中，背景图片只需复制一次，所以我们设置值为 no-repeat。

<img src = "https://mdn.mozillademos.org/files/12956/image-bullets.png">

## list-style 速记

上述提到的三种属性可以用一个单独的速记属性 list-style 来设置。例如：

```css
ul {
  list-style-type: square;
  list-style-image: url(example.png);
  list-style-position: inside;
}
```

可以被如下方式代替：

```css
ul {
  list-style: square url(example.png) inside;
}
```

属性值可以任意顺序排列，可以设置一个，两个或者三个值（该属性的默认值为 disc, none, outside），如果指定了 type 和 image，如果由于某种原因导致图像无法加载，则 type 将用作回退。

## 管理列表计数

<strong>在有序列表上进行不同的计数方式。</strong>

### `start`

start 属性允许从1 以外的数字开始计数。

```css
<ol start="4">
  <li>Toast pitta, leave to cool, then slice down the edge.</li>
  <li>Fry the halloumi in a shallow, non-stick pan, until browned on both sides.</li>
  <li>Wash and chop the salad.</li>
  <li>Fill pitta with salad, humous, and fried halloumi.</li>
</ol>
```

### `reversed`

reversed 属性将启动列表倒计数。示例如下：

```css
<ol start="4" reversed>
  <li>Toast pitta, leave to cool, then slice down the edge.</li>
  <li>Fry the halloumi in a shallow, non-stick pan, until browned on both sides.</li>
  <li>Wash and chop the salad.</li>
  <li>Fill pitta with salad, humous, and fried halloumi.</li>
</ol>
```

### `value`

value 属性允许设置列表项指定数值，示例如下:

```css
<ol>
  <li value="2">Toast pitta, leave to cool, then slice down the edge.</li>
  <li value="4">Fry the halloumi in a shallow, non-stick pan, until browned on both sides.</li>
  <li value="6">Wash and chop the salad.</li>
  <li value="8">Fill pitta with salad, humous, and fried halloumi.</li>
</ol>
```