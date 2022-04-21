# CSS选择器

当使用选择器列表时，如果任何一个选择器无效 (存在语法错误)，那么整条规则都会被忽略。

```CSS
h1 {
  color: blue;
}

..special {
  color: blue;
} 
```

无效的class选择器会被忽略，而h1选择器仍会被样式化。

### 选择器类型

#### 元素选择器

```css
h1 { }
```

#### 类选择器

```css
.box { }
```

#### ID选择器

```css
#unique { }
```

#### 标签属性选择器

这组选择器根据一个元素上的某个标签的属性的存在以选择元素的不同方式：

```css
a[title] { }
```

或者根据一个有特定值的标签属性是否存在来选择：

```css
a[href="https://example.com"] { }
```

#### 伪类与伪元素

这组选择器包含了伪类，用来样式化一个元素的特定状态。例如:hover伪类会在鼠标指针悬浮到一个元素上的时候选择这个元素：

```CSS
a:hover { }
```

它还可以包含了伪元素，选择一个元素的某个部分而不是元素自己。例如，::first-line是会选择一个元素（下面的情况中是&lt;p&gt;）中的第一行，

```css
p::first-line { }
```

#### 运算符

最后一组选择器可以将其他选择器组合起来，更复杂的选择元素。下面的示例用运算符（`>`）选择了`<article>`元素的初代子元素。

```CSS
article > p { }
```

| 选择器                                                                                     | 示例                  | 学习CSS的教程                                                                                                                                                 |
|:--------------------------------------------------------------------------------------- |:------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [类型选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Type_selectors)                | `h1 { }`            | [类型选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#Type_selectors)                |
| [通配选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Universal_selectors)           | `* { }`             | [通配选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#The_universal_selector)        |
| [类选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Class_selectors)                | `.box { }`          | [类选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#Class_selectors)                |
| [ID选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/ID_selectors)                  | `#unique { }`       | [ID选择器](https://developer.mozilla.org/zh-CN/docs/user:chrisdavidmills/CSS_Learn/CSS_Selectors/Type_Class_and_ID_Selectors#ID_Selectors)                  |
| [标签属性选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Attribute_selectors)         | `a[title] { }`      | [标签属性选择器](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Attribute_selectors)                                     |
| [伪类选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-classes)                | `p:first-child { }` | [伪类](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Pseuso-classes_and_Pseudo-elements#What_is_a_pseudo-class)    |
| [伪元素选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Pseudo-elements)              | `p::first-line { }` | [伪元素](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Pseuso-classes_and_Pseudo-elements#What_is_a_pseudo-element) |
| [后代选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Descendant_combinator)         | `article p`         | [后代运算符](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Descendant_Selector)                           |
| [子代选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Child_combinator)              | `article > p`       | [子代选择器](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Child_combinator)                              |
| [相邻兄弟选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Adjacent_sibling_combinator) | `h1 + p`            | [相邻兄弟](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#Adjacent_sibling)                               |
| [通用兄弟选择器](https://developer.mozilla.org/zh-CN/docs/Web/CSS/General_sibling_combinator)  | `h1 ~ p`            | [通用兄弟](https://developer.mozilla.org/zh-CN/docs/User:chrisdavidmills/CSS_Learn/CSS_Selectors/Combinators#General_sibling)                                |
