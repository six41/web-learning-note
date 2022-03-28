# HTML vector graphics

位图使用像素网格来定义 — 一个位图文件精确得包含了每个像素的位置和它的色彩信息。流行的位图格式包括 Bitmap (.bmp), PNG (.png), JPEG (.jpg), and GIF (.gif.)

矢量图使用算法来定义 — 一个矢量图文件包含了图形和路径的定义，电脑可以根据这些定义计算出当它们在屏幕上渲染时应该呈现的样子。 SVG 格式可以让我们创造用于 Web 的精彩的矢量图形。

矢量图形相较于同样的位图，通常拥有更小的体积，因为它们仅需储存少量的算法，而不是逐个储存每个像素的信息。

SVG 是用于描述矢量图像的XML语言。 

```XML
<svg version="1.1"
     baseProfile="full"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="black" />
  <circle cx="150" cy="100" r="90" fill="blue" />
</svg>
```

<svg version="1.1"
     baseProfile="full"
     width="300" height="200"
     xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="black" />
  <circle cx="150" cy="100" r="90" fill="blue" />
</svg>

矢量图像中的文本仍然可访问（这也有利于 SEO)）。

SVG 可以很好地适应样式/脚本，因为图像的每个组件都是可以通过CSS或通过JavaScript编写的样式的元素。

SVG非常容易变得复杂，这意味着文件大小会增加; 复杂的SVG也会在浏览器中占用很长的处理时间。

SVG可能比栅格图像更难创建，具体取决于您尝试创建哪种图像。

## 将SVG添加到页面

### &lt;img&gt;方式

```HTML
<img
    src="equilateral.svg"
    alt="triangle with all three sides equal"
    height="87px"
    width="100px" />
```

#### 缺点

- 法使用JavaScript操作图像。
- 如果要使用CSS控制SVG内容，则必须在SVG代码中包含内联CSS样式。 （从SVG文件调用的外部样式表不起作用）
- 不能用CSS伪类来重设图像样式（如:focus）。

对于不支持SVG的浏览器，可以从src属性引用PNG或JPG，并使用srcset属性 只有最近的浏览器才能识别）来引用SVG。

```HTML
<img src="equilateral.png" alt="triangle with equal sides" srcset="equilateral.svg">
```

可以使用SVG作为CSS背景图像

```CSS
background: url("fallback.png") no-repeat center;
background-image: url("image.svg");
background-size: contain;
```

## SVG内联

在文本编辑器中打开SVG文件，复制SVG代码，并将其粘贴到HTML文档中

```HTML
<svg width="300" height="200">
    <rect width="100%" height="100%" fill="green" />
</svg>
```

<svg width="300" height="200">
    <rect width="100%" height="100%" fill="green" />
</svg>

#### 优点

- 将 SVG 内联减少 HTTP 请求，可以减少加载时间。
- 可以为 SVG 元素分配class和id，并使用 CSS 修改样式，无论是在SVG中，还是 HTML 文档中的 CSS 样式规则。 实际上，可以使用任何 SVG外观属性 作为CSS属性。
- 内联SVG是唯一可以让您在SVG图像上使用CSS交互（如:focus）和CSS动画的方法（即使在常规样式表中）。
- 可以通过将 SVG 标记包在`<a>`元素中，使其成为超链接。

#### 缺点

- 这种方法只适用于在一个地方使用的SVG。多次使用会导致资源密集型维护（resource-intensive maintenance）。
- 额外的 SVG 代码会增加HTML文件的大小。
- 浏览器不能像缓存普通图片一样缓存内联SVG。
- 可能会在`<foreignObject>` 元素中包含回退，但支持 SVG 的浏览器仍然会下载任何后备图像。- 需要考虑仅仅为支持过时的浏览器，而增加额外开销是否真的值得。

## 使用`<iframe>`嵌入SVG

```HTML
<iframe src="triangle.svg" width="500" height="500" sandbox>
    <img src="triangle.png" alt="Triangle with three unequal sides" />
</iframe>
```

iframe有一个**回退机制**，如果浏览器不支持iframe，则只会显示回退。

此外，除非 SVG 和您当前的网页具有相同的 origin，否则你不能在主页面上使用 JavaScript 来操纵 SVG。

