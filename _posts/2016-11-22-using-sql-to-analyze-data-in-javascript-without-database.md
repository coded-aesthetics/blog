---
layout: post
title: Using SQL to analyze data in JavaScript without a database
---

<div class="message">
  Exploration of the possibility to use SQL syntax to analyze javascript data with the array methods map, reduce, filter and sort.
</div>

[View Demo Here](https://s3.eu-central-1.amazonaws.com/coded-aesthetics/demos/javascript-sql-data-analysis/index.html)

This is the elaboration of an idea I had in this blog post: 
[JavaScript Arrays - Map, Reduce and Filter]({{ site.baseurl }}{% post_url 2016-11-19-javascript-arrays-map-reduce-filter %}).

Take the following dataset listing countries and their respective population/GDP: 

{% highlight js %}
  let countries =
    [{"country":"Fiji","population":892145,"gdp":4386}, 
     {"country":"Suriname","population":542975,"gdp":4878},
     {"country":"UAE","population":9156963,"gdp":307293},
     {"country":"Angola","population":25021974,"gdp":102643},
     {"country":"Argentina","population":43416755,"gdp":529726},
     {"country":"Japan","population":126958000,"gdp":4123000},
     {"country":"Germany","population":81413145,"gdp":3356000},
     {"country":"USA","population":321418000,"gdp":16663000}];
{% endhighlight %}

Consider you want to find the average gdp of all countries with a population less than 10 million.   
Wouldn't it be nice to be able to do this using an SQL statement?

{% highlight sql %}
  SELECT avg(gdp) from countries where population < 10000000;
{% endhighlight %}

The idea is the following:
The map, reduce, sort and filter methods on JavaScript arrays can easily be mapped to select, where and order by in SQL.   

### WHERE <---> Filter

The WHERE statement thins out the rows of a tables.  
Just like Array.prototype.filter

{% highlight js %}
  let whereColumn = "population";
  let whereOperator = ">";
  let whereValue = 10000000;
  countries.filter((current) => {
    return eval(`current.${whereColumn} ${whereOperator} ${whereValue}`);
  });
{% endhighlight %}

### SELECT <---> Map

The SQL SELECT statement picks a subset of the table columns.   
Array.prototype.map can be used to do the same:

{% highlight js %}
  let selectField = "gdp";
  countries.map((current) => {
    return {[selectField]: current[selectField]};
  });
{% endhighlight %}

### ORDER BY <---> Sort

Using ORDER BY sorts the selected rows.   
Exactly like Array.prototype.sort:

{% highlight js %}
  let orderColumn = "country";
  let orderDirection = "desc"
  countries.sort((o1, o2) => {
    let field1 = o1[orderColumn];
    let field2 = o2[orderColumn];
    if (typeof field1 === 'number') {
      if (orderDir == 'asc') {
        return field1 - field2;
      } else {
        return field2 - field1;
      }
    }
    if (typeof field1 === 'string') {
      if (orderDir == 'asc') {
        return field1.localeCompare(field2);
      } else {
        return field2.localeCompare(field1);
      }
    }
  });
{% endhighlight %}

### Aggregation functions (like sum, avg etc.) <---> Reduce

The following SQL statement containing the 'sum' aggregation function can be implemented in JavaScript by using Array.prototype.reduce.

{% highlight sql %}
  SELECT sum(gdp) from countries
{% endhighlight %}

{% highlight js %}
  let functionParam = "gdp";
  countries.reduce((red, current) => {
    return current[functionParam] + red; 
  }, 0);
{% endhighlight %}

Pretty straight-forward, don't you think?   
Well these examples are simplified for brevity's sake, but they constitute a good starting point to dive into the implementation.  

### Implementation, Demo and Repository 

The implementation is based on the [SQLLite parser](http://codeschool.github.io/sqlite-parser/demo/) written by [Nick Wronski](https://github.com/nwronski) for Codeschool which parses SQL statements and generates an abstract syntax tree out of which the neccessary data can be extracted.
[You can find the repository here](https://github.com/coded-aesthetics/javascript-sql-data-analysis). 
Please note that this is highly experimental and to be considered a case study.    
If you would however like to use or build on this technique, feel free to do so.  

[View Demo Here](https://s3.eu-central-1.amazonaws.com/coded-aesthetics/demos/javascript-sql-data-analysis/index.html)

You can find [a nice collection of data to analyze](https://github.com/jdorfman/awesome-json-datasets) in this github repo by Justin Dorfman

Currently supported statements:
- select *  
- select column  
- select column1, column2  
- select sum(column)  
- select avg(column)  
- select min(column)  
- select max(column)  
- select count(*)  
- where column = 3
- where column = 'str'
- where column like 'A%' (begins with A)  
- where column like '%D' (ends with D)  
- where column like 'DA' (contains DA)  
- order by column asc  
- order by column desc  
  
since the where clause is eval'd you can do more advanced stuff e.g. on sub-objects in your dataset like:  
- where "arrColumn[0].subObj" = 'something'
- where "arrColumn.every((cur) => {return cur.val > 3;})" = 'true'

Note that due to the fact that sqllite columns are case insensitive **you have to put camelCase columns in quotation-marks**:  
Checking if a column is null only works like this: where "column == null" = 'true'

  
