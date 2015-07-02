title: CSS reference—— ::after
date: 2015-07-02 14:32:22
description: CSS参考 ::after
tags: CSS
---

{% blockquote %}
原文地址：[http://tympanus.net/codrops/css_reference/after/](http://tympanus.net/codrops/css_reference/after/)
{% endblockquote %}

##`::after`可以用来生成一个具有内容的元素，它是所匹配的元素中抽象上的最后一个子元素，能够被设定样式 

通过`::after`插入的内容通常会被放置到匹配元素内部其他内容的后面，并且以行内元素来显示。插入的实际内容通过`content`属性来指定。 

例如，假设你想在所有的超链接后面增加一个小图标，用来表明这个链接指向网站其他的页面，而不是用户正在浏览的那个。用一个小图标来告诉用户，那个他们将要点击的链接，将会把他们带到另外一个域名，这通常是一个很好的点子。这样一个图标可以被加在这个链接的前面或者后面，比较普遍的做法是加在链接的后面，所以我们接下里要做的一件事情——使用`::after`，我们将在页面上，具有相同类名`.external`的超链接后面插入这个小图标（{% img http://codropspz.tympanus.netdna-cdn.com/codrops/wp-content/uploads/2014/12/external-link.png %} ）

```html
Let's <a href="http://movethewebforward.org/" class="external">Move The Web Forward</a> together!
```

<!--more-->

下面的代码片段会在链接的后面加上图标，这个图标会作为行内元素插入到链接内容的后面。 

```CSS
.external::after {
    content: url(external-link.png);
    padding-left: 5px; /* 在图片和前面文字之间添加一点空间 */
}
```

使用`content`属性来增加图片，但是使用伪元素插入的图片不能调整尺寸，它们会用自身的尺寸插入进去，所以在使用之前，你必须调整好图片的尺寸。

下面是上面代码的结果： 

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/dYfExU3k/embed/result,html,css/" width="100%" height="300px"></iframe> 

因为通过伪元素插入的内容并没有真的插入到DOM中，通常是不可能通过浏览器的开发工具来查看这些内容。但是，Chrome 32+和Firebug for Firefox允许你在DOM中查看这些伪元素的位置，并能够在CSS面板中查看关联的样式。在Chrome开发工具中查看之前的那个例子，会是下面的结果： 

 {% img http://codropspz.tympanus.netdna-cdn.com/codrops/wp-content/uploads/2014/12/inspecting-after.png [title text [alt inspection pseudo-element]] %}

上述演示也表明了使用`::after`增加的内容，会被行内定位到引用块剩余内容的后面。 

因为`::after`的内容会被插入到元素内部其他内容的后面，那意味着伪元素的层级会比其他出现在资源树前面的元素更高。 

伪元素能够用于插入几乎所有种类的的内容，包括符号（如上），字符串和图片。例如，下面全部都是带有正确内容的合法`::after`申明：

```
.element::after {
    content: url(path/to/image.png); /* 图片，例如，图标 */
}

.element::after {
    content: "(To be continued...)"; /* 字符串 */
}

.element::after {
    content: "\201C"; /* 也是字符串，用unicode来表示，作为一个单个的字符来渲染 */
}
```

伪元素`::after`的内容也可以是一个计数器[`counter`]，也可以空着。空伪元素在清除元素内部的浮动是非常有用的。例如，Nicolas Gallagher使用`::after`和`::before`来清除浮动容器内部的浮动：[ micro clearfix hack ](http://nicolasgallagher.com/micro-clearfix-hack/)。你可以去阅读更多关于浮动的内容，并且去了解它在浮动体内部是如何工作的。 

伪元素`::after`能够像其他别的内容一样被定义样式，它能被浮动，被定位，甚至添加动画。（并不是所有的浏览器都支持对伪元素添加动画，参考浏览器支持章节来了解更多。） 

伪元素能够被添加样式的能力，好像他们是页面上真正的元素一样，导致使用他们大部分是出于“装饰”的目的。在CSS中，伪元素被大量使用在创建[几何图形](http://www.samuelrossille.com/css-shape/)，相对于其他别的用法。下面的一个例子就会展示这样一个用例。通过使用一个元素和它的伪元素，可以创建一个八角星。开始的四个角是用元素自身创建的，做成一个矩形。然后，这个元素的伪元素被设置为和父节点同样的高度和宽度，并绝对定位在父元素的上面，然后旋转45°，组成一个八角星。

```
/* 
    为了更好的显示例子中元素和伪元素的位置关系，他们都被设置成了半透明，用 `opacity`属性。
    移除opacity属性值，你能够看到一个完全不透明的八角星。
*/
.element {
    width: 250px;
    height: 250px;
    background-color: #009966;
    opacity: .8;
    position: relative;
    margin: 100px auto;
}

.element:after {
    content: "";
    position: absolute;
    display: block;
    width: 250px;
    height: 250px;
    background-color: #009966;
    opacity: .8;
    transform: rotateZ(45deg);
}
```

因为伪元素仅仅只被用作了装饰元素，所以它的内容可以为空。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/kFTn9yJk/embed/result,html,css/" width="100%" height="480px"></iframe> 

这个例子也可以使用`::before`伪元素来制作。

##备注

####`(:)`和`(::)`的不同 

你很有可能会遇到（或者已经遇到了）用一个冒号代替两个冒号的表示法：`:after`。

在CSS1和CSS2中，定义伪元素以一个冒号（:）开始，就像伪类一样（例如`:hover`）。在CSS3中，为了和伪类区分，引入两个冒号（::）来定义伪元素。 

```
/* old CSS2 syntax */
.element:after {
    /* content and styles here */
}

/* new CSS3 syntax */
.element::after {
    /* content and styles here */
}
```

凡是支持两个冒号表示法的浏览器，都支持一个冒号表示法。但是IE8不支持两个冒号表示法。所以，除非你需要支持IE8，否则就可以使用两个冒号表示法，而不必担心浏览器的兼容性。 

在这片文章所有的例子中，为了更好的支持在IE8下阅读的用户，采用的是一个冒号的语法。 

####访问友好度

通过伪元素增加的内容，并没有真的插入到DOM中——仅仅是视觉上的显示。因此，使用屏幕阅读器的用户不能访问和阅读通过伪元素生成的内容。那么，推荐不要用伪元素在页面中插入及其重要的内容（例如，与文章相关的页脚注释）。 

伪元素最常见的作用是插入装饰性的内容，并且页面上内容的意义和完整性不应该与插入的内容相关连。 

同时，由于使用伪元素加入的内容并没有插入到DOM中，那意味着你不能使用JavaScript为其附加事件处理。 

##案例

伪元素，包括`::after`，可以用来做很多事情，创建很多效果。除了上面的例子之外，下面的文章包含一些伪元素的用例，推荐细细品读一番。 

*    [使用伪元素实现图片替换](http://nicolasgallagher.com/css-image-replacement-with-pseudo-elements/) 
*    [使用CSS伪元素:before和:after](http://www.bennadel.com/blog/2445-Using-CSS-Pseudo-Elements-before-And-after.htm) 
 
####使用`::after`来调整打印的链接样式 
 
对`::after`伪元素来说，一个非常有用的使用场景就是在打印样式表中。因为链接是不能在纸上点击的（当然咯），你通常都应该把链接指向的URL附带在链接的后面，以便读者可以在需要的时刻访问他们。下面的例子就是这么做的： 

```
@media print {
    a[href]::after {
        content: " (" attr(href) ")";
    }
}
```

上面的代码片段包含多个CSS规则：属性选择器（`a[href]`）， `content`属性， 以及`attr()`函数。

* 属性选择器会选择页面中，所有具有`href`属性的链接。
* `::after`告诉浏览器，选择那些链接，并且在链接文字的后面插入`content`属性的值。
* `content`属性自身可以接受相当多种类的值，其中一种就是字符串。字符串可以被分割成几个部分，每个部分都必须用引号包裹。多个字符串可以拼接成一个字符串，详细请参考介绍`content`属性的文章。 
* `attr(x)`函数：以字符串的方式，返回选择器主体元素`X`属性的值，在这个例子中，对应的就是`::after`伪元素。 

所以上面的选择规则会匹配所有具有`href`属性的链接（使用属性选择器），然后使用`attr(x)`函数获取`href`属性的值，并且在`::after`伪元素的内容中应用这个值，那将附加在链接文字的后面。

除此之外，这个代码片段还使用了媒体查询，通过规则`@media`，这会某一种具体的媒体类型（在这个案例中是打印）定义一系列的样式。

下面的一个在线案例展示了在网页上这种规则的效果。如果想仅仅只限定在打印样式表中的话，你必须使用上面提到的媒体查询规则。出于演示的目的，在这个例子中，我们应用到页面上了。

 <iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/AuXAZ3c8/embed/result,html,css/" width="100%" height="300px"></iframe>  

##在线演示 

下面例子使用`::after`在那些鼠标悬停张开一个子菜单的菜单项中增加一个箭头符号，通过转义相应的unicode值，箭头被添加在`content`属性中。这是经由CSS表示和添加象形符号的一种普遍方式。

 <iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/RETvk1HZ/embed/result,html,css/" width="100%" height="300px"></iframe> 
 
当悬停在菜单项之上时候，向下指向的箭头会被向上指向的箭头所取代，通过改变`content`属性值的方式。能够这样做的原因是应为伪元素和伪类都可以链式调用，像这样`li:hover::after`，当悬停时候，选择添加在菜单项上的`::after`伪元素。 

##浏览器兼容性

支持一个冒号表示法`:after`的有：Chrome, Safari, Opera, Internet Explorer 8+, 以及Android和iOS。

以上所有的浏览器都支持两个冒号的语法`::after`，但是在Internet Explorer中，只有IE9及以上版本才支持。

Chrome 26+, Firefox 4+, Safari 6.1+, Opera( post Blink )和Internet Explorer 10+支持为伪元素添加动画效果。 

##注意 

Internet Explorer不支持对伪元素使用`z-index`。

##深度阅读 

* [CSS生成的内容，自动编号和列表](http://www.w3.org/TR/CSS2/generate.html#before-after-content) 
* [第三层级CSS选择器](http://dev.w3.org/csswg/selectors3/#gen-content) 
* [学习使用CSS中:before和:after伪元素](http://coding.smashingmagazine.com/2011/07/13/learning-to-use-the-before-and-after-pseudo-elements-in-css/) 

##相关文章

* content
* ::selection
* ::before
* ::placeholder
* ::first-letter
* ::first-line
* attr()