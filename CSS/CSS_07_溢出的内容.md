# 溢出控制

`overflow`属性是你控制一个元素溢出的方式，它告诉浏览器你想怎样处理溢出。`overflow`的默认值为`visible`，这就是我们的内容溢出的时候，我们在默认情况下看到它们的原因。

## overflow: hidden

溢出时隐藏内容

## overflow:scroll

总会显示滚动条，即使没有足够多引起溢出的内容

可以使用`overflow-y`属性，设置`overflow-y: scroll`来仅在y轴方向滚动

仅显示垂直方向的滚动条

同理，也可以用`overflow-x`，以在x轴方向上滚动

## overflow: auto

使用`overflow: auto`。此时由浏览器决定是否显示滚动条。

**这种方式可以在没有内容溢出的时候隐藏滚动条**

---

CSS中有所谓**块级排版上下文Block Formatting Context，BFC**的概念

在使用诸如`scroll`或者`auto`的时候，就建立了一个块级排版上下文

改变了`overflow`的值的话，对应的盒子就变成了更加小巧的状态

在容器之外的东西没法混进容器内，也没有东西可以突出盒子，进入周围的版面
