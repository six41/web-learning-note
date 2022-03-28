# HTML other embedding technologies

## &lt;iframe&gt;

`<iframe>`元素旨在允许您将其他Web文档嵌入到当前文档中。

```HTML
<iframe src="https://developer.mozilla.org/en-US/docs/Glossary"
        width="100%" height="500" frameborder="0"
        allowfullscreen sandbox>
  <p> <a href="https://developer.mozilla.org/en-US/docs/Glossary">
    Fallback link for browsers that don't support iframes
  </a> </p>
</iframe>
```

#### allowfullscreen

如果设置，`<iframe>`则可以通过全屏API设置为全屏模式（稍微超出本文的范围）。

#### frameborder

如果设置为1，则会告诉浏览器在此框架和其他框架之间绘制边框，这是默认行为。0删除边框。不推荐这样设置，因为在CSS中可以更好地实现相同的效果。border: none;

#### src

该属性与`<video>/<img>`一样包含指向要嵌入文档的URL路径。

#### width和height

这些属性指定您想要的iframe的宽度和高度。

#### 备选内容

与`<video>`等其他类似元素相同，您可以在`<iframe></iframe>`标签之间包含备选内容，如果浏览器不支持`<iframe>`，将会显示备选内容，这种情况下，我们已经添加了一个到该页面的链接。现在您几乎不可能遇到任何不支持`<iframe>`的浏览器。

#### sandbox

该属性需要在已经支持其他`<iframe>`功能（例如IE 10及更高版本）但稍微更现代的浏览器上才能工作，该属性可以提高安全性设置; 我们将在下一节中更加详细地谈到。

### 安全隐患

- 只有在必要时嵌入
- 使用 HTTPS
  1. HTTPS减少了远程内容在传输过程中被篡改的机会
  2. HTTPS防止嵌入式内容访问您的父文档中的内容，反之亦然
- 始终使用`sandbox`属性
  - 默认情况下，您应该使用没有参数的sandbox属性来强制执行所有可用的限制
- 配置CSP指令
  - CSP代表内容安全策略，它提供一组HTTP标头（由web服务器发送时与元数据一起发送的元数据），旨在提高HTML文档的安全性。

## `<embed>`和`<object>`元素

`<embed>`和`<object>`元素的功能不同于`<iframe>`—— 这些元素是用来嵌入多种类型的外部内容的通用嵌入工具，其中包括像Java小程序和Flash，PDF（可在浏览器中显示为一个PDF插件）这样的插件技术，甚至像视频，SVG和图像的内容。

> 插件是一种对浏览器原生无法读取的内容提供访问权限的软件。

|     | &lt;embed&gt;  |  &lt;object&gt;  |
|  :---:  | :----:  | :----:  |
| 嵌入内容的网址  | src | data |
| 嵌入内容的准确媒体类型  | type | type |
| 由插件控制的框的高度和宽度（以CSS像素为单位）  | height width | height width |
| 名称和值，将插件作为参数提供  | 	具有这些名称和值的ad hoc属性 | 单标签`<param>`元素，包含在内`<object>` |
| 独立的HTML内容作为不可用资源的回退  | 不支持 | 包含在元素`<object>`之后`<param>` |