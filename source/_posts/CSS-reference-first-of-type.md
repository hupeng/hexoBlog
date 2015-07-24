title: :first-of-type | CSS reference
date: 2015-07-24 15:30:56
description: CSS参考 :first-of-type
tags: CSS
---

> 原文链接：[http://tympanus.net/codrops/css_reference/first-of-type/](http://tympanus.net/codrops/css_reference/first-of-type/)

###`:first-of-type`是一种伪类选择器，如果某个元素在其父元素一系列子元素当中，是这个类型元素的第一个元素，那么`:first-of-type`就能匹配它。

换句话说，`:first-of-type`会匹配父元素当中第一次出现的元素。例如，下面的规则会选择`.container`当中第一个段落，并为其设定样式。

```html
<article>
    <h1>Article Title</h1>
    <p>
        First paragraph.
    </p>
    <p>
        Second paragraph.
    </p>
    <!-- .... -->
</article>
```

<!--more-->

```css
p:first-of-type {
    font-size: 1.5em;
}
```

###备注

`:first-of-type`和`:first-child`选择器有点类似，但是会比后者更具体。`:first-of-type`会选择上面例子中的第一段，无论是否为`article`的第一个子元素，但是`:first-child`则用于选择那些仅为其父元素第一个子元素的元素，因此：

```css
p:first-child {
    font-size: 1.5em;
}
```

将不会选择上述例子中的任何段落，因为不是其父元素的第一个子元素。你可以在`:first-child`文章中获得更多信息。

就像其他伪类一样，`:first-of-type`伪类也能和其他选择器一起链式使用，例如`:hover`，如果想为选择的元素提供一个悬浮样式的话。也可以和`::before`，`::after`伪元素一起使用，参考下面的案例和在线演示。

###案例

假设有下面这段HTML：

```html
<div class="container">
    <h1>Title</h1>
    <nav>
        <ul>
            <li>First Item</li>
            <li>Second Item</li>
            <li>Third Item</li>
            <li>Fourth Item</li>
        </ul>
    </nav>
    <article>
        <h2>Title</h2>
        <p>
            Lorem Ipsum... <a href="#">Link</a>... <a href="#">another Link</a>
        </p>
        <p>
            Lorem Ipsum...
        </p>
    </article>

    <article>
        <h2>Title</h2>
        <p>
            Lorem Ipsum...
        </p>
        <p>
            Lorem Ipsum
        </p>
    </article>
</div>
```

下面的规则会匹配上面`.container`中的第一个`article`：

```css
article:first-of-type {
    background-color: #eee;
    border: 1px solid #ddd;
}
```

下面的规则会匹配其父元素的子元素列表中第一个出现的段落：

```css
p:first-of-type {
    font-weight: bold;
}
```

下面的规则会选择父元素当中第一个出现的链接，并用伪元素打印出的链接的`href`属性，用括号包裹，放置在右边：

```css
a:first-of-type {
    color: deepPink;
}

a:first-of-type::after {
    content: "(" attr(href) ")";
    color: deepPink;
}
```

可以在下面看到在线演示。

###在线演示

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/nh3EEl6x/embed/result,html,css/" width="100%" height="330px"></iframe>

###浏览器兼容性

支持`:first-of-type`的浏览器有：Chrome, Firefox, Safari, Opera 9.5+, Internet Explorer 9+, 以及 Android 和 iOS。

###深度阅读

* [CSS Selectors Level 3](http://dev.w3.org/csswg/selectors3/#first-of-type-pseudo)

###相关文章

* :last-of-type
* :nth-of-type()
* :nth-last-of-type()
