# 格式化文本

# 样式化文字

用于样式文本的 CSS 属性通常可以分为两类

- **字体样式**: 作用于字体的属性，会直接应用到文本中，比如使用哪种字体，字体的大小是怎样的，字体是粗体还是斜体，等等。
- **文本布局风格**: 作用于文本的间距以及其他布局功能的属性，比如，允许操纵行与字之间的空间，以及在内容框中，文本如何对齐。

## 字体

### 颜色

color 属性设置选中元素的前景内容的颜色 (通常指文本，不过也包含一些其他东西，或者是使用 text-decoration 属性放置在文本下方或上方的线 (underline overline)。

```css
text-decoration: underline dotted;
/*虚线*/

text-decoration: green wavy underline;
/*绿色波浪线*/

text-decoration: underline overline #FF3028;
/*上下各一条红线*/
```

### 字体种类

要在你的文本上设置一个不同的字体，你可以使用 font-family  属性

```css
p {
  font-family: arial;
}
```

### 网页安全字体

说到字体可用性只有某几个字体通常可以应用到所有系统，可以毫无顾忌地使用。

这些都是所谓的 **网页安全字体**。

| 字体名称            | 泛型         | 注意                                                                                        |
| --------------- | ---------- | ----------------------------------------------------------------------------------------- |
| Arial           | sans-serif | 通常认为最佳做法还是添加 Helvetica 作为 Arial 的首选替代品，尽管它们的字体面几乎相同，但 Helvetica 被认为具有更好的形状，即使Arial更广泛地可用。 |
| Courier New     | monospace  | 某些操作系统有一个 Courier New 字体的替代（可能较旧的）版本叫Courier。使用Courier New作为Courier的首选替代方案，被认为是最佳做法。      |
| Georgia         | serif      |                                                                                           |
| Times New Roman | serif      | 某些操作系统有一个 Times New Roman 字体的替代（可能较旧的）版本叫 Times。使用Times作为Times New Roman的首选替代方案，被认为是最佳做法。 |
| Trebuchet MS    | sans-serif | 您应该小心使用这种字体——它在移动操作系统上并不广泛。                                                               |
| Verdana         | sans-serif |                                                                                           |

### 默认字体

CSS 定义了 5 个常用的字体名称:  `serif,` `sans-serif,` `monospace`, `cursive,`和 `fantasy.` 这些都是非常通用的，当使用这些通用名称时，使用的字体完全取决于每个浏览器，而且它们所运行的每个操作系统也会有所不同。

| 名称           | 定义                                    |
| ------------ | ------------------------------------- |
| `serif`      | 有衬线的字体 （衬线一词是指字体笔画尾端的小装饰，存在于某些印刷体字体中） |
| `sans-serif` | 没有衬线的字体。                              |
| `monospace`  | 每个字符具有相同宽度的字体，通常用于代码列表。               |
| `cursive`    | 用于模拟笔迹的字体，具有流动的连接笔画。                  |
| `fantasy`    | 用来装饰的字体                               |

### 字体栈

由于无法保证想在网页上使用的字体的可用性 (甚至一个网络字体可能由于某些原因而出错), 可以提供一个**字体栈** (**font stack**)，这样的话，浏览器就有多种字体可以选择了。只需包含一个`font-family属性`，其值由几个用逗号分离的字体名称组成。比如

```css
p {
  font-family: "Trebuchet MS", Verdana, sans-serif;
}
```

在这种情况下，浏览器从列表的第一个开始，然后查看在当前机器中，这个字体是否可用。如果可用，就把这个字体应用到选中的元素中。如果不可用，它就移到列表中的下一个字体，然后再检查。

在字体栈的最后提供一个合适的通用的字体名称，这样的话，即使列出的字体都无法使用，浏览器至少可以提供一个还算合适的选择。

> **注意**: 有一些字体名称不止一个单词，比如`Trebuchet MS` ，那么就需要用引号包裹。

---

### 字体大小

在调整字体大小时，最常用的单位是：

- `px` (像素): 将像素的值赋予给文本。是一个绝对单位， 它导致了在任何情况下，页面上的文本所计算出来的像素值都是一样的。
- `em`: 1em 等于我们设计的当前元素的父元素上设置的字体大小。 可以使用`em`调整任何东西的大小，不只是文本。
- `rem`: 这个单位的效果和 `em` 差不多，除了 1`rem` 等于 HTML 中的根元素的字体大小， 而不是父元素。

元素的 `font-size` 属性是从该元素的父元素继承的。

从整个文档的根元素——`<html>`开始，浏览器的 font-size 标准设置的值为 16px。在根元素中的任何段落 (或者那些浏览器没有设置默认大小的元素)，会有一个最终的大小值：16px。其他元素也许有默认的大小，比如 <h1> (en-US) 元素有一个 2em 的默认值，所以它的最终大小值为 32px。

---

### 字体样式，字体粗细，文本转换和文本装饰

CSS 提供了 4 种常用的属性来改变文本的样子：

- `font-style`: 用来打开和关闭文本 italic (斜体)。 可能的值如下 (你很少会用到这个属性，除非你因为一些理由想将斜体文字关闭斜体状态)：
  
  - `normal`: 将文本设置为普通字体 (将存在的斜体关闭)
  - `italic`: 如果当前字体的斜体版本可用，那么文本设置为斜体版本；如果不可用，那么会利用 oblique 状态来模拟 italics。
  - `oblique`: 将文本设置为斜体字体的模拟版本，也就是将普通文本倾斜的样式应用到文本中。

- `font-weight`: 设置文字的粗体大小。这里有很多值可选 (比如 *-light*, *-normal*, *-bold*, *-extrabold*, *-black*, 等等), 不过事实上你很少会用到 `normal` 和 `bold`以外的值：
  
  - `normal`, `bold`: 普通或者**加粗**的字体粗细
  - `lighter`, `bolder`: 将当前元素的粗体设置为比其父元素粗体更细或更粗一步。`100`–`900`: 数值粗体值，如果需要，可提供比上述关键字更精细的粒度控制。

- `text-transform`: 允许你设置要转换的字体。值包括：
  
  - `none`: 防止任何转型。
  - `uppercase`: 将所有文本转为大写。
  - `lowercase`: 将所有文本转为小写。
  - `capitalize`: 转换所有单词让其首字母大写。
  - `full-width`: 将所有字形转换成全角，即固定宽度的正方形，类似于等宽字体，允许拉丁字符和亚洲语言字形（如中文，日文，韩文）对齐。

- `text-decoration`: 设置/取消字体上的文本装饰 可用值为：
  
  - `none`: 取消已经存在的任何文本装饰。
  
  - `underline`: <u>文本下划线</u>.
  
  - `overline`: 文本上划线
  
  - `line-through`: 穿过文本的线 ~~strikethrough over the text~~.
    
    ---
  
  ### 文字阴影
  
  使用 `text-shadow`属性。最多需要 4 个值，如下例所示：
  
  ```css
  text-shadow: 4px 4px 5px red;
  ```
  
  4 个属性如下:
  
  1. 阴影与原始文本的水平偏移，可以使用大多数的 CSS 单位 , 但是 px 是比较合适的。这个值必须指定。
  2. 阴影与原始文本的垂直偏移;效果基本上就像水平偏移，除了它向上/向下移动阴影，而不是左/右。这个值必须指定。
  3. 模糊半径 - 更高的值意味着阴影分散得更广泛。如果不包含此值，则默认为0，这意味着没有模糊。可以使用大多数的 CSS 单位.
  4. 阴影的基础颜色，可以使用大多数的 CSS 颜色单位 . 如果没有指定，默认为 `black`

#### 多种阴影

您可以通过包含以逗号分隔的多个阴影值，将多个阴影应用于同一文本，例如：

```css
text-shadow: -1px -1px 1px #aaa,
             0px 4px 1px rgba(0,0,0,0.5),
             4px 4px 5px rgba(0,0,0,0.7),
             0px 0px 7px rgba(0,0,0,0.4);
```

---

## 文本布局

### 文本对齐

 `text-align` 属性用来控制文本如何和它所在的内容盒子对齐。可用值如下，并且在与常规文字处理器应用程序中的工作方式几乎相同：

- `left`: 左对齐文本。

- `right`: 右对齐文本。

- `center`: 居中文字

- `justify`: 使文本展开，改变单词之间的差距，使所有文本行的宽度相同。

### 行高

 `line-height` 属性设置文本每行之间的高，可以接受大多数单位 `length and size units`

可以设置一个**无单位的值**，作为乘数，通常这种是比较好的做法。

无单位的值乘以 font-size 来获得 line-height。当行与行之间拉开空间，正文文本通常看起来更好更容易阅读。推荐的行高大约是 1.5–2 (双倍间距。) 

```css
line-height: 1.5;
```

### 字母及单词间距

`letter-spacing` 和 `word-spacing` 属性允许设置文本中的字母与字母之间的间距、或是单词与单词之间的间距。

```css
/*将该效果设置在第一行*/
p::first-line {
  letter-spacing: 2px;
  word-spacing: 4px;
}
```

---

## 其他属性

### Font 样式:

- font-variant: 在小型大写字母和普通文本选项之间切换。

- font-kerning: 开启或关闭字体间距选项。

- font-feature-settings: 开启或关闭不同的 OpenType 字体特性。

- font-variant-alternates: 控制给定的自定义字体的替代字形的使用。

- font-variant-caps: 控制大写字母替代字形的使用。

- font-variant-east-asian (en-US): 控制东亚文字替代字形的使用, 像日语和汉语。

- font-variant-ligatures: 控制文本中使用的连写和上下文形式。

- font-variant-numeric: 控制数字，分式和序标的替代字形的使用。

- font-variant-position: 控制位于上标或下标处，字号更小的替代字形的使用。

- font-size-adjust: 独立于字体的实际大小尺寸，调整其可视大小尺寸。

- font-stretch: 在给定字体的可选拉伸版本中切换。

- text-underline-position: 指定下划线的排版位置，通过使用 text-decoration-line 属

- 的underline 值。

- text-rendering: 尝试执行一些文本渲染优化。

### 文本布局样式：

- text-indent: 指定文本内容的第一行前面应该留出多少的水平空间。

- text-overflow: 定义如何向用户表示存在被隐藏的溢出内容。

- white-space: 定义如何处理元素内部的空白和换行。

- word-break: 指定是否能在单词内部换行。

- direction: 定义文本的方向 (这取决于语言，并且通常最好让HTML来处理这部分，因为它是和文本内容相关联的。)

- hyphens: 为支持的语言开启或关闭连字符。

- line-break: 对东亚语言采用更强或更弱的换行规则。

- text-align-last: 定义一个块或行的最后一行，恰好位于一个强制换行前时，如何对齐。

- text-orientation: 定义行内文本的方向。

- word-wrap: 指定浏览器是否可以在单词内换行以避免超出范围。

- writing-mode: 定义文本行布局为水平还是垂直，以及后继文本流的方向。

## Font简写

许多字体的属性也可以通过 font 的简写方式来设置 . 这些是按照以下顺序来写的： ` font-style`, `font-variant`, `font-weight`, `font-stretch`, `font-size`, `line-height`, and `font-family`.

如果你想要使用 `font` 的简写形式，在所有这些属性中，只有 `font-size` 和 `font-family` 是一定要指定的。

`font-size` 和 `line-height` 属性之间必须放一个正斜杠。

一个完整的例子如下所示：

```css
font: italic normal bold normal 3em/1.5 Helvetica, Arial, sans-serif;
```
