---
layout: post
title: JavaScript Arrays Map, Reduce and Filter
---

<div class="message">
  Map, Reduce and Filter provide functional ways to manipulate and analyze JavaScript arrays.
</div>

Consider the following array that lists population and GDP (in millions) of various countries:

{% highlight js %}

let arr = [
  {country: "Fiji", population:892145, gdp: 4386},
  {country: "Suriname", population:542975, gdp: 4878},
  {country: "UAE", population:9156963, gdp: 307293},
  {country: "Angola", population:25021974, gdp: 102643},
  {country: "Argentina", population:43416755, gdp: 529726},
  {country: "Japan", population:126958000, gdp: 4123000},
  {country: "Germany", population:81413145, gdp: 3356000},
  {country: "USA", population:321418000, gdp: 16663000},
];

{% endhighlight %}

What if you wanted to calculate the combined GDP of all countries with a population less than 10 million?
The iterative approach would look something like this:

{% highlight js %}

let sumGDP = 0;
for (var i = arr.length; i--;) {
  if (arr[i].population < 10000000) {
    sumGDP += arr[i].gdp;
  }
}

{% endhighlight %}

With the fuctional approach using map, reduce and filter you can write the whole thing in one line:

{% highlight js %}

let sumGDP = arr.filter((cur) => cur.population < 10000000)
                .map((cur) => cur.gdp)
                .reduce((red, cur) => red + cur);

{% endhighlight %}
<div style="text-align:right;margin-top:-1em;width:100%;font-size:80%;padding-right:3em;"> <a href="https://jsfiddle.net/zrb3w29k/" target="_ext" style="">JsFiddle</a></div>    

So, what is going on here? 

#### Filter phase

First we use the Array.prototype.filter to extract all countries with population less than 10 million.
The function you pass to the filter method is expected to return true/false. 
Returning true will put the current element in the output-array while returning false will leave it out.
So this will leave us with:
{% highlight js %}
  [{"country":"Fiji", "population":892145, "gdp":4386},
   {"country":"Suriname", "population":542975, "gdp":4878},
   {"country":"UAE", "population":9156963, "gdp":307293}]
{% endhighlight %}
#### Map phase

We now use map to give us an array with only the gdp values of each country. 
Map will return an array of equal length to the original, but with altered entries.
Here we specify to leave everything out but the gdp value which gives us:
{% highlight js %}
[4386,
 4878,
 307293]
{% endhighlight %}
#### Reduce phase
In the last step we use reduce to calculate the cumulated value of all three entries. This leads to the endresult of:
{% highlight js %}
316557 millions
{% endhighlight %}

You can think of this in terms of an SQL statement: 
{% highlight sql %}
SELECT sum(gdp) from countries where population < 10000000;
{% endhighlight %}
with <span class="corange">SELECT</span> corresponding to the <span class="corange">map phase</span>, <span class="cblue">WHERE</span> corresponding to the <span class="cblue">filter phase</span> and the <span class="cgreen">summing up</span> corresponding to the <span class="cgreen">reduce phase</span>.   
Check out this <a href="http://sqlfiddle.com/#!9/db34ae/2" target="_ext">SQLFiddle</a> (yes, that really is a thing...) 

### Wrapping up

So, while this is probably not a good choice when you have to keep an eye on performance,  
it can greatly enhance readability and is much more versatile as you can plug in different functions in each of the phases to extract the data you want.