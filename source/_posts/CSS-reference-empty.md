title: :empty | CSS reference 
date: 2015-07-16 16:30:37
description: CSS参考 :empty
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/empty/](http://tympanus.net/codrops/css_reference/empty/)

###`:empty`是一种伪类选择器，用于选择页面上内容为空的元素。

如果一个元素不包含任何子元素（节点）或者文本内容，就会被认为是空元素。注释和处理指令（processing instructions）不会影响到该元素空与否。因此：

```html
<div><!-- COMMENT HERE  --></div>
```

<!--more-->

会被认为是空元素，会被`:empty`所选择。然而：

```html
<div>
    Text and a child node.
    <p>Some content here.</p>
</div>
<div>
    Text here.
</div>
```

就不是空元素，不能匹配这个选择器。

如果某些空元素具有边距，可能会引起一些奇怪的水平或者竖直空白，选择那些元素并隐藏他们是非常有用的。在那种不再需要空白元素，或不再有用了得动态环境中，移除他们也是非常有用的。

###备注

生成的内容，比如通过伪元素`::before`和`::after`生成的，不能算作“真正”的内容，因此不会影响这个元素的空白性质，就算他们确实存在于元素当中。

例如，空元素`<div></div>`有一些通过`::after`伪元素生成的文本，会被设置亚麻布色的背景。

```css
div {
    padding: 15px; /* make sure it takes up some space to be able to see it rendered (just for sake of demonstration) */
}

div::after {
    content: "I'm generated inside the div."
}

div:empty {
    background-color: linen;
}
```

在下面的在线示例中会看到一个生成内容的例子。

以下的内容来自于[Dudley Storey](http://demosthenes.info/)的[这篇文章](http://demosthenes.info/blog/692/Vanishing-Acts-The-CSS-empty-Selector)：

空格和空子元素会被认为是元素内部的字符信息，所以如果某个元素中存在两个当中的一个，就不再是空元素了。例如下面两个元素都不是空元素：

```html
<p> </p> <!-- contains a white space -->
<p><span></span></p> <!-- contains an empty element -->
```

由于空格会被当做内容来看待，所以那些没有闭合处在开启状态的元素标签也会被认为是非空的，例如：

```html
<p>
```

然而，如果一个开启的标签直接跟随着另外一个标签，那么它会被认为是空元素。

```html
<p><p>content...</p>
```

如果一个开启的标签后面再跟随一个开启的标签，而其后没有其他别的标签了，那么第一个标签会被认为是空的，第二个则不是（因为空格的缘故）。例如：

```html
<p><p>
```

自闭合元素，例如`<hr />`, `<br />`, 和`<img />`，会被认为是空，将匹配`:empty`选择器。

你可以在[这里](http://demosthenes.info/blog/692/Vanishing-Acts-The-CSS-empty-Selector)阅读更多关于`:empty`选择器的例子。

###案例

```css
/* selects and hides all elements on a page */
*:empty {
    display: none;
}

/* selects and hides all empty paragraphs */
p:empty {
    display: none;
}

/* selects and hides all menu items that are empty */
nav a:empty {
    display: none;
}

/* selects empty table cells in a table and applies a background color to them */
td:empty {
    background-color: #eee;
}
```

###在线演示

在下面的例子中，空段落会被设置为亚麻布色的背景。看下源码，看下哪些元素被当做成空元素，哪些没有。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/EQxjt5wp/embed/result,html,css/" width="100%" height="300px"></iframe>

###浏览器兼容性

支持`:empty`伪类的浏览器有： Chrome, Firefox, Safari, Opera 9.5+, Internet Explorer 9+, 以及 Android 和 iOS。

###深度阅读

* [CSS Selectors Level 3](http://dev.w3.org/csswg/selectors3/#empty-pseudo)
* [Vanishing Acts: The CSS :empty Selector](http://demosthenes.info/blog/692/Vanishing-Acts-The-CSS-empty-Selector)

###相关文章

* :last-child
* :not()
* :first-child
* :only-child

