title: ::first-line | CSS reference
date: 2015-07-06 17:09:38
description: CSS参考 ::first-line
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/first-line/](http://tympanus.net/codrops/css_reference/first-line/)

###`::first-line`是一个伪元素，用来选择块级元素（例如段落`<p>`）的第一个格式化的行。

与其他的伪元素一样，`::first-line`并不会匹配任何真实的HTML元素。`::first-line`伪元素不会匹配行内元素的第一行，也就是说，`display: inline`的元素。它只会在`display`的属性值为`block`，`inline-block`，`table-cell`，`table-caption`或者`list-item`的元素上起作用。

某个元素第一行文本的数量取决于很多因素，包括页面宽度，字体大小等等。

<!--more-->

###用于`::first-line`样式的属性

`::first-line`伪元素和行内元素类似，但是有明显的限制，只有一部分的CSS样式可以用来设置`::first-line`的属性：

* Font属性：`font`, `font-style`, `font-variant`, `font-weight`, `font-size`, `line-height`, 和 `font-family`。
* Background 属性: `background`, `background-color`, `background-image`, `background-position`, `background-repeat`, `background-size`, 和 `background-attachment`。
* `text-decoration`, `text-transform`, `letter-spacing`, and `word-spacing`。

客户端也有可能应用其他的样式属性。

###备注

元素第一个格式化的行，很可能出现在其具有相同文档流的后代块级元素中（例如，一个块级后代元素没有因为浮动或者定位而脱离文档流）。例如，下面的例子中，`div`的第一行也是段落`p`的第一行（假设`div`和`p`都是块级元素，没有改变他们的`display`属性）。

```html
<div>
    <p>This line...</p>
</div>
```

`table-cell`或者行内快的第一行不能够是其祖先元素的第一个格式化的行，所以，下面的例子中，`div`第一个格式化的行不是行`Hello`。

```html
<div>
    <p style="display: inline-block">
        Hello
        <br>
        Goodbye
    </p> 
    etcetera
</div> 
```

同样要注意，下面例子中，段落`p`的第一行不包含任何字符（假设`<br>`是默认样式），那么单词`First`不是第一个格式化的行，第一个格式化的行仅仅由空格组成。

```html
<p><br>First...</p> 
```

和其他伪元素和伪类一样，`::first-line`能够链式的加在其他的伪类和伪元素后面，详细信息参考下面的示例。

####继承性和差异性

在CSS继承中，出现在第一行中的那部分子元素仅仅从`::first-line`伪元素中继承适用于之上的那部分属性。其他的属性继承，来自于第一行伪元素的非伪元素的父元素之上。（没有出现在第一行的那部分子元素则总是从其父元素那边继承。）

`::first-letter`伪元素用于设置元素第一个字母的样式，`::first-letter`会继承应用在`::first-line`之上的样式。如果同时使用`::first-letter`和`::first-line`，`::first-letter`会覆盖定义在`::first-line`上面的样式。

定义在元素上能够对一行起作用的样式，都会被`::first-line`上定义的覆盖。也就是说，如果在段落上定义一些样式，会被`::first-line`中冲突的样式覆盖掉——`::first-line`总会获得最高的优先级，就算段落中一些样式应用了规则`!important`。例如：

```html
<p class="text" id="text">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Non modi aspernatur accusamus repudiandae atque suscipit dolorem rerum. Iure explicabo repellendus magnam quisquam porro vitae quibusdam quam maiores fugiat! Enim, sed.
</p>
```

`::first-line`伪元素为段落的第一行定义样式。

```css
p::first-line {
    tetx-transform: uppercase;
}
```

段落中第一眼的文本会被转化为大写字母，尽管下面的一些规则存在：

```css
/* General type (tag) selector */
p {
    text-transform: lowercase;
}

/* Class selector */
.text {
    text-transform: lowercase;
}

/* ID selector */
#text {
    text-transform: lowercase;
}

/* ID selector with !important bash */
#text {
    text-transform: uppercase !important;
}
```

上面四种选择器内的规则都会被`::first-line`中的所覆盖。

####`(:)`和`(::)`的不同

你很有可能会遇到（或者已经遇到了）用一个冒号代替两个冒号的表示法：`:first-line`。

在CSS1和CSS2中，定义伪元素以一个冒号（:）开始，就像伪类一样（例如`:hover`）。在CSS3中，为了和伪类区分，引入两个冒号（::）来定义伪元素。

```css
/* old CSS2 syntax */
p:first-line {
    /* content and styles here */
}

/* new CSS3 syntax */
p::first-line {
    /* content and styles here */
}
```

凡是支持两个冒号表示法的浏览器，都支持一个冒号表示法。但是IE8不支持两个冒号表示法。所以，除非你需要支持IE8，否则就可以使用两个冒号表示法，而不必担心浏览器的兼容性。

在这片文章所有的例子中，为了更好的支持在IE8下阅读的用户，采用的是一个冒号的语法。

###案例

下面的代码片段会把一片文章中，第一段的第一行中的文本转化为大写字母。例子中使用了`:first-of-type`伪类来选择文章的第一段。

```css
/* chaining ::first-line with the :first-of-type selector */
p:first-of-type::first-line {
    text-transform: uppercase;
    font-weight: bold;
}
```

下面这行CSS对段落的第一行不起作用，因为`margin`属性不能用于`::first-line`。

```css
p::first-line {
    margin-left: 1.5em;
}
```

###在线演示

下面的示例定义了文章段落第一行的样式，他们具有下划线，粗体文字，以及被转化成全大写字母。

如果你的浏览器支持`:first-of-type`伪类选择器，那么第一段的第一行文本会是粉红色。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/HX6N5Kfb/embed/result,html,css/" width="100%" height="300px"></iframe>

示例中所有段落的第一行都会被渲染成大写字母。如果你使用的是Chrome，可能不会起作用。参考下面浏览器兼容性。

###浏览器兼容性

支持两个冒号语法（`::first-line`）的浏览器有：Chrome, Firefox, Safari, Opera, Internet Explorer 9+, 以及 Android 和 iOS。

两个冒号表示法（`::first-line`）是在CSS Level 3中引入，不支持Internet Explorer 8及其之前的版本，只有一个冒号表示法:first-letter在IE 5.5+都被支持。

###注意

在Chrome中有一个[历史问题](https://code.google.com/p/chromium/issues/detail?id=142827)：`::first-line`元素的`text-transform`属性会失效。

###深度阅读

* [CSS Selectors](http://www.w3.org/TR/CSS2/selector.html#first-line-pseudo)
* [CSS Selectors Level 3](http://dev.w3.org/csswg/selectors3/#first-line)

###相关文章

* [::first-letter](http://lesrecord.com/2015/07/04/CSS-reference-first-letter/)
* attr()
* [::before](http://lesrecord.com/2015/07/03/CSS-reference-before/)
* content
* [::after](http://lesrecord.com/2015/07/02/CSS-reference-after/)
