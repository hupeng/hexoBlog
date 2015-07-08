title: CSS reference—— ::selection
date: 2015-07-08 15:43:31
description: CSS参考 ::selection
tags: CSS
---

> 原文地址：[http://tympanus.net/codrops/css_reference/selection/](http://tympanus.net/codrops/css_reference/selection/)

###`::selection`是一中CSS伪元素，表示文档中被用户高亮的那部分内容。例如，用户通过鼠标或者其他的指针设备选择的页面上的一部分内容。

 {% img http://codropspz.tympanus.netdna-cdn.com/codrops/wp-content/uploads/2014/12/selection-default.png [title text [alt 选择内容]] %}

在绝大部分的浏览器，选择的内容默认会有一个蓝色的背景，通过`::selection`，你能改变那些效果，为了和全局样式或者页面主题相匹配。

只有一部分的CSS属性可以用于`::selection`，他们是：`color`，`background-color`，和`text-shadow`。

<!--more-->

也可以使用`background`复合属性来设置选区的样式。但是，不支持背景图片，会被忽略。所以`background`复合属性只能简单的用于定义背景颜色。

###备注

`::selection`伪元素在Lv3 CSS选择器中被引入，但是在它成为候选的推荐状态之前被移除了，目前不在CSS模型的标准当中。但是主流浏览器都实现了这个伪元素，并且可能一直保留。

###案例

下面的例子设置页面选择部分的前景色和背景色：

```css
::selection {
    background-color: #222;
    color: white;
}
```

下面的例子会设置引用快中高亮文本的前景色和背景色：

```css
blockquote::selection {
    background-color: #aaa;
    color: white;
}
```

###在线演示

看一看下面的示例：

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/JsnvwNcX/embed/result,html,css/" width="100%" height="550px"></iframe>

###浏览器兼容性

支持`::selection`伪元素的浏览器有：Chrome,  Safari, Opera, 和 Internet Explorer 9+。

Firefox需要带有`-moz-`前缀，也就是`::-moz-selection`。

`::selection`伪元素中只有Chrome, Safari, Opera, 和 Firefox支持`text-shadow`属性。

###相关文章

* [::before](http://lesrecord.com/2015/07/03/CSS-reference-before/)
* [::after](http://lesrecord.com/2015/07/02/CSS-reference-after/)
