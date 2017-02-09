---
layout: post
title: CSS3 - Flexbox - Flex-Basis, Flex-Grow, Flex-Shrink
---

<div class="message">
  Flexbox is a two-dimensional layout entity. It provides features like reordering of elements without changing the DOM,
  easy vertical centering and it let's you specify how elements are to be resized in case there is too much space or not enough space.
</div>

### Defining how flex-items should be resized when there is more than enough space

#### flex-grow

We start with this example:
<p data-height="265" data-theme-id="0" data-slug-hash="xgyQBM" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="xgyQBM" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/xgyQBM/">xgyQBM</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
Here, all the flex-items use just as much space as they need (`width:auto`).
`flex-grow` is assigned to the flex-items and gets a decimal value.
Here we assign `flex-grow:1` to all items but box2, which gets `flex-grow:2`:
<p data-height="265" data-theme-id="0" data-slug-hash="dNgQQB" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="dNgQQB" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/dNgQQB/">dNgQQB</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
This results in box2 being twice as large as the other boxes.
Flex-grow can have arbitrary values greater or equal to zero:
<p data-height="265" data-theme-id="0" data-slug-hash="dNgQxb" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="dNgQxb" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/dNgQxb/">dNgQxb</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
When we only assign flex-grow to one flex-item, it chews up all the extra space and the other ones stay at `width:auto`
<p data-height="265" data-theme-id="0" data-slug-hash="ZLqVEj" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="ZLqVEj" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/ZLqVEj/">ZLqVEj</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
This is because flex-grow is 0 by default.

#### flex-basis

The resizing behaviour changes when we introduce `flex-basis`. This property states how big the flex-items should ideally be.
Setting flex-basis without flex-grow is the same as if we were setting the width (with horizontal main axis).
<p data-height="265" data-theme-id="0" data-slug-hash="JEmwdQ" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="JEmwdQ" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/JEmwdQ/">JEmwdQ</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
But if we set flex-grow now, only the extra space that is available when flex-items have their ideal size is up for distribution.
In this example the flexbox has a width of 300px and both flex-items have a flex-basis of 100px making them 200px wide (ideally).
So the extra space that can be distributed is 100px wide.
<p data-height="265" data-theme-id="0" data-slug-hash="EZdGyJ" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="EZdGyJ" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/EZdGyJ/">EZdGyJ</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
Here box1 gets three times more of the extra space (75px) than box2 (25px). So the extra space (100px) is distributed in the ratio 3:1.

#### flex-shrink

`flex-shrink` only makes sense, when a flex-basis is set.
It then signifies how much space a flex-item should give up (compared to the others), when there is less space than is ideal.
In this example everything is as in the previous ones, but now we don't have enough space, as the flexbox only is 100px wide (200px would be ideal).
So we lack 100px of space. Setting `flex-shrink:3` on box1 and `flex-shrink:1` on box2 results in box1 giving up 3 times more space (75px) than box2 (25px).
So box1 is 25px wide and box2 is 75px wide.
<p data-height="265" data-theme-id="0" data-slug-hash="apRPGb" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="apRPGb" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/apRPGb/">apRPGb</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

#### flex

The property flex is a shorthand that sets both flex-grow and flex-shrink to the same value
