title: :focus | CSS reference
date: 2015-07-26 19:35:58
description: CSS参考 :focus
tags: CSS
---

> 原文链接：[http://tympanus.net/codrops/css_reference/focus/](http://tympanus.net/codrops/css_reference/focus/)

###`:focus`是一个伪类，用于选择那些获得用户焦点的元素——通常为链接和表单元素，并为其设置样式。可以通过键盘的“tab”键或者点击来获取焦点。

诸如`<input>`，`<button>`以及`<textarea>`的表单元素可以通过键盘“tab”键或者点击来接收焦点。输入框或者文本域在被点击，准备输入的时候拥有焦点。

当用户通过“tab”键遍历页面上的链接和表单元素时候，浏览器会为当前接收tab焦点的元素添加虚线外边框。浏览器添加的这些样式都是各自默认的，通常在不同的浏览器之间看起来不一样，所以你很有可能想覆盖那些默认样式，并用自己的取代他们。

<!--more-->

在默认的样式表中，浏览器使用`outline`属性为获得焦点的元素添加`:focus`样式。为了移除默认，添加自己的`:focus`样式，唯一需要做的就是为你想改变`:focus`样式的元素添加`outline: 0`；然后再添加自己的样式，例如：

```css
a:focus {
    outline: 0;
    /* then add your own styles here */
}
```

当你为链接设置`:focus`样式的时候，推荐在`:link`和`:visited`之后设置`:focus`样式，否则`:focus`样式就会被`:link`和`:visited`之中的覆盖。除了这三种伪类之外，`:hover`和`:active`伪类也被用于设置链接样式，并且在样式表中位于`:focus`之后。这些伪类出现的顺序最好是确保在需要的时候能够应用相应的伪类，并且不会被其他的伪类样式覆盖。

###备注

非常容易移除浏览器添加的默认`:focus`样式，但是出于访问性的目的，添加自己的`:focus`样式是非常重要的。

键盘访问是非常重要的，应该保留，因为很多用户更喜欢使用键盘在页面中导航，因此，应该总是[提供`:focus`样式](http://a11yproject.com/posts/never-remove-css-outlines/)。

###案例

下面的代码用背景和文本颜色代替了浏览器默认`:focus`边框样式，使链接在处于焦点状态时候更突出。

```css
a:link {
    color: #0099cc;
}

a:visited {
    color: grey;
}

a:focus {
    background-color: black;
    color: white;
}

a:hover {
    border-bottom: 1px solid #0099cc;
}

a:active {
    background-color: #0099cc;
    color: white;
}
```

下面的代码片段会把焦点状态的输入框和文本域背景设置为亮黄色，边框为浅红色。

```css
input:focus, textarea:focus {
    background-color: #FFFF66;
    border: 1px solid #F47E58;
}
```

###在线演示

在下面的示例中使用键盘的“tab”键，或者点击输入框和文本域，使他们获得焦点，然后查看`:focus`样式。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/axvfKiBK/embed/result,html,css/" width="100%" height="500px"></iframe>

###浏览器兼容性

所有主流的浏览器都支持`:focus`伪类：Chrome, Firefox, Safari, Opera 7+, Internet Explorer 7+, 以及 Android 和 iOS。

###深度阅读

* [CSS Selectors Module](http://www.w3.org/TR/CSS2/selector.html#dynamic-pseudo-classes)

###相关文章

* :hover
* :disabled
* :active
* :visited