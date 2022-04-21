# HTML Images

```HTML
<figure>
  <img src="https://raw.githubusercontent.com/mdn/learning-area/master/html/multimedia-and-embedding/images-in-html/dinosaur_small.jpg"
     alt="一只恐龙头部和躯干的骨架，它有一个巨大的头，长着锋利的牙齿。"
     width="400"
     height="341"
     title="A T-Rex on display in the Manchester University Museum">
  <figcaption>曼彻斯特大学博物馆展出的一只霸王龙的化石</figcaption>
</figure>
```

<img src="https://raw.githubusercontent.com/mdn/learning-area/master/html/multimedia-and-embedding/images-in-html/dinosaur_small.jpg"
     alt="一只恐龙头部和躯干的骨架，它有一个巨大的头，长着锋利的牙齿。"
     width="400"
     height="341"
     title="A T-Rex on display in the Manchester University Museum">

### alt 属性

对图片的文字描述，用于在图片无法显示或不能被看到的情况。

### title 属性

title属性会给一个鼠标悬停提示

## &lt;figure&gt;

&lt;figure&gt; 里不一定要是一张图片，只要是一个这样的独立内容单元：

- 用简洁、易懂的方式表达意图。
- 可以置于页面线性流的某处。
- 为主要内容提供重要的补充说明。

&lt;figcaption&gt; 元素告诉浏览器和其他辅助的技术工具这段说明文字描述了 &lt;figure&gt; 元素的内容.

> 从无障碍的角度来说，说明文字和 alt 文本扮演着不同的角色。看得见图片的人们同样可以受益于说明文字，而 alt 文字只有在图片无法显示时才这样。  