title: :dir | CSS reference
date: 2015-07-13 17:29:35
description: CSS参考 :dir
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/dir/](http://tympanus.net/codrops/css_reference/dir/)

###`:dir()`是一种CSS伪类选择器，用于选择那些基于自身文本方向的元素，这种方向性是由文档语言来决定的。

元素中文本的方向可以用CSS `direction`属性来定义。但是`:dir()`伪类选择器并不会匹配那些完全由`direction`属性确定方向性的元素——如果想要匹配这个选择器，需要在文档中定义方向性，而不是在CSS中，因为`:dir()`不能根据文本样式进行匹配。

在HTML5文档中，可以通过`dir`属性来定义元素的方向性。其方向可以设置为`ltr`（从左到右）或者`rtl`（从右到左）。例如：

```html
<article dir="rtl">
    <!-- ... -->
</article>
```

<!--more-->

`:dir()`伪类选择器需要`ltr`或者`rtl`作为参数。伪类`:dir(ltr)`表示那些具有从左到右（`ltr`）的方向的元素，伪类`:dir(rtl) `表示那些具有从右到左（`rtl`）的方向的元素。除了`ltr`和`rtl`之外的值都是不合法的，而不会匹配任何元素。（如果将来标记规范定义了其他方向，那么CSS选择可能会扩展相应的值。）

`:dir()`的参数需为一个单独的标示符，否则选择器会是不合法的。空白符可以出现在标示符和括号之间。

###备注

因为元素的方向是通过设置`dir`属性来确定的，所以一个设置过方向的元素也可以用属性选择器`[dir = ""]`来选择，例如：

```css
article[dir="rtl"] {
    /* styles applied to article elements that have a rtl directionality set using the dir attribute */
}
```

**`:dir()`的用法并不等同于`[dir = ""]`选择器的用法**

`[dir = ""]`属性选择器只会比较元素上给出的属性。那意味着，它只能匹配那些被设置过`dir`属性的元素，不能匹配那些没有设置`dir`属性的元素，就算这个元素在文档其他地方明确定义过方向。除此之外，如果`dir`的属性被设置为`auto`，那么`[dir = "ltr"]`和`[dir = "rtl"]`都匹配不到。

另一方面，如果某个元素的方向，继承自它有合法`dir`属性的最近的祖先元素，那么`:dir()`伪类选择器也能匹配到。如果元素的`dir`的属性被设置为`auto`，匹配`:dir(ltr)`还是`:dir(rtl) `取决于元素的实际方向，由其内容来确定。

###案例

下面的代码片段会匹配具有`ltr`方向的元素，并设定其样式：

```css
*:dir(ltr) {
    /* styles here */
}
```

下面的代码会选择所有方向为`rlt`的引用块：

```css
blockquote:dir(rtl) {
    /* styles here */
}
```

###在线演示

下面示例中匹配`:dir(ltr)`的文本为蓝色，匹配`:dir(rtl) `的文本是绿色。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/w75xRCUo/embed/result,html,css/" width="100%" height="300px"></iframe>

###浏览器兼容性

目前只有Firefox支持`:dir()`伪类选择器，并且需要`-moz-`前缀。

###深度阅读

* [CSS Selectors Level 4](http://dev.w3.org/csswg/selectors4/#the-dir-pseudo)

###相关文章

* :lang()

