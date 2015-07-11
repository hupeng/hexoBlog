title: :checked | CSS reference
date: 2015-07-11 10:25:24
description: CSS参考 :checked
tags: CSS
---

> 原文链接：[http://tympanus.net/codrops/css_reference/checked/](http://tympanus.net/codrops/css_reference/checked/)

###用户可以触发单选（`<input type="radio">`）和复选（`<input type="checkbox">`）元素的开关，当用户选择他们的时候，那些菜单项是`checked`状态。当某些元素切换至“开启”状态时候，`:checked`伪类将会起作用。

因此，`:checked`是用于匹配和设置那些被用户选择或者设置为“开启”状态的元素，他们是：复选框（`<input type="checkbox">`），单选框（`<input type="radio">`）以及选择项（`<select></select>`中的`<option></option>`）。

下面的单选和复选按钮能够被开启或者关闭。

<!--more-->

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/7T0I8SKv/embed/result,html,css/" width="100%" height="300px"></iframe>

如果作者明确设置了单选和复选条目的`checked`属性，或者选择项的`selected`属性，那么这些被设置的条目也能被`:checked`匹配到。

```html
<input type="radio" checked>
<input type="checkbox" checked>
<select name="options" id="list">
    <option value="Something" selected>This option is selected</option>
    <option value="Something-else">This one is not</option>
</select>
```

`:checked`伪类起初是用于这些元素，但是，用户当然也可以将状态切换至“关闭”状态，那么它就不会再起作用了。

###备注

用户可以切换单选和复选元素的状态，但是在有些时候，却是处在一个模棱两可的状态，既没有选择，也没有不选择。这可能归咎于该元素的属性，或者DOM操作。这种元素可以用`:indeterminate`伪类来设定样式。

设置`:checked`输入框标签的样式可以是非常有用的，能够使这些输入框更容易理解。任何有助于用户区分两种状态的不同点的视觉反馈都是有用的。例如，下面的例子使用一种代办事件列表的方法，来剔出那些被选择的复选框标签。

```html
<input type="checkbox"id="todo">
<label for="todo">Buy Milk</label>
```

```css
input[type = "checkbox"]:checked + label {
    text-decoration: line-through;
    color: grey;
}
```

切换下面示例中复选框的状态，查看不同的效果。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/93BVJUQq/embed/result,html,css/" width="100%" height="300px"></iframe>

另外，`:checked`伪类还可以用于模拟事件处理，仅仅通过CSS。 Ryan Seddon写了一篇非常有见解的文章，介绍如何设置自定义的单选和复选框的样式，描写一种很厉害的技巧：[用CSS自定义单选和复选框](http://www.thecssninja.com/css/custom-inputs-using-css)。在关于[CSS点击事件](http://tympanus.net/codrops/2012/12/17/css-click-events/)的文章中，你可以获得很多关于这种技术的信息。

###案例

下面的代码片段会为任何选中状态的输入框和选择项设定样式。

```css
:checked {
    color: green;
}
```

下面的例子，使用CSS属性选择器，分别为选中状态的复选框，单选框和选择项来设定样式。

```css
input[type="checkbox"]:checked {
    width: 20px;
    height: 20px;
}

input[type="radio"]:checked {
    color: green;
}

option:checked {
    background-color: blue;
    color: white;
}
```

###在线演示

切换下面示例中复选，单选和选择项到选中状态，查看`:check`样式。

<iframe src="http://tympanus.net/codrops-playground/SaraSoueidan/5WTDgopt/embed/result,html,css/" width="100%" height="300px"></iframe>

###浏览器兼容性

支持`:check`伪类的浏览器有：Chrome, Firefox, Safari, Opera 9+, Internet Explorer 9+, 以及 Android 和 iOS。

###深度阅读

* [CSS Selectors Level 3](http://www.w3.org/TR/css3-selectors/#checked)
* [HTML5 Specification](http://www.w3.org/TR/html5/disabled-elements.html#selector-checked)

###相关文章

* :hover
* :in-range
* :default
* :disabled
* :enabled
