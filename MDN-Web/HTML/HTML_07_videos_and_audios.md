# HTML Videos and Audios

## &lt;video&gt;

```HTML
<video src="rabbit320.webm" controls>
  <p>你的浏览器不支持 HTML5 视频。可点击<a href="rabbit320.mp4">此链接</a>观看</p>
</video>
```

### src

同 `<img>` 标签使用方式相同，src 属性指向你想要嵌入网页当中的视频资源，他们的使用方式完全相同。

### controls

用户必须能够控制视频和音频的回放功能。你可以使用 controls 来包含浏览器提供的控件界面。

### &lt;video&gt;标签内容

这个叫做后备内容 — 当浏览器不支持 `<video>` 标签的时候，就会显示这段内容，这使得我们能够对旧的浏览器提供回退内容。你可以添加任何后备内容，在这个例子中我们提供了一个指向这个视频文件的链接，从而使用户至少可以访问到这个文件，而不会局限于浏览器的支持。

## 浏览器支持

### Codecs

编解码器（从“coder-decoder”派生的混合词）是对数据流进行编码或解码的程序、算法或设备。给定的编解码器知道如何处理特定的编码或压缩技术。

---

浏览器包含了不同的 Codecs，如 Vorbis 和 H.264，它们用来将已压缩的音频和视频转化成二进制数字。

### video demo code

```HTML
<!--demo code-->
<video controls width="400" height="400"
       autoplay loop muted
       poster="poster.png">
  <source src="rabbit320.mp4" type="video/mp4">
  <source src="rabbit320.webm" type="video/webm">
  <p>你的浏览器不支持 HTML5 视频。可点击<a href="rabbit320.mp4">此链接</a>观看</p>
</video>
```

将 src 属性从 &lt;video&gt; 标签中移除，转而将它放在几个单独的标签 &lt;source&gt; 当中。

浏览器将会检查 <source> 标签，并且播放第一个与其自身 codec 相匹配的媒体。

### type属性

每个 &lt;source&gt; 标签页含有一个 type 属性，这个属性是可选的，但是建议你添加上这个属性 — 它包含了视频文件的 MIME types ，同时浏览器也会通过检查这个属性来迅速的跳过那些不支持的格式。

> **MIME type** （现在称为“媒体类型(media type)”，但有时也是“内容类型(content type)”）是指示文件类型的字符串，与文件一起发送（例如，一个声音文件可能被标记为 audio/ogg ，一个图像文件可能是 image/png ）。

### 一些特性

- width 和 height
  - 你可以用属性控制视频的尺寸，也可以用 CSS 来控制视频尺寸。 无论使用哪种方式，视频都会保持它原始的长宽比 — 也叫做纵横比。如果你设置的尺寸没有保持视频原始长宽比，那么视频边框将会拉伸，而未被视频内容填充的部分，将会显示默认的背景颜色。
- autoplay
  - 这个属性会使音频和视频内容立即播放，即使页面的其他部分还没有加载完全。建议不要应用这个属性在你的网站上，因为用户们会比较反感自动播放的媒体文件。
- loop
  - 这个属性可以让音频或者视频文件循环播放。同样不建议使用，除非有必要。
- muted
  - 这个属性会导致媒体播放时，默认关闭声音。
- poster
  - 这个属性指向了一个图像的URL，这个图像会在视频播放前显示。通常用于粗略的预览或者广告。
- preload
  - 这个属性被用来缓冲较大的文件，有3个值可选：
    - "none" ：不缓冲
    - "auto" ：页面加载后缓存媒体文件
    - "metadata" ：仅缓冲文件的元数据

## &lt;audio&gt;

### audio demo code

```HTML
<!--demo code-->
<audio controls>
  <source src="viper.mp3" type="audio/mp3">
  <source src="viper.ogg" type="audio/ogg">
  <p>你的浏览器不支持 HTML5 音频，可点击<a href="viper.mp3">此链接</a>收听。</p>
</audio>
```

- &lt;audio&gt; 标签不支持 width/height 属性 — 由于其并没有视觉部件，也就没有可以设置 width/height 的内容。

- 同时也不支持 poster 属性 — 同样，没有视觉部件。

### 重新播放媒体

```javascript
const mediaElem = document.getElementById("my-media-element");
mediaElem.load();
```

可以在Javascript中调用load()来重置媒体。有多个由&lt;source&gt;如果有多个由 <source> 标签指定的媒体来源，浏览器会从选择媒体来源开始重新加载媒体。

### 音轨增删事件

你可以监控媒体元素中的音频轨道，当音轨被添加或删除时，你可以通过监听相关事件来侦测到。具体来说，通过监听 AudioTrackList (en-US) 对象的 addtrack 事件（即 HTMLMediaElement.audioTracks 对象），你可以及时对音轨的增加做出响应。

```javascript
const mediaElem = document.querySelector("video");
mediaElem.audioTracks.onaddtrack = function(event) {
  audioTrackAdded(event.track);
}
```

### 显示音轨文本

WebVTT 是一个格式，用来编写文本文件，这个文本文件包含了众多的字符串，这些字符串会带有一些元数据，它们可以用来描述这个字符串将会在视频中显示的时间，甚至可以用来描述这些字符串的样式以及定位信息。这些字符串叫做 cues ，你可以根据不同的需求来显示不同的样式，最常见的如下：

#### subtitles

通过添加翻译字幕，来帮助那些听不懂外国语言的人们理解音频当中的内容。

#### captions

同步翻译对白，或是描述一些有重要信息的声音，来帮助那些不能听音频的人们理解音频中的内容。

#### timed descriptions

将文字转换为音频，用于服务那些有视觉障碍的人。

典型的 WebVTT 文件如下：

```WebVTT
WEBVTT

1
00:00:22.230 --> 00:00:24.606
第一段字幕

2
00:00:30.739 --> 00:00:34.074
第二段

  ...
```

> 在HTML媒体中显示WebVTT
> 1. 以 .vtt 后缀名保存文件。
> 2. 用 `<track>` 标签链接 .vtt 文件， `<track>` 标签需放在 `<audio>` 或 `<video>` 标签当中，同时需要放在所有 `<source>` 标签之后。使用 kind 属性来指明是哪一种类型，如 subtitles 、 captions 、 descriptions。然后，使用 srclang 来告诉浏览器你是用什么语言来编写的 subtitles。

```HTML
<video controls>
    <source src="example.mp4" type="video/mp4">
    <source src="example.webm" type="video/webm">
    <track kind="subtitles" src="subtitles_en.vtt" srclang="en">
</video>
```

