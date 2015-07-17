title: :enabled | CSS reference
date: 2015-07-17 21:31:52
description: CSS参考 :enabled
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/enabled/](http://tympanus.net/codrops/css_reference/enabled/)

###`:enabled`是一种伪类选择器，用于选择那些处于激活状态的用户界面元素（通常是表单元素），并设定他们的样式。

也就是说，它是用来匹配那些能够接受用户交互行为，如点击，文本输入，或者获取焦点，的元素，包括按钮（`<button>`），选择菜单（`<select>`），输入框（`<input>`），以及文本域（`<textarea>`）。

<!--more-->

###备注

激活的元素也有一个对应的禁用状态，使用`:disabled`伪类可以设置禁用状态的样式。`:enabled`只能让我们选择那些处于激活状态的用户界面元素，因此禁用的那些会被排除掉。

CSS属性可能会影响用户同给与的用户界面元素之间的交互能力，但是这并不妨碍他们匹配`:enabled`或者`:disabled`。例如，`display`和`visibility`属性并不会影响到元素的激活/禁用状态，尽管他们在文档中被隐藏了。

同其他伪类选择器一样，`:disabled`选择器也可以在其他选择器后面链式使用，如`:hover`。

###案例

```css
/* styles all enabled elements on a page */
:enabled {
    background-color: white;
    color: green;
    border: 1px solid black;
}

/* styles enabled submit inputs on a page */
input[type="submit"]:enabled {
    border: 1px solid green;
}
```

下面的例子链式调用`:enabled`和`:hover`选择器。

```css
button:enabled:hover {
    background-color: green;
    color: white;
}
```

###在线演示

下面例子使用`:enabled`来设置激活状态的表单元素样式，你可以在这个案例中看到禁用状态的元素没有被选择及设定样式，可以使用`:disabled`来代替。如果你的浏览器支持`:enabled`，激活状态元素的文字是绿色的，当悬停在文本域上时候，背景色会变成绿色。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/ZxpA9v3H/embed/result,html,css/" width="100%" height="300px"></iframe>

###浏览器兼容性

支持`:enabled`伪类的有：Chrome, Firefox, safari, Opera 9+, Internet Explorer 9+, 以及 Android 和 iOS。

###深度阅读

* [CSS Selectors Level 3](http://dev.w3.org/csswg/selectors3/#enableddisabled)

###相关文章

* :checked
* :default
* :disabled
* :indeterminate
