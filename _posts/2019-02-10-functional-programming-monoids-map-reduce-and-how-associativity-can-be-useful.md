---
layout: post
title: Functional programming - Monoids or what can associativity do for you?!
---

<div class="message">
  Since functional programming is based on abstract mathematical concepts, one thing is often hard to see:
  How is this useful?!
  or
  When do I get my reward?!
</div>

### The problem

Imagine you have a large array you want to aggregate (read: reduce) to one value, but computation is quite expensive and takes a lot of time. How can you make things faster?

Right, run things in parallel.

So, in our case this means you split the array and compute the aggregate of each part in a separate thread like this:

[reduce(1..r), reduce(r+1, s), reduce(s+1, t)]

Now you end up with an array of 3 elements that needs to be reduced itself to get your result.

There are a few rules, though, in order for this to work.

1. Reduce needs to put out an object of the same type as the individual members of the original array
2. Our reduction function needs to allow this kind of partition and still return the right result
3. Should we encounter an empty array, the reduction function still needs to return a suitable value.

First, let's make things a bit clearer by looking at a real world example. Our array looks like this:
const a = [1,2,3,4,5,6,7,8];

We want to generate the sum of the array.

Of course, in this case, parallel processing does not really make sense. This is just an example, that is easy to understand.

Remember, that a reduction function is a binary function, that combines the result of the last reduction (or the starting value) with the current array member.

const reducer = (acc, cur) => acc + cur;
a.reduce(reducer, 0); // 36

Essentially, what we are computing is (1 + 2 + 3 + 4 + 5 + 6 + 7 + 8)

Our parallel example would look like this:

const a1 = a.slice(0, 4);
const a2 = a.slice(4);

[a1.reduce(reducer, 0), a2.reduce(reducer, 0)]


Rule one means we need an function, that combines any two members of a certain type to a third member of this type.
Rule two means that this operation needs to be associative.
Rule three means that a neutral element needs to exists for the type.

### Enter mathematics

The first rule means we need the
Defining a CSS grid is done by assiging the `display:grid` or `display:inline-grid`  property to the container element.
Each of the child elements that are to be layouted then gets a grid-identifier that we'll use to place them. This is done using the `grid-area` CSS property.

So, this is the html for our grid:

{% highlight html %}
<div class="container">
  <header class="header-section">
    header
  </header>
  <section class="section-1">
    section-1
  </section>
  <section class="section-2">
    section-2
  </section>
  <aside class="aside-1">
    aside-1
  </aside>
  <footer class="footer-section">
    footer
  </footer>
</div>
{% endhighlight %}

Note that these elements are not it the order that can be seen in the layout screenshots above. This is because element order can be set, when defining the grid (just like with flexbox order)
On the css side we give each of the children a unique identifier through `grid-area`:

{% highlight css %}
.header-section {
  grid-area: header;
}
.section-1 {
  grid-area: section-one;
}
.section-2 {
  grid-area: section-two;
}
.aside-1 {
  grid-area: aside-one;
}
.footer-section {
  grid-area: footer;
}
{% endhighlight %}

### grid-template-areas

The layout can then be done via the `grid-template-areas` property:

{% highlight css %}
.container {
  grid-template-areas:
    "header"
    "aside-one"
    "section-one"
    "section-two"
    "footer"
}
{% endhighlight %}

This sets a five row, one column layout and leads to this:

![low width layout]({{ site.url }}/assets/css-grid/css-grid-low-width.png)

For the high width version we define a media query like so:
{% highlight css %}
@media (min-width:600px) {
  .container {
    grid-template-areas:
      "header      header"
      "section-one section-two"
      "aside-one   section-two"
      "footer      footer"
  }
}
{% endhighlight %}

This defines a four row, two column layout. Note how section-two spans one column and two rows, and footer and header each span two columns and one row.

![MusicCookie]({{ site.url }}/assets/css-grid/css-grid-high-width.png)