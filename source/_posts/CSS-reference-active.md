title: :active | CSS reference
date: 2015-07-09 15:56:21
description: CSS参考 :active
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/active/](http://tympanus.net/codrops/css_reference/active/)

###`:active`是一种CSS伪类，用来匹配具有激活状态的元素，并在那些元素上面定义样式。

`:active`伪类是一种动态类，只有当用户激活某个元素的时候，才会被应用样式。常常被用于定义突出某个激活状态的元素，或者定义其样式（正如其名）。更确切的说，它会突出一个元素（通常是一个超链接`<a>`），在其被点击和释放之间。

定义某个元素激活状态下的样式，会提供更好的用户体验，因为页面会给与用户一个反馈，当他在点击这个元素的时候。如果没有这种反馈，用户可能会认为他们的动作没有成功，因为她没有获得一个视觉提示，来确认点击是否成功了，可能会连续多次点击这个元素。

<!--more-->

`:active`伪类绝大部分时候会用于设定超链接的样式，但是它也可以用于设定页面其他元素的样式，甚至于根元素（`html`）。例如，下面的例子，会在文本段落被点击的时候，将其背景色设置为浅灰色：

```css
p:active {
    background-color: #aaa;
}
```

当使用`:active`设定超链接样式的时候，与其他三种伪元素一起使用会更好，他们是：`:link`，`:visited`，和`:hover`，通常也是用于设定不同链接状态的样式。可以参考每个伪类对应的文章来获取详细信息和范例。

###备注

一个元素可以同时具有`:visited`和`:active`（或者`:link`和`:active`）。

如果同时使用四种链接伪类，他们最好按照下面的顺序来使用：`:link`, `:visited`, `:hover`, 和 `:active`。例如：

```css
a:link {
    /* style links */
}

a:visited {
    /* style visited link */
}

a:hover {
    /* hover styles */
}

a:active {
    /* active state styles */
}
```

通过使用类似 “**L**ast **V**intage **H**at **A**vailable” 的技巧，可以很容易记住上面的顺序。你也可以在[spacefm.com](http://spacefem.com/mnemonics/)创建自己的记忆技巧。

因为一些状态样式可能会覆盖其他的状态样式，所以顺序最好这样来，否则就有可能不会按照期望的来显示。例如，如果你把`:visited`的状态样式放在最后，它将会覆盖链接的`:hover`和`:active`的状态样式，并且无论链接是在悬停状态或者被点击，`:visited`的样式都会应用在之上。

除了上面提到的四种状态之外，你也可以设置链接获得焦点时候的样式。`:focus`伪类能够达到这个目的。为了记住顺序，你能把`fur`加在之前的句子中：“**L**ast **V**intage **F**ur **H**at **A**vailable”。在介绍`:focus`伪类的文章中你可以获得更多的信息。

*对于那些有多个鼠标按钮的系统，`:active`只会在最初的激活按钮（通常为鼠标的左键）上起作用，以及其他的别名。*

###案例

下面的例子设置了链接和页面上其他元素的`:active`状态的样式，可以在`:active`状态下使用任何样式属性。

```css
a:active {
    background-color: black;
    color: white;
}

p:active {
    border: 2px dotted BlanchedAlmond;
}

body:active {
    border: 5px solid
}
```

###在线演示

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/kWulr51g/embed/result,html,css/" width="100%" height="300px"></iframe>

###浏览器兼容性

`:active`伪类的兼容性与其应用的元素相关。

在链接元素`<a>`上使用`:active`伪类，所有主流的浏览器都支持：Chrome, Firefox, Safari, Opera, Internet Explorer, 以及 Android 和 iOS。

支持在页面其他元素上使用`:active`伪类的有：Chrome, Firefox, Opera, Internet Explorer 8+, 和 Android。

###深度阅读

* [CSS Selectors Module](http://www.w3.org/TR/CSS2/selector.html#dynamic-pseudo-classes)
* [CSS Selectors Module Level 3](http://dev.w3.org/csswg/selectors3/#useraction-pseudos)

###相关文章

* :visited
* :hover
* :link
* :focus
