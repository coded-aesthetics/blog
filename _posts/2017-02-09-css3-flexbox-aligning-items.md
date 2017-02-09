---
layout: post
title: CSS3 - Flexbox - Aligning items
---

<div class="message">
  Flexbox is a two-dimensional layout entity. It provides features like reordering of elements without changing the DOM,
  easy vertical centering and it let's you specify how elements are to be resized in case there is too much space or not enough space.
</div>

### Aligning items along the main-axis with justify-content

`justify-content` sets how flex-items are to be **aligned along the main-axis** (which is left to right in these examples)

`justify-content:flex-start (default)`
<p data-height="171" data-theme-id="0" data-slug-hash="mRzpjM" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="mRzpjM" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/mRzpjM/">mRzpjM</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`justify-content:flex-end`
<p data-height="171" data-theme-id="0" data-slug-hash="bgmaxK" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="bgmaxK" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/bgmaxK/">bgmaxK</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`justify-content:center`
<p data-height="157" data-theme-id="0" data-slug-hash="GrYyYO" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="GrYyYO" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/GrYyYO/">GrYyYO</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`justify-content:space-between`
<p data-height="173" data-theme-id="0" data-slug-hash="qRJpQN" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="qRJpQN" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/qRJpQN/">qRJpQN</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`justify-content:space-around`
<p data-height="169" data-theme-id="0" data-slug-hash="NdOXEL" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="NdOXEL" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/NdOXEL/">NdOXEL</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

All this also works with flipped axes. Here is just one example:
<p data-height="272" data-theme-id="0" data-slug-hash="xgypMV" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="xgypMV" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/xgypMV/">xgypMV</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

### Aligning items along the cross-axis with align-items

`align-items` sets how flex-items are to be **aligned along the cross-axis** (which is top to bottom in these examples)

`align-items:stretch (default)`
<p data-height="265" data-theme-id="0" data-slug-hash="mRzpYp" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="mRzpYp" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/mRzpYp/">mRzpYp</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`align-items:center`
<p data-height="265" data-theme-id="0" data-slug-hash="PWyQoa" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="QdZQLo" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/QdZQLo/">QdZQLo</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
Which is exactly how you vertically align items with flexbox...

`align-items:flex-start`
<p data-height="265" data-theme-id="0" data-slug-hash="MJPrMN" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="MJPrMN" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/MJPrMN/">MJPrMN</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`align-items:flex-end`
<p data-height="265" data-theme-id="0" data-slug-hash="EZdQYK" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="EZdQYK" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/EZdQYK/">EZdQYK</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`align-items:baseline`
<p data-height="265" data-theme-id="0" data-slug-hash="bgmLdO" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="bgmLdO" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/bgmLdO/">bgmLdO</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
This aligns items so that the baseline of the contained texts are on one line.

### Aligning individual items with align-self

`align-self` is set on flex-items and overrides the align-content property that has been set on the flexbox.
<p data-height="228" data-theme-id="0" data-slug-hash="LxgQNL" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="LxgQNL" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/LxgQNL/">LxgQNL</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
In the above example, only box3 is aligned by align-items. All other boxes override this property by setting align-self.

### Align-content = justify-content for the cross-axis.
Settings `align-content` has the same effect as `justify-content`, but for the cross-axis instead of the main-axis.
This will only have an effect if there is any wrapping, so `flex-wrap:wrap(-reverse)` needs to be set.

`align-content:stretch (default)`
<p data-height="265" data-theme-id="0" data-slug-hash="egPVez" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="egPVez" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/egPVez/">egPVez</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`align-content:flex-start`
<p data-height="265" data-theme-id="0" data-slug-hash="oBaEEE" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="oBaEEE" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/oBaEEE/">oBaEEE</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`align-content:flex-end`
<p data-height="265" data-theme-id="0" data-slug-hash="jyeZzE" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="jyeZzE" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/jyeZzE/">jyeZzE</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`align-content:space-around`
<p data-height="232" data-theme-id="0" data-slug-hash="PWyQRV" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="PWyQRV" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/PWyQRV/">PWyQRV</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

`align-content:space-between`
<p data-height="234" data-theme-id="0" data-slug-hash="rjqJvW" data-default-tab="css,result" data-user="coded-aesthetics" data-embed-version="2" data-pen-title="rjqJvW" class="codepen">See the Pen <a href="http://codepen.io/coded-aesthetics/pen/rjqJvW/">rjqJvW</a> by Jan Reinsch (<a href="http://codepen.io/coded-aesthetics">@coded-aesthetics</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>