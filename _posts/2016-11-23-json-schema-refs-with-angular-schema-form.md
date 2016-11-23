---
layout: post
title: Getting $refs to work with angular-schema-form
---

<div class="message">
  Reusing schema definitions in angular-schema-form via the $ref identifier is not officially supported. <br> Here's how to get them to work anyway
</div>

### The problem

You have a set of values, which the user can enter in multiple forms throughout your application.  
For example you have a form in which the user can enter data about her city of birth as well as current city of residence.  

{% highlight js %}
PersonalDataModel.schema = {
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "firstName": {"type": "string"},
    "surName": {"type": "string"},
    ...
    "cityOfBirth": { 
      "type": "object",
      "properties": {
        "name": {"type": "string"},
        "zip": {"type": "string"},
        "country": {"type": "string"}
      }
    }
    "cityOfResidence": { 
     "type": "object",
      "properties": {
         "name": {"type": "string"},
         "zip": {"type": "string"},
         "country": {"type": "string"}
      }
    }
  }
}
{% endhighlight %}

This is an unnecessary repetition. It is better maintainable if you write a separate schema for your CityModel like so:

{% highlight js %}
CityModel.schema = {
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "name": {"type": "string"},
    "zip": {"type": "string"},
    "country": {"type": "string"}
  }
}
{% endhighlight %}
and include it in your PersonalDataModel.schema via the definitions 
property and provide a reference to it in both your cityOfBirth and cityOfResidence declaration.
{% highlight js %}
PersonalDataModel.schema = {
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "firstName": {"type": "string"},
    "surName": {"type": "string"},
    ...
    "cityOfBirth": { "$ref": "#/definitions/city" }
    "cityOfResidence": { "$ref": "#/definitions/city" }
  },
  "definitions": {
    "city": CityModel.schema
  }
}
{% endhighlight %}

**Unfortunately, resolving json-schema $refs is not supported by angular-json-forms out of the box**

### The solution

You have to include the [json-refs](https://github.com/whitlockjc/json-refs) library into your project.  
If you're using bower this can be accomplished by calling
{% highlight sh %}
bower install json-refs --save
{% endhighlight %}
and including the json-refs file into your build.

In the controller where you want to use your schema, you have to call
{% highlight js %}
JsonRefs.resolveRefs(PersonalDataModel.schema).then(
  function(resolvedSchema) {
    /* store the resolved schema 
       into a variable of your choice */
    vm.schema = resolvedSchema.resolved;
  }, 
  function(err) {
    throw err;
  }
);
{% endhighlight %}

Now you have the city schema in both PersonalDataModel.cityOfBirth and PersonalDataModel.cityOfResidence.