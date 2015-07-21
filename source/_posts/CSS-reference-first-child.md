title: :first-child | CSS reference 
date: 2015-07-21 17:07:24
description: CSS参考 :first-child
tags: CSS
---

> 原文链接：[http://tympanus.net/codrops/css_reference/first-child/](http://tympanus.net/codrops/css_reference/first-child/)

###`:first-child`是一种伪类，选择那些是其他元素的第一个子元素的目标元素。也就是说，如果某个元素是其父元素的第一个子元素，`:first-child`将会匹配它。

例如，假设有下下面一段HTML：

```html
<article>
    <p>
        Lorem Ipsum...
        </p>
    <p>
        Another Lorem Ipsum...
    </p>
</article>
```

<!--more-->

下面的代码会选择第一个段落，并在上面应用那些样式，这个例子中，就是父元素的第一个子元素。

```css
p:first-child {
    font-size: 1.5em;
}
```

上面的规则不会对下面例子中的段落起作用，因为它不是其父元素`.container`的第一个子元素。

```html
<div class="container">
    <h1>Heading</h1>
    <p>
        Lorem Ipsum...
    </p>
</div>
```

###备注

如果你想选择某个容器内的第一段，并为其设定样式，无论它是不是第一个子元素，那么你可以使用`:first-of-type`选择器，就像名字描述的那样，会选择该类型的第一个元素，而不管是不是其父元素的第一个子元素。例如，在上面的源码示例当中，`p:first-of-type`会选择标题之后的那个段落，但是不会匹配随后的其他别的段落。

和其他伪类一样，`:first-child`伪类也可以跟随其他选择器链式使用，如`:hover`，如果想为匹配的元素提供悬浮样式。也可以和伪元素一起链式使用，如`::before`和`::fater`。参考下面的案例和在线示例。

###案例

假设有下面一段HTML：

```html
<article>
    <h1>Understanding :first-child</h1>
    <p>
        This is the first paragraph, but it's not the first child of its parent.
    </p>
    <p>
        This is another paragraph. <span>This is a span inside the paragraph.</span>
    </p>
    <ul>
        <li>First list item</li>
        <li>Second list item</li>
        <li>Third list item</li>
    </ul>
</article>
```

下面的规则会匹配第二段中的`span`，因为它是其父元素中的第一个子元素。

```css
span:first-child {
    color: grey;
}
```

下面的规则会匹配上面无序列表中的第一个条目。

```css
li:first-child {
    text-decoration: underline;
    color: deepPink;
}
```

下面的规则匹配不到任何段落，因为没有一个是其父元素的第一个子元素。

```css
p:first-child {
    font-size: 1.5em;
}
```

下面的规则使用`::before`和`::after`伪元素将`span`用两个括号包裹起来。

```css
span:first-child::before {
    content: "(";
    color: deepPink;
}

span:first-child::after {
    content: ")";
    color: deepPink;
}
```

你可以在下一章节看到在线演示。

###在线演示

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/zaSPYYp7/embed/result,html,css/" width="100%" height="350px"></iframe>

###浏览器兼容性

支持`:first-child`伪类的浏览器有：Chrome, Firefox, Safari, Opera 9.5+, Internet Explorer 7+, 以及 Android 和 iOS。

###注意

如果元素是动态插入的，Internet Explorer 7不会更新样式。在Internet Explorer 8中，如果通过点击一个连接来动态插入元素，直到连接失去焦点后，第一个子元素的样式才会被应用。

###深度阅读

* [CSS Selectors Level 3](http://dev.w3.org/csswg/selectors3/#first-child-pseudo)

###相关文章

* :empty
* :nth-child()
* :last-child
* :nth-last-child()

