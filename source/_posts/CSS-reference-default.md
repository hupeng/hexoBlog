title: :default | CSS reference
date: 2015-07-12 21:11:55
description: CSS参考 :default
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/default/](http://tympanus.net/codrops/css_reference/default/)

###`:default`是一种伪类选择器，用于在一系列相同的UI元素中，选择那些处于默认状态的元素，并设定他们的样式。

这个选择器通常会被用于内容菜单项，按钮，以及选择列表。例如一系列按钮中的[默认提交按钮](http://www.w3.org/TR/html5/forms.html#default-button)。另一个例子是弹出菜单中的默认选项。在一个组合当中，可能有多个`:default`元素。

能够被`:default`匹配的元素也包括：已选择的多选框，设置了`checked`属性的单选框，以及设置了`selected`属性的选择菜单项。这些元素也会被`:checked`伪类所匹配。在`:checked`文章中获取更多关于选择和设置选择的输入框。

<!--more-->

###案例

```css
/* select and style default button  */
button:default {
    border: 1px dotted #009966;
}

/* select and style default submit input */
input[type="submit"]:default {
    color: green;
}

/* select and style default options in a select list, 
and the label for the default (checked) checkboxes */
input[type="checkbox"]:default + label {
    text-decoration: line-through;
}

option:default {
    background-color: black;
    color: white; 
}
```

###在线演示

下面的示例包含一个具有不同UI元素的表单：复选框，单选框，类型为`submit`的输入框，以及类型为`submit`的按钮。`:default`的复选框，他们的标签文字具有下划线。如果你的浏览器支持`:default`，那么你就能看到这种效果。

但是`type="submit"`的输入框和按钮被归于同一个组，因此，在支持的浏览器中，当中的第一个会是默认的，并且被设置为蓝色虚线边框。如果把这些元素中的第一个移除，之后的那个就会成为默认的，并且被设置为蓝色虚线边框。浏览器支持的详细情况可以参考下面的兼容性章节。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/y9Oi9N4K/embed/result,html,css/" width="100%" height="550px"></iframe>

###浏览器兼容性

支持`:default`的浏览器有：Chrome 10+, Firefox 4+, Safari 5+, 和 Opera 10+ 。Internet Explorer, Android, 和 iOS不支持。

但是不同的浏览器对`:default`的支持程度不一样。而且浏览器只会在确定的UI元素上使用`:default`，不会在其他的元素上。

* Firefox完全支持：可以在复选框，单选按钮，以及input类型的提交按钮上使用`:default`。
* Opera（pre-webkit）只支持在复选框和单选按钮上使用。
* 基于WebKit和Blink内核的浏览器（包括WebKit内核的Opera, Safari和Chrome）只支持在input类型的提交按钮上使用`:default`，复选框和单选按钮不行。
* Internet Explorer完全不支持`:default`。

#深度阅读

* [CSS Basic User Interface Module Level 3](http://dev.w3.org/csswg/css-ui/#pseudo-default)
* [Selectors Level 4](http://dev.w3.org/csswg/selectors4/#default-pseudo)
* [HTML5](http://www.w3.org/TR/html5/disabled-elements.html#selector-default)
* [HTMl5 Forms](http://www.w3.org/TR/html5/forms.html#default-button)

###相关文章

* :indeterminate
* :checked
* :enabled
