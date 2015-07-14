title: :disabled | CSS reference
date: 2015-07-14 21:24:02
description: CSS参考 :disabled
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/disabled/](http://tympanus.net/codrops/css_reference/disabled/)

###`:disabled`是一种伪类选择器，用于匹配那些被禁用的用户界面元素（通常是一些表单元素），并为其设置样式。

也就是说，它会匹配那些被设置过`disabled`属性的元素，例如按钮（`<button>`），选择菜单（`<select>`），输入框（`<input>`），以及文本域（`<textarea>`），尽管那些元素不能和用户交互。

```html
<input type="submit" disabled> <!-- disabled attribute added as a boolean value -->
<!-- OR -->
<input type="submit" disabled="disabled"> <!-- disabled attribute added with a "disabled" value -->
```

<!--more-->

`disabled`属性是一个HTML5属性，可以在这些元素上使用：`<button>`, `<input>`, `<textarea>`, `<optgroup>`, `<option>`, 和 `<fieldset>`。当禁用这些元素的时候，用户交互如点击，文本输入，或者获取焦点都不起作用。

###备注

禁用的元素也有一个对应的激活状态，处在激活状态的元素可以使用`:enabled`伪类来设定样式。

CSS属性可能会影响用户同给与的用户界面元素之间的交互能力，但是这并不妨碍他们匹配`:enabled`或者`:disabled`。例如，`display`和`visibility`属性并不会影响到元素的激活/禁用状态，尽管他们在文档中被隐藏了。

同其他伪类选择器一样，`:disabled`选择器也可以在其他选择器后面链式使用，如`:hover`，例如，给禁用元素添加悬浮效果。参考下面的例子和在线演示。

###案例

```css
/* styles all disabled elements on a page */
:disabled {
    background-color: #aaa;
    color: grey;
    border: 1px solid grey;
}

/* styles disabled submit inputs on a page */
input[type="submit"]:disabled {
    background: #eee url(path/to/disabled.png) repeat-x;
    border: 1px solid grey;
}
```

下面的例子链式使用`:disabled`和`:hover`伪类选择器，当禁用按钮处在悬浮状态时候，改变指针样式，显示`Not Allow`标记。

```css
button:disabled:hover {
    cursor: not-allowed;
}
```

###在线演示

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/Z0o15MdN/embed/result,html,css/" width="100%" height="300px"></iframe>

###浏览器兼容性

支持`:disabled`伪类的浏览器有：Chrome, Firefox, safari, Opera 9+, Internet Explorer 9+, 以及 Android 和 iOS。

###深度阅读

* [CSS Selectors Level 3](http://dev.w3.org/csswg/selectors3/#enableddisabled)
* [Styling Disabled Form Controls With CSS](http://www.456bereastreet.com/lab/styling-form-controls-revisited/disabled/)

###相关文章

* :read-only
* :checked
* :enabled
* :focus
* :indeterminate
* :required
* :optional

