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

## 背景附加