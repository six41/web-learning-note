# CSS构建 层叠与继承

CSS代表层叠样式表(Cascading Style Sheets)。

<em>cascade</em>, 和它密切相关的概念是 specificity，决定在发生冲突的时候应该使用哪条规则。

<strong>继承</strong>，些css属性继承当前元素的父元素上设置的值，有些则不继承。

## 层叠

Stylesheets cascade（样式表层叠） — 简单的说，css规则的顺序很重要；当应用两条同级别的规则到一个元素的时候，<strong>写在后面的就是实际使用的规则</strong>。

### 优先级

浏览器是根据优先级来决定当多个规则有不同选择器对应相同的元素的时候需要使用哪个规则。

- 一个元素选择器不是很具体 — 会选择页面上该类型的所有元素 — 所以它的优先级就会低一些。
- 一个类选择器稍微具体点 — 它会选择该页面中有特定 class 属性值的元素 — 所以它的优先级就要高一点。

```CSS
/*<h1 class="main-heading">This is my heading.</h1>*/
.main-heading { 
    color: red; 
}
        
h1 { 
    color: blue; 
}
```

此时浏览器会将颜色设置为红色，因为<strong>类选择器比元素选择器更加具体</strong>

## 继承

 一些设置在父元素上的css属性是可以被子元素继承的，有些则不能。

 如果你设置一个元素的 color 和 font-family ，每个在里面的元素也都会有相同的属性，除非你直接在元素上设置属性。

```CSS
/*body内除了span元素外都继承body的css属性，也就是颜色是蓝色*/
body {
    color: blue;
}

span {
    color: black;
}
```

#### 继承例子

下面的例子中有一个ul，里面有两个无序列表。我们已经给 &lt;ul&gt; 设置了 border， padding 和 font color.

color 应用在直接子元素，也影响其他后代。直接子元素&lt;li&gt;，和第一个嵌套列表中的子项。然后添加了一个 special 类到第二个嵌套列表，其中使用了不同的颜色。然后通过它的子元素继承。

#### html

```HTML
<ul class="main">
    <li>Item One</li>
    <li>Item Two
        <ul>
            <li>2.1</li>
            <li>2.2</li>
        </ul>
    </li>
    <li>Item Three
        <ul class="special">
            <li>3.1
                <ul>
                    <li>3.1.1</li>
                    <li>3.1.2</li>
                </ul>
            </li>
            <li>3.2</li>
        </ul>
    </li>
</ul>
```

#### CSS

```CSS
.main {
    color: rebeccapurple;
    border: 2px solid #ccc;
    padding: 1em;
}

.special {
    color: black;
    font-weight: bold;
}
```

## 控制继承

