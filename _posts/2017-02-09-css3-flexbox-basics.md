---
layout: post
title: CSS3 - Flexbox basics
---

<div class="message">
  Flexbox is a two-dimensional layout entity. It provides features like reordering of elements without changing the DOM,
  easy vertical centering and it let's you specify how elements are to be resized in case there is too much space or not enough space.
</div>

### What is a flexbox?

A flexbox is a two-dimensional layout entity. This means elements inside a flexbox, which are called **flex-items**, will be aligned after two axes: The **main-axis** and the **cross-axis**. By default they are aligned like this:

![flexbox default axis alignment]({{ site.url }}/assets/flexbox/flexbox-axis.jpg)

### How to make an element a Flexbox

Usually, when you have a list of divs, they will be vertically stacked on top of each other inside their container like so:

<p data-height="213" data-theme-id="0" data-slug-hash="qRJVmQ" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="qRJVmQ" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/qRJVmQ/">qRJVmQ</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

By putting the property `display:flex` on the container they align like this:

<p data-height="191" data-theme-id="0" data-slug-hash="zNmPEa" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="zNmPEa" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/zNmPEa/">zNmPEa</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

The flex-items are now aligned along the main-axis, which points from left to right by default.
Note that the flex-items don't take up the whole space of the flexbox along the main-axis.

### Flex direction

Through the property `flex-direction` you can change the direction and orientation of the main axis: The default is `flex-direction: row`.
By setting `flex-direction:column` the alignment of the axes looks like this:

![flexbox axis alignment flex-direction column]({{ site.url }}/assets/flexbox/flex-direction-column.jpg)

Other options are `flex-direction:row-reverse`
![flexbox axis alignment flex-direction column]({{ site.url }}/assets/flexbox/flex-direction-row-reverse.jpg)

and `flex-direction:column-reverse`
![flexbox axis alignment flex-direction column]({{ site.url }}/assets/flexbox/flex-direction-column-reverse.jpg)

which flip the direction of the respective main-axis.

### Flex-wrap or welcome to 2D

In the previous paragraphs, flex-items were not aligned two-dimensionally yet. This is because the flex-items did not take up the whole space of the main-axis.
So we give each flex-item a width of 100px so they exceed the space of the main axis:

<p data-height="174" data-theme-id="0" data-slug-hash="XpxVmO" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="XpxVmO" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/XpxVmO/">XpxVmO</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

But as you can see, the items don't wrap into the next row. To make this happen you need to set `flex-wrap:wrap` on the container.

<p data-height="187" data-theme-id="0" data-slug-hash="VPEyae" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="VPEyae" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/VPEyae/">VPEyae</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

This also works with flipped axes aka `flex-direction:column`

<p data-height="242" data-theme-id="0" data-slug-hash="XpxVdG" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="XpxVdG" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/XpxVdG/">XpxVdG</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

By setting `flex-wrap:wrap-reverse` the direction of the cross-axis is reversed, so that it points from right to left:

<p data-height="242" data-theme-id="0" data-slug-hash="ZLqvpV" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="ZLqvpV" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/ZLqvpV/">ZLqvpV</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

### Reordering of flex-items through flex order

The order of flex-items can be changed by assigning the order property to individual flex-items. By default the order property is 0.

<p data-height="187" data-theme-id="0" data-slug-hash="NdOXvY" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="NdOXvY" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/NdOXvY/">NdOXvY</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

The order property is a decimal value like the z-index:

<p data-height="265" data-theme-id="0" data-slug-hash="vgVppg" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="vgVppg" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/vgVppg/">vgVppg</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

Flex-items are now ordered according to the value of their order property.