# HTML hyperlinks

```HTML
<p>我创建了一个指向
<a href="https://github.com/six41"
   title="six41的Github主页">我的代码仓库</a>
的超链接。
</p>
```

## 块级链接

可以将一些内容转换为链接，甚至是块级元素。

```HTML
<a href="https://www.mozilla.org/zh-CN/">
  <img src="mozilla-image.png" alt="链接至 Mozilla 主页的 Mozilla 标志">
</a>
```

## 链接到HTML文档片段

首先给要链接到的元素分配一个id属性,例如想要连接到标题h2

```HTML
<h2 id="Mailing_address">邮寄地址</h2>
```

然后链接到那个特定的id，可以在URL的结尾使用一个井号指向它，例如：

```HTML
<p>要提供意见和建议，请将信件邮寄至 <a href="contacts.html#Mailing_address">我们的地址</a>。</p>
```

甚至可以在同一份文档下，通过链接文档片段，来链接到同一份文档的另一部分：

```HTML
<p>本页面底部可以找到 <a href="#Mailing_address">公司邮寄地址</a>。</p>
```

## 统一资源定位符 Uniform Resource Locator

URL使用路径查找文件。路径指定文件系统中您感兴趣的文件所在的位置。

### 绝对URL

指向由其在Web上的绝对位置定义的位置，包括 protocol（协议） 和 domain name（域名）。

不管绝对URL在哪里使用，它总是指向确定的相同位置。

### 相对URL

指向与您链接的文件相关的位置。

- 指向当前目录
- 指向子目录
- 指向上级目录

当链接到同一网站的其他位置时，应该使用相对链接（当链接到另一个网站时，你需要使用绝对链接）

- 首先，检查代码要容易得多——相对URL通常比绝对URL短得多，这使得阅读代码更容易。
- 其次，在可能的情况下使用相对URL更有效。当使用绝对URL时，浏览器首先通过DNS查找服务器的真实位置，然后再转到该服务器并查找所请求的文件。另一方面，相对URL，浏览器只在同一服务器上查找被请求的文件。因此，如果使用绝对URL而不是相对URL，就会不断地让浏览器做额外的工作，这意味着它的效率会降低。
