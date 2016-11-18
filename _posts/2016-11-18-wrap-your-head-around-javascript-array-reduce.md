---
layout: post
title: Wrap your head around JavaScript Array.prototype.reduce
---

<div class="message">
  The array.reduce function let's you iterate over its content and boil it down to a single value.
</div>

Consider we have the following array:

{% highlight js %}

let arr = [3, 7, 9, 13];

{% endhighlight %}

and we want to calculate the sum of all its elements.
The traditional (iterative) way would look like this:

{% highlight js %}
var sum = 0;
for (var i = 0; i < arr.length; i++) {
    sum += arr[i];
}
{% endhighlight %}

With Array.reduce we can condens this into a one-liner:

{% highlight js %}
let sum = arr.reduce(reducer);
{% endhighlight %}

With reducer being defined as follows:

{% highlight js %}
function reducer(reductionSoFar, currentArrayElement, index)  {
    return reductionSoFar + currentArrayElement;
}
{% endhighlight %}

Take a look at each iteration-step and what is passed to the reducer function:

Here is our array again:

[<span class="cred">3</span>, <span class="cgreen">7</span>, <span class="corange">9</span>, <span class="cblue">13</span>]

<table>
<thead>
<tr>
<td>Step #</td>
<td>reductionSoFar</td>
<td>currentArrayElement</td>
<td>index</td>
<td>reduce function output:</td>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td><span class="cred">3</span></td>
<td><span class="cgreen">7</span></td>
<td>1</td>
<td>3 + 7 = <strong>10</strong></td>
</tr>
<tr>
<td>2</td>
<td><strong>10</strong></td>
<td><span class="corange">9</span></td>
<td>2</td>
<td>10 + 9 = <strong>19</strong></td>
</tr>
<tr>
<td>3</td>
<td><strong>19</strong></td>
<td><span class="cblue">13</span></td>
<td>3</td>
<td>19 + 13 = 32</td>
</tr>
</tbody>
</table>
= 32   

Note that in each step, the reductionSoFar variable is assigned the return value of the reducer function and it is is initialized with the first element of the array.


You can pass an optional second argument to the array.reduce function, that serves as initialization of the reductionSoFar variable.
{% highlight js %}
arr.reduce(reducer, startValue);
{% endhighlight %}

Consider we'd pass 10 as second argument like so:     
    
arr.reduce(reducer, <span class="cviolet">10</span>);    

our iterations would now look like this:    
[<span class="cred">3</span>, <span class="cgreen">7</span>, <span class="corange">9</span>, <span class="cblue">13</span>]  
<table>
<thead>
<tr>
<td>Step #</td>
<td>reductionSoFar</td>
<td>currentArrayElement</td>
<td>index</td>
<td>reduce function output:</td>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td><span class="cviolet">10</span></td>
<td><span class="cred">3</span></td>
<td>0</td>
<td>10 + 3 = <strong>13</strong></td>
</tr>
<tr>
<td>2</td>
<td><strong>13</strong></td>
<td><span class="cgreen">7</span></td>
<td>1</td>
<td>13 + 7 = <strong>20</strong></td>
</tr>
<tr>
<td>2</td>
<td><strong>20</strong></td>
<td><span class="corange">9</span></td>
<td>2</td>
<td>20 + 9 = <strong>29</strong></td>
</tr>
<tr>
<td>3</td>
<td><strong>29</strong></td>
<td><span class="cblue">13</span></td>
<td>3</td>
<td>29 + 13 = 42</td>
</tr>
</tbody>
</table>
= 42  

The only difference being, that the first value of reductionSoFar now is 10 and the function is called four times starting with arr[0] as currentArrayElement.