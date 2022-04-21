# 背景与边框

```css
.box {
  background: linear-gradient(105deg, rgba(255,255,255,.2) 39%, rgba(51,56,57,1) 96%) center center / 400px 200px no-repeat,
  url(big-star.png) center no-repeat, rebeccapurple;
} 
```

## 背景颜色

background-color属性定义了CSS中任何元素的背景颜色。属性接受任何有效的`<color>`值。背景色扩展到元素的内容和内边距的下面。

## 背景图片

background-image属性允许在元素的背景中显示图像。

### 控制背景图像平铺

background-repeat属性用于控制图像的平铺行为。可用的值是:

- no-repeat — 不重复。
- repeat-x —水平重复。
- repeat-y —垂直重复。
- repeat — 在两个方向重复。

### 调整背景图像大小

可以使用 background-size属性，它可以设置长度或百分比值，来调整图像的大小以适应背景。

也可以使用关键字:

- cover —浏览器将使图像足够大，使它完全覆盖了盒子区，同时仍然保持其高宽比。在这种情况下，有些图像可能会跳出盒子外
- contain — 浏览器将使图像的大小适合盒子内。在这种情况下，如果图像的长宽比与盒子的长宽比不同，则可能在图像的任何一边或顶部和底部出现间隙。

### 背景图像定位

background-position属性允许您选择背景图像显示在其应用到的盒子中的位置。它使用的坐标系中，框的左上角是(0,0)，框沿着水平(x)和垂直(y)轴定位。

最常见的背景位置值有两个单独的值——一个水平值后面跟着一个垂直值。

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top center;
} 
```

或者使用 长度值, and 百分比：

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: 20px 10%;
} 
```

也可以混合使用关键字，长度值以及百分比，例如：

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top 20px;
}
```

还可以使用4-value语法来指示到盒子的某些边的距离——在本例中，长度单位是与其前面的值的偏移量。所以在下面的CSS中，我们将背景从顶部调整20px，从右侧调整10px:

```css
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top 20px right 10px;
} 
```

## 同时使用多个背景图片

```css
background-image: url(image1.png), url(image2.png), url(image3.png), url(image1.png);
background-repeat: no-repeat, repeat-x, repeat;
background-position: 10px 20px,  top right;
```

## 渐变背景

```css
.a {
  background-image: linear-gradient(105deg, rgba(0,249,255,1) 39%, rgba(51,56,57,1) 96%);
}

.b {
  background-image: radial-gradient(circle, rgba(0,249,255,1) 39%, rgba(51,56,57,1) 96%);
  background-size: 100px 50px;
} 
```

## 背景附加

这是由background-attachment属性控制的，它可以接受以下值:

- `scroll`: 使**元素的背景**在页面滚动时滚动。如果滚动了元素内容，则背景不会移动。实际上，背景被固定在页面的相同位置，所以它会随着页面的滚动而滚动。
- `fixed`: 使元素的背景固定在视图端口上，这样当页面或元素内容滚动时，它就不会滚动。它将始终保持在屏幕上相同的位置。
- `local`: 这个值是后来添加的(它只在Internet Explorer 9+中受支持，而其他的在IE4+中受支持)，因为滚动值相当混乱，在很多情况下并不能真正实现您想要的功能。局部值将背景固定在设置的元素上，因此当您滚动元素时，背景也随之滚动。

background-attachment属性只有在有内容要滚动时才会有效果

可以查看下面的示例

[Background attachment example](https://mdn.github.io/learning-area/css/styling-boxes/backgrounds/background-attachment.html)

# 边框

使用一个简写属性在一行CSS中设置边框的颜色、宽度和样式。

```css
.box {
  border: 1px solid black;
} 
```

仅设置一个边

```css
.box {
  border-top: 1px solid black;
} 
```

这些简写的等价于：

```css
.box {
  border-width: 1px;
  border-style: solid;
  border-color: black;
} 
```

也可以使用更加细粒度的属性：

```css
.box {
  border-top-width: 1px;
  border-top-style: solid;
  border-top-color: black;
} 
```

## 圆角

要使一个盒子的四个角都有10px的圆角半径：

```css
.box {
  border-radius: 10px;
} 
```

或使右上角的水平半径为1em，垂直半径为10％：

```css
.box {
  border-top-right-radius: 1em 10%;
} 
```