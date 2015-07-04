title: CSS reference—— ::first-letter
date: 2015-07-04 15:26:09
description: CSS参考 ::first-letter
tags: CSS
---

>  原文地址：[http://tympanus.net/codrops/css_reference/first-letter/](http://tympanus.net/codrops/css_reference/first-letter/)

###`::first-letter`是一个伪元素，用来选择块级元素（例如段落`<p>`）第一行的第一个字母，并且这个字母的前面不存在其他别的内容（如图片或者内嵌表格）。

伪元素`::first-letter`不会选择行内元素的第一个字母，也就是说，那些具有样式`display: inline;`的元素。它只会在那些`display`值为`block`，`inline-block`， `table-cell`， `table-caption`， 或者`list-item`的元素上起作用。

如果这个元素的开始被附加了一些文本内容，通过使用`::before`伪元素的`content`属性，那么生成内容的第一个字母会是`::first-letter`的选择目标。例如，如果一个段落使用下面的规则来添加了一些内容：

<!--more-->

```css
p:before {
    content: "Note: ";
}
```

选择器`p:first-letter`会匹配`Note`的`N`，就算这个段落中还存在其他的文本。

如果第一个字母其实上是一个数字，`:first-letter`也会匹配到，例如`25 cats`中得`2`。

首字母必须出现在第一行，例如，在这段代码中：

```html
<p><br>First level of...&ly;/p>
```

第一行不包含任何字母（这行被折进另外一行，没有任何内容在里面），那么`:first-letter`不能匹配到任何东西。就这个例子来说，它不能匹配到`First`中得`F`。

首字母前面或者后面的标点符号会被包含在`:first-letter`当中， 例如，为下面这段文本设置首字母样式：

```html
<p>
    "Drawing from our own ignorance, and from the united ignorance of others (most freely and generously bestowed), we mapped out the details of the campaign with glibness and ease. At Vardö we were to purchase furs to wear and horses to ride."
</p>
```

将看起来像下面这张图，引号也会做为`::first-letter`的一部分而被设定样式。

 {% img http://codropspz.tympanus.netdna-cdn.com/codrops/wp-content/uploads/2015/01/first-letter-with-punctuation.png [title text [alt punctuation style]] %}

####用于`::first-letter`样式的属性

只有一部分的CSS属性能够被用于设置`::first-letter`，他们是：

* 字体属性：`font`, `font-style`, `font-variant`, `font-weight`, `font-size`, `line-height`, 和 `font-family`。
* `text-decoration`, `text-transform`, `letter-spacing`, `word-spacing` (在适当的时候), `float`, `vertical-align` (仅仅当`float`的值为`none`的时候), 和 `color`。
* Margin 属性: `margin`, `margin-top`, `margin-right`, `margin-bottom`, 和 `margin-left`。
* Padding 属性: `padding`, `padding-top`, `padding-right`, `padding-bottom`, 和 `padding-left`。
* Border 属性: `border`, `border-width`, `border-style`, `border-color`, 以及这些属性对应的复合属性。
* Background 属性: `background`, `background-color`, `background-image`, `background-position`, `background-repeat`, `background-size`, 和 `background-attachment`。

###备注

如果元素是一个列表项（`display: list-item`），`::first-letter`会匹配项目符号之后的首字母。如果列表项的样式中有`list-style-position: inside`，客户端可能会忽略`::first-letter`。

关于如何看待某些字母组合，某些语言可能有特殊的规则。例如在荷兰语中，如果字母组合`ij`出现在某个单词的前面，这两个字母都应该算在`::first-letter`伪元素当中。

`table-cell`或者`inline-block`元素的首字母不能成为其父元素的首字母。例如，在下面的代码片段中：

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

`div`的首字母不是字母`H`，事实上，`div`没有首字母。

如果组成首字母的字母不在同一个元素中，例如`<p>'<em>Tomorrow..</em>...</p>`中的`'T`，客户端可能从一个元素中创建首字母伪元素，或者两个元素都创建，或者简单的不创建伪元素。

`::first-letter`伪元素能够用于创建“首字母大写”和“下沉”，那些是比较普遍的排版效果。这种类型的首字母和行内级别的元素类似，如果它的`float`属性为`none`，否则就和一个浮动元素类似。

伪元素`::first-line`能够用于设置元素第一行的样式，`::first-letter`会继承那些应用在`::first-line`上面的样式。如果同时使用了`::first-line`和`::first-letter`，定义在`::first-letter`上面的样式会覆盖`::first-line`的。

和其他的伪元素和伪类一样，`::first-letter`也可以链式的加在其他伪元素和伪类的后面。参考以下章节的示例。

####`(:)`和`(::)`的不同 

你很有可能会遇到（或者已经遇到了）用一个冒号代替两个冒号的表示法：`:first-letter`。

在CSS1和CSS2中，定义伪元素以一个冒号（:）开始，就像伪类一样（例如`:hover`）。在CSS3中，为了和伪类区分，引入两个冒号（::）来定义伪元素。

```css
/* old CSS2 syntax */
p:first-letter {
    /* content and styles here */
}

/* new CSS3 syntax */
p::first-letter {
    /* content and styles here */
}
```

凡是支持两个冒号表示法的浏览器，都支持一个冒号表示法。但是IE8不支持两个冒号表示法。所以，除非你需要支持IE8，否则就可以使用两个冒号表示法，而不必担心浏览器的兼容性。 

在这片文章所有的例子中，为了更好的支持在IE8下阅读的用户，采用的是一个冒号的语法。 

###案例

下面的例子在文章第一段的第一个字母上设置了一个不同的字体族，示例用了`:first-of-type`伪类选择器来选择文章的第一段。

```css
/* chaining ::first-letter with the :first-of-type selector */
p:first-of-type::first-letter {
    font-family: "Gentium Book Basic", serif;
    font-weight: bold;
    color: grey;
}
```

###在线演示

下面的演示设置了文章中段落的首字母。

如果你的浏览器支持`:first-of-type`伪类选择器，那么你会看到第一段的首字母为粉红色，衬线字体。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/g9woiDBK/embed/result,html,css/" width="100%" height="300px"></iframe> 

###浏览器兼容性

支持两个冒号表示法`::first-letter`的有：Chrome, Safari, Opera, Internet Explorer 9+, 以及Android和iOS。

###注意

两个冒号表示法`::first-letter`是在CSS Level 3中引入，不支持Internet Explorer 8及其之前的版本，只有一个冒号表示法`:first-letter`在IE 5.5+都被支持。

###深度阅读

* [CSS Selectors Level 2](http://www.w3.org/TR/CSS2/selector.html#first-letter)
* [CSS Selectors Level 3](http://dev.w3.org/csswg/selectors3/#first-letter)

###相关文章

* attr()
* [::before](http://lesrecord.com/2015/07/03/CSS-reference-before/)
* content
* ::placeholder
* ::first-line
* [::after](http://lesrecord.com/2015/07/02/CSS-reference-after/)