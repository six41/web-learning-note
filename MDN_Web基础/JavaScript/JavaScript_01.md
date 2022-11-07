# JavaScript

浏览器执行到一段 JavaScript 代码时，通常会按**从上往下**的顺序执行这段代码。

```javascript
const para = document.querySelector('p');

para.addEventListener('click', updateName);

function updateName() {
  let name = prompt('输入一个新的名字：');
  para.textContent = '玩家 1：' + name;
}
```

**代码说明**
 
选定一个文本段落（第 1 行)，然后给它附上一个事件监听器（第 3 行），使得在它被点击时，`updateName()` 代码块（code block） （5 – 8 行）便会运行。`updateName()` （这类可以重复使用的代码块称为“函数”）向用户请求一个新名字，然后把这个名字插入到段落中以更新显示。

## 服务器端代码 vs 客户端代码

你或许还听说过**服务器端（server-side）**和 客户端（client-side）代码这两个术语，尤其是在 web 开发时。客户端代码是在用户的电脑上运行的代码，在浏览一个网页时，它的客户端代码就会被下载，然后由浏览器来运行并展示。这就是客户端`JavaScript`。

而服务器端代码在服务器上运行，接着运行结果才由浏览器下载并展示出来。流行的服务器端 web 语言包括：PHP、Python、Ruby、ASP.NET 以及...... JavaScript！JavaScript 也可用作服务器端语言，比如现在流行的 Node.js 环境.

### async “异步”属性

它告知浏览器在遇到 `script` 元素时不要中断后续 HTML 内容的加载。

## async 和 defer

上述的脚本阻塞问题实际有两种解决方案 —— async 和 defer。我们来依次讲解。

浏览器遇到 async 脚本时不会阻塞页面渲染，而是直接下载然后运行。这样脚本的运行次序就无法控制，只是脚本不会阻止剩余页面的显示。当页面的脚本之间彼此独立，且不依赖于本页面的其它任何脚本时，async 是最理想的选择。

比如，如果你的页面要加载以下三个脚本：


```javascript
<script async src="js/vendor/jquery.js"></script>

<script async src="js/script2.js"></script>

<script async src="js/script3.js"></script>
```

三者的调用顺序是不确定的。jquery.js 可能在 script2 和 script3 之前或之后调用，如果这样，后两个脚本中依赖 jquery 的函数将产生错误，因为脚本运行时 jquery 尚未加载。

解决这一问题可使用 defer 属性，脚本将按照在页面中出现的顺序加载和运行：

```javascript
<script defer src="js/vendor/jquery.js"></script>

<script defer src="js/script2.js"></script>

<script defer src="js/script3.js"></script>
```

添加 defer 属性的脚本将按照在页面中出现的顺序加载，因此第二个示例可确保 jquery.js 必定加载于 script2.js 和 script3.js 之前，同时 script2.js 必定加载于 script3.js 之前。

## 脚本调用总结

- 如果脚本无需等待页面解析，且无依赖独立运行，那么应使用 async。
- 如果脚本需要等待页面解析，且依赖于其它脚本，调用这些脚本时应使用 defer，将关联的脚本按所需顺序置于 HTML 中。

```javascript
// 函数：创建一个新的段落并添加至 HTML body 底部。
function createParagraph() {
  let para = document.createElement('p');
  para.textContent = '你点了这个按钮！';
  document.body.appendChild(para);
}

/*
  1. 取得页面上所有按钮的引用并将它们置于一个数组中。
  2. 通过一个循环为每个按钮添加一个点击事件的监听器。
  当按钮被点击时，调用 createParagraph() 函数。
*/

const buttons = document.querySelectorAll('button');

for (let i = 0; i < buttons.length; i++) {
  buttons[i].addEventListener('click', createParagraph);
}
```