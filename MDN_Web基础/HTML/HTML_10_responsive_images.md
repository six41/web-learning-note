# HTML Responsive images

最近应用的**响应式图像技术**，通过让浏览器提供多个图像文件来解决上述问题，比如使用相同显示效果的图片但包含多个不同的分辨率（分辨率切换），或者使用不同的图片以适应不同的空间分配（美术设计）。

> CSS是比HTML更好的响应式设计工具

```HTML
<img srcset="elva-fairy-320w.jpg 320w,
             elva-fairy-480w.jpg 480w,
             elva-fairy-800w.jpg 800w"
     sizes="(max-width: 320px) 280px,
            (max-width: 480px) 440px,
            800px"
     src="elva-fairy-800w.jpg" alt="Elva dressed as a fairy">
```

可以使用两个新的属性——**srcset** 和 **sizes**——来提供更多额外的资源图像和提示，帮助浏览器选择正确的一个资源。

### srcset

srcset定义了我们允许浏览器选择的图像集，以及每个图像的大小。
1. 一个文件名 (elva-fairy-480w.jpg.)
2. 一个空格
3. 图像的固有宽度（以像素为单位）（480w）——注意到这里使用w单位，而不是预计的px,这是图像的真实大小

### sizes

sizes定义了一组媒体条件（例如屏幕宽度），并且指明当某些媒体条件为真时，什么样的图片尺寸是最佳选择。应该包含

1. 一个媒体条件（(max-width:480px)
2. 一个空格
3. 当媒体条件为真时，图像将填充的槽的宽度（440px）

### 浏览器执行的操作

1. 查看设备宽度
2. 检查sizes列表中哪个媒体条件是第一个为真
3. 查看给予该媒体查询的槽大小
4. 加载srcset列表中引用的最接近所选的槽大小的图像

让浏览器通过srcset和x语法结合来选择适当分辨率的图片

```HTML
<img srcset="elva-fairy-320w.jpg,
             elva-fairy-480w.jpg 1.5x,
             elva-fairy-640w.jpg 2x"
     src="elva-fairy-640w.jpg" alt="Elva dressed as a fairy">
```

在这个例子中，下面的CSS会应用在图片上，所以它的宽度在屏幕上是320像素（也称作CSS像素）：

```CSS
img {
  width: 320px;
}
```

## &lt;picture&gt;

```HTML
<picture>
  <source media="(max-width: 799px)" srcset="elva-480w-close-portrait.jpg">
  <source media="(min-width: 800px)" srcset="elva-800w.jpg">
  <img src="elva-800w.jpg" alt="Chris standing up holding his daughter Elva">
</picture>
```

- `<source>`元素包含一个media属性，这一属性包含一个媒体条件——就像第一个srcset例子，这些条件来决定哪张图片会显示——第一个条件返回真，那么就会显示这张图片
- srcset属性包含要显示图片的路径。请注意，正如我们在`<img>`上面看到的那样，`<source>`可以使用引用多个图像的srcset属性，还有sizes属性。所以可以通过一个 <picture>元素提供多个图片，不过也可以给每个图片提供多分辨率的图片
- 在任何情况下，都必须在 `</picture>`之前正确提供一个`<img>`元素以及它的src和alt属性，否则不会有图片显示


```HTML
<picture>
  <source type="image/svg+xml" srcset="pyramid.svg">
  <source type="image/webp" srcset="pyramid.webp">
  <img src="pyramid.png" alt="regular pyramid built from four equilateral triangles">
</picture>
```

- 不要使用media属性，除非需要美术设计
- 在`<source>` 元素中，你只可以引用在type中声明的文件类型
- 像之前一样，如果必要，你以在srcset和sizes中使用逗号分割的列表