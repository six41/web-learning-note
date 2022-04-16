# 处理不同方向文本

## 书写模式

CSS中的书写模式是指文本的排列方向是横向还是纵向的。[`writing-mode`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/writing-mode) 属性使我们从一种模式切换到另一种模式。

writing-mode的三个值分别是：

- `horizontal-tb`: 块流向从上至下。对应的文本方向是横向的。
- `vertical-rl`: 块流向从右向左。对应的文本方向是纵向的。
- `vertical-lr`: 块流向从左向右。对应的文本方向是纵向的。

当我们切换书写模式时，我们也在改变块和内联文本的方向。`horizontal-tb`书写模式下块的方向是从上到下的横向的，而 `vertical-rl`书写模式下块的方向是从右到左的纵向的。

> 块维度指的总是块在页面书写模式下的显示方向。而内联维度指的总是文本方向。

这张图展示了在水平书写模式下的两种维度。

![](https://mdn.mozillademos.org/files/17148/horizontal-tb-zh.png)

这张图片展示了纵向书写模式下的两种维度。

![](https://mdn.mozillademos.org/files/17149/vertical-zh.png)

## 逻辑属性和逻辑值

这些属性用逻辑（**logical**）和相对变化（**flow relative**）代替了像宽`width`和高`height`一样的物理属性。

横向书写模式下，映射到width的属性被称作内联尺寸（inline-size）——内联维度的尺寸。而映射height的属性被称为块级尺寸（block-size），这是块级维度的尺寸。

## 逻辑外边距、边框和内边距属性

margin-top属性的映射是margin-block-start——总是指向块级维度开始处的边距。

padding-left属性映射到 padding-inline-start，这是应用到内联开始方向（这是该书写模式文本开始的地方）上的内边距。

border-bottom属性映射到的是border-block-end，也就是块级维度结尾处的边框。

对于每一个普通边距，都有许多属性可以参考.

[CSS Logical Properties and Values - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties)

## 逻辑值

目前为止我们看到的都是逻辑属性的名称。还有一些属性的取值是一些物理值（如`top`、`right`、`bottom`和`left`）。这些值同样拥有逻辑值映射（`block-start`、`inline-end`、`block-end`和`inline-start`）。
