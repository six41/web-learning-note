button,
input,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
  box-sizing: border-box;
  padding: 0; margin: 0;
}

textarea {
  overflow: auto;
} 都放在一起“重置”](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/Building_blocks/Images_media_form_elements#%E5%B0%86%E4%B8%80%E5%88%87%E9%83%BD%E6%94%BE%E5%9C%A8%E4%B8%80%E8%B5%B7%E2%80%9C%E9%87%8D%E7%BD%AE%E2%80%9D "Permalink to 将一切都放在一起“重置”")

### [将一切将一切都放在一起“重置”

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

### 将一切将一切都放在一起“重置”

作为最后一步，我们可以将上面讨论过的各式属性包起来，成为以下的“表单重置”，以提供一个统一的在其上继续进行工作的地基，这包含了前三节提到的所有东西：

```css
button,input,select,textarea {
  font-family: inherit;
  font-size: 100%;
  box-sizing: border-box;
  padding: 0; margin: 0;
}

textarea {
  overflow: auto;
} 
```
