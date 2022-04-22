# 图像、媒体和表单

## 替换元素

图像和视频被描述为替换元素。 这意味着CSS不能影响这些元素的内部布局-仅影响它们在页面上于其他元素中的位置。

### object-fit属性

当使用`object-fit`时，替换元素可以以多种方式被调整到合乎盒子的大小

<img title="" src="image/obeject_fit.jpg" alt="example">

```css
.cover {
  object-fit: cover;
}

.contain {
  object-fit: contain;
}
```

```html
<div class="wrapper">
  <div class="box"><img src="balloons.jpg" alt="balloons" class="cover"></div>
  <div class="box"><img src="balloons.jpg" alt="balloons" class="contain"></div>
</div>
```

- 使用值`cover`，缩小图像，维持了图像的比例，所以图像可以整齐地充满盒子，同时由于比例保持不变，图像的一部分将会被盒子裁切掉。

- 将`contain`作为值，图像将会缩放到足以放到盒子里面的大小。

- `fill`值，它可以让图像充满盒子，但是不会维持比例。

## form元素

允许文本输入的元素，例如`<input type="text">`，特定的类型例如`<input type="email">`以及`<textarea>`元素，是相当容易样式化的，它们会试图表现得和在你的页面上其他盒子一样。

<img title="" src="file:///image/input_type.jpg" alt="">

```css
input[type="text"],
input[type="email"] {
  border: 2px solid #000;
  margin: 0 0 1em 0;
  padding: 10px;
  width: 100%;
}

input[type="submit"] {
  border: 3px solid #333;
  background-color: #999;
  border-radius: 5px;
  padding: 10px 2em;
  font-weight: bold;
  color: #fff;
}

input[type="submit"]:hover {
  background-color: #333;
}
```

```html
<form>
  <div><label for="name">Name</label>
  <input type="text" id="name"></div>
  <div><label for="email">Email</label>
  <input type="email" id="email"></div>

  <div class="buttons"><input type="submit" value="Submit"></div>
</form>
```

> 改变表单样式的时候小心，确保对于用户而言，它们仍然很容易被认出来是表单元素。你也许可以建立一个无边框的表单输入，其背景也与周围的内容难以区分开来，但是这会让表单很难识别和填入。

### 继承和表单元素

在一些浏览器中，表单元素默认不会继承字体样式，因此如果想要确保表单填入区域使用body中或者一个父元素中定义的字体，需要向CSS中加入这条规则。

```css
button,
input,
select,
textarea {
  font-family : inherit;
  font-size : 100%;
} 
```

### form元素和box-sizing

跨浏览器的form元素对于不同的挂件使用不同的盒子约束规则。

在样式化表单时候，可以使用box-sizing，确保在给form元素设定宽度和高度时可以有统一的体验。

为了保证统一，可以所有元素的内外边距均设为`0`，然后在单独进行样式化控制的时候将这些加回来。

```css
button,
input,
select,
textarea {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
```

### 其他有用的设置

除了上面提到的规则以外，也应该在`<textarea>`上设置`overflow: auto` 以避免IE在不需要滚动条的时候显示滚动条：

```css
textarea {
  overflow: auto;
}
```

### 将一切都放在一起“重置”

作为最后一步，我们可以将上面讨论过的各式属性包起来，成为以下的“表单重置”，以提供一个统一的在其上继续进行工作的地基，这包含了前三节提到的所有东西：

```css
button,input,select,textarea {
  font-family: inherit;
  font-size: 100%;
  box-sizing: border-box;
  padding: 0; 
  margin: 0;
}

textarea {
  overflow: auto;
} 
```

## Example 样式化表格

### 一个典型的HTML表格

```html
<table>
  <caption>A summary of the UK's most famous punk bands</caption>
  <thead>
    <tr>
      <th scope="col">Band</th>
      <th scope="col">Year formed</th>
      <th scope="col">No. of Albums</th>
      <th scope="col">Most famous song</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Buzzcocks</th>
      <td>1976</td>
      <td>9</td>
      <td>Ever fallen in love (with someone you shouldn't've)</td>
    </tr>
    <tr>
      <th scope="row">The Clash</th>
      <td>1976</td>
      <td>6</td>
      <td>London Calling</td>
    </tr>

      ... some rows removed for brevity

    <tr>
      <th scope="row">The Stranglers</th>
      <td>1974</td>
      <td>17</td>
      <td>No More Heroes</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th scope="row" colspan="2">Total albums</th>
      <td colspan="2">77</td>
    </tr>
  </tfoot>
</table>
```

---

### 间距和布局

```css
/* spacing */

table {
  table-layout: fixed;
  width: 100%;
  border-collapse: collapse;
  border: 3px solid purple;
}

thead th:nth-child(1) {
  width: 30%;
}

thead th:nth-child(2) {
  width: 20%;
}

thead th:nth-child(3) {
  width: 15%;
}

thead th:nth-child(4) {
  width: 35%;
}

th, td {
  padding: 20px;
}
```

### `table-layout: fixed;`

通常情况下，表列的尺寸会根据所包含的内容大小而变化，这会产生一些奇怪的结果。通过 table-layout: fixed，您可以根据列标题的宽度来规定列的宽度，然后适当地处理它们的内容。这就是为什么我们使用了thead th:nth-child(n) 选择了四个不同的标题(:nth-child)选择器（“选择第n个子元素，它是一个顺序排列的<th>元素，且其父元素是<thead>元素”）并给定了它们的百分比宽度。

### `thead th:nth-child(*n*)`

使用了`thead th:nth-child(*n*)` 选择了四个不同的标题`:nth-child`选择器（“选择第n个子元素，它是一个顺序排列的`<th>`元素，且其父元素是`<thead>`并给定了它们的百分比宽度。整个列宽度与列标题的宽度是一样的，这是一种很好的设定表列尺寸的方式。

### `border-collapse`

一个`border-collapse`属性的`collapse`值对于任何表样式的工作来说都是一个标准的最佳实践。默认情况下，当您在表元素上设置边框时，它们之间将会有间隔，如下图所示：

一个[``border-collapse`属性的`collapse`值对于任何表样式的工作来说都是一个标准的最佳实践。默认情况下，当您在表元素上设置边框时，它们之间将会有间隔，如下图所示：![](https://mdn.mozillademos.org/files/13068/no-border-collapse.png)

使用 `border-collapse: collapse;` ，让边框合为一条.

---

## 简单排版

```css
/* typography */

html {
  font-family: 'helvetica neue', helvetica, arial, sans-serif;
}

thead th, tfoot th {
  font-family: 'Rock Salt', cursive;
}

th {
  letter-spacing: 2px;
}

td {
  letter-spacing: 1px;
}

tbody td {
  text-align: center;
}

tfoot th {
  text-align: right;
}
```

## 图形和颜色

```css
thead, tfoot {
 background: url(leopardskin.jpg);
 color: white;
 text-shadow: 1px 1px 1px black;
}
thead th, tfoot th, tfoot td {
 background: linear-gradient(to bottom, rgba(0,0,0,0.1), rgba(0,0,0,0.5));
 border: 3px solid purple;
}
```

## 斑马条纹

`:nth-child`选择器用于选择特定的子元素。它也可以用一个公式作为参数，来选择一个元素序列.

在代码中使用了`odd`和`even`的关键字，在这里，我们给奇数行和偶数行不同的(醒目的)颜色。

```css
tbody tr:nth-child(odd) {
  background-color: #ff33cc;
}

tbody tr:nth-child(even) {
  background-color: #e495e4;
}

tbody tr {
  background-image: url(noise.png);
}

table {
  background-color: #ff33cc;
}
```

![](https://mdn.mozillademos.org/files/13074/table-with-color.png)

## 样式化标题

```css
caption {
  font-family: 'Rock Salt', cursive;
  padding: 20px;
  font-style: italic;
  caption-side: bottom;
  /*标题会被放在底部*/
  color: #666;
  text-align: right;
  letter-spacing: 1px;
}
```