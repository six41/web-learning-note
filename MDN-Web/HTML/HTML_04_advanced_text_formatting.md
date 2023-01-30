# HTML Advanced text formatting

## 描述列表

描述列表使用与其他列表类型不同的闭合标签— &lt;dl&gt;; 此外，每一项都用 &lt;dt&gt; (description term) 元素闭合。每个描述都用 &lt;dd&lt; (description definition) 元素闭合。

```HTML
<dl>
  <dt>内心独白</dt>
    <dd>戏剧中，某个角色对自己的内心活动或感受进行念白表演，这些台词只面向观众，而其他角色不会听到。</dd>
  <dt>语言独白</dt>
    <dd>戏剧中，某个角色把自己的想法直接进行念白表演，观众和其他角色都可以听到。</dd>
  <dt>旁白</dt>
    <dd>戏剧中，为渲染幽默或戏剧性效果而进行的场景之外的补充注释念白，只面向观众，内容一般都是角色的感受、想法、以及一些背景信息等。</dd>
</dl>
```

浏览器的默认样式会在描述列表的描述部分（description definition）和描述术语（description terms）之间产生缩进。

## 块引用

如果一个块级内容（一个段落、多个段落、一个列表等）从其他地方被引用，你应该把它用&lt;blockquote&gt;元素包裹起来表示，并且在cite属性里用URL来指向引用的资源。

```HTML
<blockquote cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote">
  <p>The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or <em>HTML Block
  Quotation Element</em>) indicates that the enclosed text is an extended quotation.</p>
</blockquote>
```

>The **HTML `<blockquote>` Element** (or *HTML Block Quotation Element*) indicates that the enclosed text is an extended quotation.

## 行内引用

行内元素用同样的方式工作，除了使用<q>元素。

```HTML
<p>The quote element — <code>&lt;q&gt;</code> — is <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">intended
for short quotations that don't require paragraph breaks.</q></p>
```

The quote element — `<q>` — is intended for short quotations that don't require paragraph breaks.

&lt;q&gt;元素旨在用于不需要分段的短引用.

## 缩略语

另一个你在web上看到的相当常见的元素是&lt;abbr&gt;——它常被用来包裹一个缩略语或缩写，并且提供缩写的解释（包含在title属性中）。

```HTML
<p>我们使用 <abbr title="超文本标记语言（Hyper text Markup Language）">HTML</abbr> 来组织网页文档。</p>
```

文本显示如下（实际网页中 鼠标移动至HTML上会有提示）

我们使用 HTML 来组织网页文档。

## 标记联系方式

```HTML
<address>
  <a href="mailto:jim@rock.com">jim@rock.com</a><br>
  <a href="tel:+13115552368">(311) 555-2368</a>
</address>
```

## 上标和下标

当你使用日期、化学方程式、和数学方程式时会偶尔使用上标和下标。 &lt;sup&gt; 和&lt;sub&gt;元素可以解决这样的问题。

## 标记时间和日期

HTML 还支持将时间和日期标记为可供机器识别的格式的 &lt;time&gt; 元素。

```HTML
<!-- 标准简单日期 -->
<time datetime="2016-01-20">20 January 2016</time>
<!-- 只包含年份和月份-->
<time datetime="2016-01">January 2016</time>
<!-- 只包含月份和日期 -->
<time datetime="01-20">20 January</time>
<!-- 只包含时间，小时和分钟数 -->
<time datetime="19:30">19:30</time>
<!-- 还可包含秒和毫秒 -->
<time datetime="19:30:01.856">19:30:01.856</time>
<!-- 日期和时间 -->
<time datetime="2016-01-20T19:30">7.30pm, 20 January 2016</time>
<!-- 含有时区偏移值的日期时间 -->
<time datetime="2016-01-20T19:30+01:00">7.30pm, 20 January 2016 is 8.30pm in France</time>
<!-- 调用特定的周 -->
<time datetime="2016-W04">The fourth week of 2016</time>
```

