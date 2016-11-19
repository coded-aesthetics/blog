---
layout: post
title: ES6 generators, iterators and the yield statement
---

<div class="message">
  Think of generator functions as functions being able to have a lot of consecutive return values that can be iterated over.
</div>

Generator functions are declared by adding the * (asterisk) sign after the function statement:

{% highlight js %}

function* gen() { /* do things here */ };

{% endhighlight %}

They "return" values through the yield statement. Here is an example:

{% highlight js %}

function* gen() {
  yield 1;
  yield 4;
  yield 9;
}

{% endhighlight %}

You can harvest these values by using the iterator returned by the generator function and calling its next() method:

{% highlight js %}

let it = gen();
it.next(); /* returns {value: 1, done: false} */
it.next(); /* returns {value: 4, done: false} */
it.next(); /* returns {value: 9, done: false} */
it.next(); /* returns {value: undefined, done: true} */

{% endhighlight %}

So what yield really does is define iteration steps that are returned when the next() function is called.
Actually the execution of the generator function is halted until the next value is requested.    
So it's entirely possible to have an endless loop in you generator:

{% highlight js %}

function* gen() {
  let i = 0;
  while (1) {
     yield i++;
  }
}

{% endhighlight %}


You can iterate over the values with a for loop:

{% highlight js %}

for (let cur = it.next(); !cur.done; cur = it.next()) {
  console.log(cur.value);
}

{% endhighlight %}

or a do while loop:

{% highlight js %}

do {
  var cur = it.next();
  console.log(cur.value);
} while (!cur.done)

{% endhighlight %}

But the nicest way is using the for ... of method:

{% highlight js %}

for (let value of it) {
  console.log(value);
}

{% endhighlight %}

These will all output
{% highlight js %}
1
4
9
{% endhighlight %}

### Generators and arrays

Arrays are already iteratables so you can choose to yield the whole array or its individual entries.

{% highlight js %}
  function* gen1() { yield ["a", "b", "c"]; }
  function* gen2() { yield* ["a", "b", "c"]; }
{% endhighlight %}
  
Note the subtle difference: in gen2() the array's entries are yielded using yield*  

{% highlight js %}
  let it1 = gen1();
  for (let value of it1) {
    console.log(value);
  }
  /* will output 
     ["a", "b", "c"] 
  */
{% endhighlight %} 
{% highlight js %}
  let it2 = gen2();
  for (let value of it1) {
      console.log(value);
  }
  /* will output 
     "a" 
     "b"
     "c"
  */
  
{% endhighlight %}


Here are some examples of generator functions:

### Prime number generator

{% highlight js %}
function* prime() {
    var cur = 3; /** start with 3 **/
    yield 2; /** 2 is a prime **/
    let foundPrimes = [2]; /** store in array of found primes **/
    while(1) {
      let isPrime = true;
      /** loop through found primes **/
      for (var i = 0; i < foundPrimes.length; i++) {
        let p = foundPrimes[i];
        /** if the current value is divisible by one 
        of the found primes it is not prime itself **/
        if (cur % p === 0) {
          isPrime = false;
          break;
        }
        /** we need not go further than cur/2 **/
        if (p > cur/2) {
          break;
        }
      }
      /** if a prime was found yield it 
      and add it to the array of found primes **/
      if (isPrime) {
        yield cur;
        foundPrimes.push(cur);
      }
      ++cur;
    }
}
{% endhighlight %}
<div style="text-align:right;margin-top:-1em;width:100%;font-size:80%;padding-right:3em;"> <a href="https://jsfiddle.net/n3woqc73/" target="_ext" style="">JsFiddle</a></div>    

### Fibonacci numbers generator    

{% highlight js %}
/* generates 'count' fibonacci number pairs */
function* fib(count) {
   let a = 1;
   let b = 1;
   for (var i = count; i--;) {
     yield a;
     yield b;
     a = a+b;
     b = a+b;
   }
}
{% endhighlight %}
<div style="text-align:right;margin-top:-1em;width:100%;font-size:80%;padding-right:3em;"> <a href="https://jsfiddle.net/1mp8rvmx/" target="_ext" style="">JsFiddle</a></div>    


the first ten fibonacci numbers can be generated like so:

{% highlight js %}
let it = fib(5);
for (let value of it) {
  console.log(value);
}

/** will output:
1
1
2
3
5
8
13
21
34
55
**/
{% endhighlight %}