title: :first | CSS reference
date: 2015-07-20 10:23:55
description: CSS参考 :first
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/first/](http://tympanus.net/codrops/css_reference/first/)

###`:first `是一种CSS伪类选择器，用于选择打印文本的首页。

它会和选择打印文档中所有页面的`@page`规则联合起来使用，因此，当和`@page`一起使用的时候，`:first `实际上扮演着一种过滤器的角色，用来选择所有页面的第一页。

```css
@page :first {
    /* styles for the first page */
}
```

<!--more-->

在`@page :first`规则中定义的样式会覆盖那些没有定义任何伪类的`@page`规则提供的样式。

除了`:first `，`@page`还能和另外两种伪类联合使用，他们是`:left`和`:right`，用于选择双页文档中对应的左右页面。

在`@page :first`规则中定义的样式同样也会覆盖那些，在`:left`和`:right @page`规则中定义的样式。

着重提醒下，在某个`@rule`中并不能使用所有的CSS属性，参考`@page`文章获取更多关于那些可以使用的属性。

###备注

客户端会把所有的页面自动的归类于`:left`或者`:right`伪类当中，文档的第一页属于`:left`或者`:right`，取决于根元素主要的书写方向。例如，文档第一页的主要书写方向是从右到左，那么会被归于`:right`；如果文档第一页的主要书写方向是从左到右，那么会被归于`:left`。为了明确规定文档是从左还是右开始打印，作者可以在初始生成框中插入一个[分页前](http://tympanus.net/codrops/css_reference/page-break-before)（page break before）。

如果在初始生成框之前有个一个强制分页，在CSS 2.1中确定了`:first `会应用于分页之前的空白页还是随后的页面。

###官方语法

`:first `伪类选择器像这样和`@page`联合起来使用：

```css
@page :first {
    /* styles for the first page */
}
```

###案例

```css
/* All margins set to 2cm */
@page { 
    margin: 2cm; 
} 

/* Top margin on first page 10cm */
@page :first {
  margin-top: 10cm;    
}
```

###浏览器兼容性

支持`:first `伪类选择器的浏览器有：Internet Explorer 8+ 和 in Opera 9.2+ 。Firefox不支持，其他的浏览器也没有发现支持的。

###深度阅读

* [Paged Media: CSS Level 2.1](http://www.w3.org/TR/CSS2/page.html#page-selectors)
* [CSS Paged Media Module Level 3](http://dev.w3.org/csswg/css-page/#valuedef-first)

###相关文章

* :right
* :left
* @page
