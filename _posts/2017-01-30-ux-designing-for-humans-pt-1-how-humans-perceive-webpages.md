---
layout: post
title: UX - Designing for humans - pt 1 - How humans perceive webpages
---

<div class="message">
  To effectively design user interfaces, one needs to know about how humans visually perceive and pick up information.
</div>

### The field of view

![The human field of vision]({{ site.url }}/assets/ux-human-perception/fov.png)

The human field of vision is quite wide, but in the peripheral areas we are only able to perceive contrasts and light/dark. 
<div class="message">
  Actually, the only area where we can pick up detailed information are the 5 degrees right in the center.
</div>

### Saccades

So to get a detailed picture the eye needs to do several "jumps", which are called saccades.

![Saccades on a webpage form]({{ site.url }}/assets/ux-human-perception/saccades.png)

The above picture shows which parts of a form on a webpage were fixated by a test user, starting with the green circle and ending at the red one.   
What is interesting about this picture is, that there are certain areas that were not fixated (not noticed) at all.

<div class="message">
  Not everything you put on a webpage will get noticed by the users.
</div>

Here are three webpages that have been overlayed with a heatmap that shows where users used to look (red and yellow) and which parts they hardly even noticed (blue and grey).  

![Heatmap of eye fixations]({{ site.url }}/assets/ux-human-perception/eye-fixation-heatmap.png)

By analyzing the eye fixations on multiple webpages, researchers noticed that there is a pattern.
<div class="message">
The areas that are most looked at roughly represent an F-shape. The first line of information gets almost completely noticed, the second also, but after that users tend to only do a vertical scan of the beginnings of the lines to see if there might be something interesting but do not pay detailed attention.
</div>

### The wrap-up

Knowing this, you should:
- Leverage the read: Know that you have two lines (plus some) to get the most important information across and layout your content accordingly
- Ask yourself: Did they see it? when doing user testing
- Make important information & actions stand out