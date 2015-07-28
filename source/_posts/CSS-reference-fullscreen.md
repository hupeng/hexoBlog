title: :fullscreen | CSS reference
date: 2015-07-28 19:25:12
description: CSS参考 :fullscreen
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/fullscreen/](http://tympanus.net/codrops/css_reference/fullscreen/)

###`:fullscreen`是一种CSS伪类选择器，用于选择那些在全屏模式下显示的元素，并设定样式。

大部分的浏览器都有进入全屏或者kiosk模式的能力，并持续一段时间。本质上来说，浏览器的GUI不再控制，内容开始接管。在那种情况下，整个页面都处在全屏模式中，你可以在页面激活的时候，按下F11观看效果。

但是，如果用`:fullscreen`伪类选择器选择页面上的某个元素，将不能匹配。如果想要元素匹配到`:fullscreen`，必须使用HTML5的[全屏API](https://dvcs.w3.org/hg/fullscreen/raw-file/tip/Overview.html)进入全屏模式。

<!--more-->

全屏API超出本片文章的范围，所以我不会详细的介绍如何使用它。但是这里有一个简单的代码片段，介绍如何让一个元素进入全屏模式：

```javascript
var el = document.getElementByID('element');

// use necessary prefixed versions
el.webkitRequestFullscreen();
el.mozRequestFullScreen();
el.msRequestFullscreen();

// finally the standard version
el.requestFullscreen();
```

上面例子中的`el`现在就能匹配`:fullscreen`选择器了，并能够在那个模式中设定样式：

```css
#element:fullscreen {
    width: 100vw;
    height: 100vh;
    /* etc.. */
}
```

全屏模式中的内容通常是由浏览器的视口（viewport）生成的。使用`:fullscreen`，你可以对那些处在全屏模式中的元素定义任何你想要的样式。大部分时间，你会想要元素扩展到填充整个视口的大小。参考下面的案例和在线演示。

###备注

W3C标准使用没有短线的语法：`:fullscreen`。但是基于webkit内核的浏览器实现了一个前缀和试验性的变体，将`full`和`screen`用短线分开：`:-webkit-full-screen`。类似的，Firefox使用一个`-moz-`前缀，也包含一个短线：`:-moz-full-screen`。所以在最初使用`:fullscreen`选择器的时候，你需要包含这两种语法和各自的前缀。参考下面的浏览器兼容性。

###案例

下面的例子为一个全屏模式中的元素设定样式，以便于能够填充整个视口尺寸：

```css
.el:-webkit-full-screen {
  width: 100vw;
  height: 100vh;
}

.el:-moz-full-screen {
  width: 100vw;
  height: 100vh;
}

.el:-ms-fullscreen {
  width: 100vw;
  height: 100vh;
}

.el:fullscreen {
  width: 100vw;
  height: 100vh;
}
```

下面的例子会隐藏图片的标题，当其进入全屏模式时候：

```css
figure:-webkit-full-screen figcaption {
  display: none;
}

figure:-moz-full-screen figcaption {
  display: none;
}

figure:-ms-fullscreen figcaption {
  display: none;
}

figure:fullscreen figcaption {
  display: none;
}
```

下面的例子会在全屏模式激活时候，隐藏所有具有类名为`footnotes`的元素：

```css
:-webkit-full-screen .footnotes {
  display: none;
}

:-moz-full-screen .footnotes {
  display: none;
}

:-ms-fullscreen .footnotes {
  display: none;
}

:fullscreen .footnotes {
  display: none;
}
```

###在线演示

下面例子中的蓝色盒子宽度被设定为100%。当它处在正常的屏幕模式时候，它会占据其容器的全部宽度。当它匹配`:fullscreen`时候，背景色会变成另外一种颜色，并且会被扩展到填充整个视口的高度和宽度。

试着按下F11或者例子当中的那个按钮进入全屏模式。使用F11，整个页面都会进入全屏模式，不仅仅那个元素自己，那么那个元素的样式就不会改变。点击按钮将使元素自身进入全屏模式，定义的样式就会生效。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/MMY4EHxc/embed/result,html,css/" width="100%" height="600px"></iframe>

###浏览器兼容性

`:fullscreen`伪类选择器在Chrome中是：`:-webkit-full-screen`，在Firefox中是`:-moz-full-screen`，在 Opera 和 Safari 是：`:-webkit-full-screen`，以及在 Internet Explorer 11+ 中是：`:-ms-fullscreen`。

下面的表格中列出了全屏API的支持详情：

<iframe src="http://caniuse.com/fullscreen/embed/" width="100%" height="350px"></iframe>

###深度阅读

* [Fullscreen Specification (Living Standard)](https://dvcs.w3.org/hg/fullscreen/raw-file/tip/Overview.html#selectors-%28:fullscreen-and-:fullscreen-ancestor%29)

###相关文章

* :target
* :scope
