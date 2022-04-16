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

哪些属性属于默认继承很大程度上是由常识决定的。

## 控制继承

CSS 为控制继承提供了四个特殊的通用属性值。每个css属性都接收这些值。

#### inherit

设置该属性会使子元素属性和父元素相同。实际上，就是 "开启继承".

#### initial

设置属性值和浏览器默认样式相同。如果浏览器默认样式中未设置且该属性是自然继承的，那么会设置为 inherit 。

#### unset

将属性重置为自然值，也就是如果属性是自然继承那么就是 inherit，否则和 initial一样 。

## 重设所有属性值

CSS 的 shorthand 属性 all 可以用于同时将这些继承值中的一个应用于（几乎）所有属性。

```CSS
blockquote {
    background-color: red;
    border: 2px solid green;
}
        
.fix-this {
    all: unset;
}
```

## 层叠

层叠如何定义在不止一个元素的时候应用css规则

有三个因素需要考虑

1. 重要程度
2. 优先级
3. 资源顺序

### 资源顺序

有超过一条规则，而且都是相同的权重，那么最后面的规则会应用。

### 优先级

比如，类选择器的权重大于元素选择器，因此类上定义的属性将覆盖应用于元素上的属性。

#### 计算方式

- 千位： 如果声明在 style 的属性（内联样式）则该位得一分。这样的声明没有选择器，所以它得分总是1000。
- 百位： 选择器中包含ID选择器则该位得一分。
- 十位： 选择器中包含类选择器、属性选择器或者伪类则该位得一分。
- 个位：选择器中包含元素、伪元素选择器则该位得一分。


<table>
<tr>
<td>选择器</td>
<td>千位</td>
<td>百位</td>
<td>十位</td>
<td>个位</td>
<td>优先级</td>
</tr>
<tr>
<td>h1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0001</td>
</tr>
<tr>
<td>h1 + p::first-letter</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>3</td>
<td>0003</td>
</tr>
<tr>
<td>li > a[href*="en-US"] > .inline-warning</td>
<td>0</td>
<td>0</td>
<td>2</td>
<td>2</td>
<td>0022</td>
</tr>
<tr>
<td>#identifier</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0100</td>
</tr>
<tr>
<td>内联样式</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1000</td>
</tr>
</table>
### CSS位置的影响

相互冲突的声明将按以下顺序适用，后一种声明将覆盖前一种声明：

1. 用户代理样式表中的声明(例如，浏览器的默认样式，在没有设置其他样式时使用)。
2. 用户样式表中的常规声明(由用户设置的自定义样式)。
3. 作者样式表中的常规声明(这些是我们web开发人员设置的样式)。
4. 作者样式表中的`!important`声明
5. 用户样式表中的`!important` 声明

