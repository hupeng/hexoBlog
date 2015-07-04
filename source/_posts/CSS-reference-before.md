title: CSS reference—— ::before
date: 2015-07-03 10:17:46
description: CSS参考 ::before
tags: CSS
---


>  原文地址：[http://tympanus.net/codrops/css_reference/before/](http://tympanus.net/codrops/css_reference/before/)


###`::before`可以用来生成一个具有内容的元素，它是所匹配的元素中抽象上的第一个子元素，能够被设定样式

通过`::before`插入的内容会被附加到匹配元素内部所有内容的前面，并且默认以行内元素来显示。插入的内容通过`content`来指定。

例如，假设有一段文字的块引用，你可以使用`::before`在实际的文字之前插入一些花式引号。引号会显示在页面上，但是不会被插入到DOM的块引用中。 

```html
<blockquote>
    Your present circumstances don't determine where you can go; they merely determine where you start.—Nido Qubein
</blockquote>
```

<!--more-->

下面的代码片段会使用`::before`，在块引用之前添加一对花式引号。这对引号会作为行内元素被附加到块引用内部文字之前。

```css
blockquote::before {
    content: "\201C";
    /* style the quote */
    color: deepPink;
    font-size: 3em;
    position: relative;
    top: 20px;
}
```

通过转义相应的unicode值，引号被定义在`content`属性中。这是经由CSS表示和添加象形符号的一种普遍方式。

上述代码的结果如下：

 <iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/D4fl7lIS/embed/result,html,css/" width="100%" height="300px"></iframe> 

因为通过伪元素插入的内容并没有真的插入到DOM中，通常是不可能通过浏览器的开发工具来查看这些内容。但是，Chrome 32+和Firebug for Firefox允许你在DOM中查看这些伪元素的位置，并能够在CSS面板中查看关联的样式。在Chrome开发工具中查看之前的那个例子，会是下面的结果：

{% img http://codropspz.tympanus.netdna-cdn.com/codrops/wp-content/uploads/2014/12/inspecting-before.png [title text [alt inspection pseudo-element]] %}

上述演示也表明了使用`::before`增加的内容，会被行内定位到引用块剩余内容的前面。

因为`::before`的内容会被插入到元素内部其他内容的前面，那意味着伪元素的层级会比其他出现在资源树后面的元素更低。

伪元素能够用于插入几乎所有种类的的内容，包括符号（如上），字符串和图片。例如，下面全部都是带有正确内容的合法`::before`申明： 

```css
.element::before {
    content: url(path/to/image.png); /* an image, for example, an icon */
}

.element::before {
    content: "Note: "; /* a string */
}

.element::before {
    content: "\201C"; /* also counts as a string. Escaping the Unicode renders it as a character */
}
```

使用伪元素插入的图片不能调整尺寸，它们会用自身的尺寸插入进去，所以在使用之前，你必须调整好图片的尺寸。 

下面的代码片段为具有类名为`.note`的文本段落添加样式。通过使用`::before`伪元素，每个这样的段落都会有一个`Note:`的字符串附加在之上。你唯一需要做的一件事就是为那些想算作笔记的文本段落加上`.note`类名，并且使用这些CSS，这些段落就会自动获得一个`Note:`前缀。 

```css
p.note {
    font-style: italic;
    color: grey;
}

p.note::before {
    content: "Note: ";
    color: red;
}
```

在下面章节在线演示中，你可以看到这个例子的效果。

`::before`的内容属性也可以是一个计数器，计数器可以是`counter()`或者`counters()`函数，用来美化列表。你可以从Roger Johansson的[这篇文章](http://www.456bereastreet.com/archive/201105/styling_ordered_list_numbers/)中获得更多关于计数器美化列表的内容。 

`::before`的内容属性甚至可以空着，空伪元素在清除元素内部的浮动是非常有用的。例如，Nicolas Gallagher使用`::after`和`::before`来清除浮动容器内部的浮动：[ micro clearfix hack ](http://nicolasgallagher.com/micro-clearfix-hack/)。你可以去阅读更多关于浮动的内容，并且去了解它在浮动体内部是如何工作的。 

伪元素`::before`能够像其他别的内容一样被定义样式，它能被浮动，被定位，甚至添加动画。（并不是所有的浏览器都支持对伪元素添加动画，参考浏览器支持章节来了解更多。） 

伪元素能够被添加样式的能力，好像他们是页面上真正的元素一样，导致使用他们大部分是出于“装饰”的目的。在CSS中，伪元素被大量使用在创建[几何图形](http://www.samuelrossille.com/css-shape/)，相对于其他别的用法。下面的一个例子就会展示这样一个用例。通过使用一个元素和它的伪元素，可以创建一个八角星。开始的四个角是用元素自身创建的，做成一个矩形。然后，这个元素的伪元素被设置为和父节点同样的高度和宽度，并绝对定位在父元素的上面，然后旋转45°，组成一个八角星。 

```css
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

.element:before {
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

这个例子也可以使用[::after](http://lesrecord.com/2015/07/02/CSS-reference-after/)伪元素来制作。

###备注

####`(:)`和`(::)`的不同 

你很有可能会遇到（或者已经遇到了）用一个冒号代替两个冒号的表示法：`:before`。

在CSS1和CSS2中，定义伪元素以一个冒号（:）开始，就像伪类一样（例如`:hover`）。在CSS3中，为了和伪类区分，引入两个冒号（::）来定义伪元素。 

```
/* old CSS2 syntax */
.element:before {
    /* content and styles here */
}

/* new CSS3 syntax */
.element::before {
    /* content and styles here */
}
```

凡是支持两个冒号表示法的浏览器，都支持一个冒号表示法。但是IE8不支持两个冒号表示法。所以，除非你需要支持IE8，否则就可以使用两个冒号表示法，而不必担心浏览器的兼容性。 

在这片文章所有的例子中，为了更好的支持在IE8下阅读的用户，采用的是一个冒号的语法。 

####访问友好度

通过伪元素增加的内容，并没有真的插入到DOM中——仅仅是视觉上的显示。因此，使用屏幕阅读器的用户不能访问和阅读通过伪元素生成的内容。那么，推荐不要用伪元素在页面中插入及其重要的内容（例如，与文章相关的页脚注释）。 

伪元素最常见的作用是插入装饰性的内容，并且页面上内容的意义和完整性不应该与插入的内容相关连。 

同时，由于使用伪元素加入的内容并没有插入到DOM中，那意味着你不能使用JavaScript为其附加事件处理。 

###案例

伪元素，包括`::before`，可以用来做很多事情，创建很多效果。除了上面的例子之外，下面的文章包含一些伪元素的用例，推荐细细品读一番。 

*    [使用伪元素实现图片替换](http://nicolasgallagher.com/css-image-replacement-with-pseudo-elements/) 
*    [使用CSS伪元素:before和:after](http://www.bennadel.com/blog/2445-Using-CSS-Pseudo-Elements-before-And-after.htm) 


###在线演示 

看一看下面的例子

 <iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/t638YeVe/embed/result,html,css/" width="100%" height="600px"></iframe> 
  

###浏览器兼容性

支持一个冒号表示法`:before`的有：Chrome, Safari, Opera, Internet Explorer 8+, 以及Android和iOS。

以上所有的浏览器都支持两个冒号的语法`::before`，但是在Internet Explorer中，只有IE9及以上版本才支持。

Chrome 26+, Firefox 4+, Safari 6.1+, Opera( post Blink )和Internet Explorer 10+支持为伪元素添加动画效果。 

###注意 

Internet Explorer不支持对伪元素使用`z-index`。

###深度阅读 

* [CSS生成的内容，自动编号和列表](http://www.w3.org/TR/CSS2/generate.html#before-after-content) 
* [第三层级CSS选择器](http://dev.w3.org/csswg/selectors3/#gen-content) 
* [学习使用CSS中:before和:after伪元素](http://coding.smashingmagazine.com/2011/07/13/learning-to-use-the-before-and-after-pseudo-elements-in-css/) 

###相关文章

* content
* ::selection
* [::after](http://lesrecord.com/2015/07/02/CSS-reference-after/)
* ::placeholder
* [::first-letter](http://lesrecord.com/2015/07/04/CSS-reference-first-letter/)
* ::first-line
* attr()


