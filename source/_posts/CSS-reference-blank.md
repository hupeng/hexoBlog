title: CSS reference—— :blank
date: 2015-07-10 17:36:54
description: CSS参考 :blank
tags: CSS
---

> 原文链接：[http://tympanus.net/codrops/css_reference/blank/](http://tympanus.net/codrops/css_reference/blank/)

###`:blank `是一种CSS伪类选择器，用于选择打印文档（如一本书）中，因为页面强制分页而导致的空白页面。

通常会和`@page`规则联合起来使用，`@page`用于匹配打印文档中所有的页面。因此，当使用`@page`的时候，`:blank `会扮演过滤器的角色，用来选择因为页面强制分页而导致空白页面。

```css
@page :blank {
    /* styles for the empty page */
}
```

只有属性`page-break-before`和`page-break-after`的值为`left`或者`right`，才能产生匹配`:blank `的空白页。

定义在`:blank @page`规则上的样式会覆盖那些没有提供伪类的`@page`规则中的样式。

<!--more-->

同样，定义在`:blank @page`规则上的样式也会覆盖那些通过`:left`和`:right @page`规则定义的样式。（`:left`和`:right`是用于选择双页打印文本中左右页面的选择器，例如一本书，参考`:left`和`:right`的文章来获取更多信息。）

特别需要注意的是，并不是所有的CSS规则都可以在`@rule`中使用，参考`@page`获得更多信息，以及可以使用的CSS属性。

###备注

在以后的CSS规范中，`page-break-before`和`page-break-after`将会被相应的`break-before`和`break-after`取代。

###官方语法

```css
@page :blank {
    /* styles for the empty page */
}
```

###案例

由于只有页边距，orphans（不懂何意），视口，和分页符可以在`@page`规则中设置，所以在空白页中设置这些东西的样式并没有什么意义。

然而，在CSS3中，引进了新的规则来选择页面边距。目前没有浏览器支持他们。下面是一个介绍如何在空白页中使用页面边距规则的例子，这个例子在空白页的上边距中心插入一段内容：

```css
@page :blank {
  @top-center { content: "This page is intentionally left blank" }
}
```

一旦可用，将会提供更多内容。

###浏览器兼容性

`:blank`在CSS Level 3中被引入，并且非常新，它的浏览器兼容性还没有查明。

###深度阅读

* [CSS Paged Media Module Level 3](http://dev.w3.org/csswg/css-page/#valuedef-blank)

###相关文章

* page-break-inside
* page-break-after
* page-break-before
* @page

