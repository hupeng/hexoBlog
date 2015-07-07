title: CSS reference—— ::placeholder
date: 2015-07-07 20:43:34
description: CSS参考 ::placeholder
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/placeholder/](http://tympanus.net/codrops/css_reference/placeholder/)

###`::placeholder`是一种CSS伪元素，用来表示input表单中的占位符文本，所谓占位符，就是出现在输入框中，暗示用户如何填充这个表单的文字。

例如，一个日期输入框可能会有这样的占位符：`YYYY/MM/DD`，用来申明将会以年-月-日的顺序输入数字日期。需要邮箱作为值的输入框可能会有这样的占位符：`john@doe.com`，暗示邮箱格式。

在大部分的浏览器中，占位符会被初始化为浅灰色。可以改变他们的颜色和样式，例如，使用`::placeholder`伪元素。

<!--more-->

###备注

能够用在`::first-line`上的属性，也可以用在`::placeholder`上。

关于`::placeholder`伪元素，一些浏览器会有他们自身一些非标准的实现，这些实现都需要一些浏览器前缀。例如：`::-webkit-input-placeholder`，`:-ms-input-placeholder`（一个冒号），以及`:-moz-placeholder`（在Firefox 19，已经被废除了，更新的版本采用`::-moz-placeholder`）。

当文本框获得焦点的时候，文本框占位符可能可见，也可能消失，这基于不同的浏览器。例如，IE10+会在文本框获取焦点的时候隐藏占位符，就算它是空的。

###案例

下面的代码片段改变页面中占位符文本默认的颜色和字体族：

```css
::placeholder {
    color: #96eb7f;
    font-family: Lato, sans-serif;
}
```

###在线演示

看下面的示例：

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/NZYjmfdZ/embed/result,html,css/" width="100%" height="300px"></iframe>

###浏览器兼容性

<iframe src="http://caniuse.com/input-placeholder/embed/" width="100%" height="350px"></iframe>

###深度阅读

* [CSS 伪元素模型 LV4](http://www.w3.org/TR/css-pseudo-4/#placeholder-pseudo)
* David Walsh：[用CSS定义HTML5占位符的样式](http://davidwalsh.name/html5-placeholder-css)
* 推荐：Zach Leatherman写的[关于HTML5占位符的文章占位标题](http://www.zachleat.com/web/placeholder/)

###相关文章

* [::first-letter](http://lesrecord.com/2015/07/04/CSS-reference-first-letter/)
* attr()
* [::before](http://lesrecord.com/2015/07/03/CSS-reference-before/)
* [::after](http://lesrecord.com/2015/07/02/CSS-reference-after/)