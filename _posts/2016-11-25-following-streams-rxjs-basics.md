---
layout: post
title: Following Streams - RxJs Basics
---

<div class="message">
  RxJS lets you handle streams of data like arrays, but with data coming in over time. 
  What is to be done with this data is described when the stream is declared.
</div>

### What are streams?

The answer is quite simple: Anything that produces data over time.   
For example: 
- all click-events on a DOM-element that a user makes while on a page. 
- the events emitted periodically by a setInterval() call
- callbacks from promises that return data aquired by ajax calls to an api
- keypresses in an input field

### How to set up streams?  

Streams are abstracted to Observables in RxJS and declared by calling for example
{% highlight js %}
let clickStream = 
  Rx.Observable.fromEvent(document.body, 'click');
{% endhighlight %}
This catches all click events on the document.body element of a page.
{% highlight js %}
let intervalStream = 
  Rx.Observable.interval(1000);
{% endhighlight %}
Will catch all events that are produced by a call to setInterval(function, 1000);

### What can I do with these streams?

You subscribe to them and get the data they yielded delivered to a function like this:
{% highlight js %}
clickStream.subscribe((evt) => {
  console.log(evt.pageX, evt.pageY)
});
{% endhighlight %}

### Well this does not do much...
 
You're right. That is because we did not declare what is to be done with the stream's data at declaration time.   
Look at this example:  
{% highlight js %}
let clickStream = 
  Rx.Observable.fromEvent(document.body, 'click')
    .bufferTime(1000)
    .map( arr => arr.length );
{% endhighlight %}
This will yield the number of clicks per second...   
**But How?**   
You can read the above declaration like a processing chain the data passes through.   
First Rx.Observable.fromEvent(document.body, 'click') will emit click events.   
The bufferTime function will collect (buffer) those for 1000ms and store them in an array.   
After the 1000ms are over this array is passed on to the function inside of map.   
Which in turn returns the length of that array i.e. the number of click(event)s.   
And the output of this chain is then yielded to all subscriber functions.  

### To sum this up

RxJs enables you to write readable, asynchroneous code, because the whole data-flow must be described during declaration time.