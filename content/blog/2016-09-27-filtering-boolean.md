---
comments: true
date: 2016-09-27T00:00:00Z
tags:
- JavaScript
- software craftmanship
title: Filtering out bad results with Boolean
type: '/blog/post'
layout: 'single'
---
While working through exercises on exercism.io, I found an interesting way to remove undefined results from the return array of a call to the map function.

When using the [filter function in JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter), the function will loop over each element in an array, apply a conditional test to an element; if the result of that test is true, the element will be outputted in a new array. It’s basically the map function but with an if statement.

I often look to filter because I started out programming with Ruby. The filter function, which for Ruby equates to the #select method, operates with the same logic: criteria to match and output elements that give a positive match in a new array, (I should be clearer here: all results elements into one array not each into a new array). I often reached for Ruby’s many mapping functions and therefore prefer to use similar mapping functions in JavaScript rather than for-loops. So, when I saw that you could use .filter(Boolean) instead of writing out a more traditional filter function with return keyword and conditional statement I was excited but confused how something like this could work.

**How it Works**

In JavaScript, [a Boolean is a JavaScript object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean). Per the MDN docs, it’s important to remember that a Boolean object is distinct and separate from a Boolean primitive value, like true or false. The best way to think of this is that a Boolean object has some value that is evaluated as a Boolean value, and not that a Boolean object is or becomes a Boolean value.

**new Boolean() vs true or false**

Taking it a step further, the MDN docs advise us not to use the new keyword with Boolean constructor function for the purpose of converting values into Boolean primitive values, (true or false). 

If we want to do that, it is ‘preferred’ to just call Boolean as a function:

    Boolean(value);

So since we just want to evaluate our elements as Boolean values, **_let’s focus on calling Boolean as a function._**

The way that the JavaScript filter function works is that we call it on a set of values in an array, and pass in a callback function to filter as an argument. Filter will take that callback function and apply it to each element it iterates over, attempting to return a value from the callback and outputting it into a new results array.

**We're going to use Boolean() as our callback function.**

In simpler terms: it takes a group of values one by one, tests that element with a conditional to see if it returns true and if it does, adds the element to a new array.

**Breaking it down**

So what happens when we have something like array.filter(Boolean) ?

    var array = [1, undefined, 2,3];

    return array.filter(Boolean);

In the above example we take each element and apply the Boolean function we saw above to it. So on the first pass, we take the first element, the number 1, and pass that as a value to Boolean().

    return Boolean(1);
    => true

This returns the Boolean primitive value of true. So what happens when we come across an element we don’t want in our result set, undefined?

    return Boolean(undefined);
    => false

The MDN docs tell us false is returned for any of the following values: 

**‘If value is omitted or is 0, -0, null, false, NaN, undefined, or the empty string (“”)...’**

And since filter only returns elements that evaluate to the Boolean value of true, using this will only return elements that we want.

**Where are my parentheses and parameter?**

You might be wondering why we don’t have parens after Boolean and a named parameter, like 

    array.filter(Boolean(element)); 

The answer is that we don’t need it.

The parens and arguments are implied. (And JS doesn’t throw an argument error like Ruby if you pass in the more or less than a defined number of arguments.) 

Try out executing Boolean in Node and see what the result is.

    Boolean
    => [Function: Boolean]

It returns a function called Boolean. Boolean, then, is a function that will be executed by filter. Filter is going to pass in the element it iterates over as an argument for us, we don't need to write anything out.

If we wanted to be more explicit to visualize, on the first pass on our array could be written as:

    function getEl () {
         return a[0];
    }

    Boolean(getEl());
    => true

First the inner functions are called and returned, in this case the getEl function. Then the outer functions are called, with the result that was returned by the inner functions, in this case the primitive value of 1. The result is the same as we got from our filter function.

And that’s how calling .filter() on a set of values with just the argument of Boolean can strip out undefined values.

**Craftsmanship: When is this right for me?**

I find that filtering after iterating over a set is kind of a bandaid on your code; it’s a code smell for missing a step in manipulating your input at an earlier time in your program, and a bit sloppy. 

**So what I’m saying is, my messy code led me to .filter(Boolean) but using it to clean up my array is not a great way to use it.** 

(I probably should have altered earlier code so that it removed unwanted results from my results array that I wanted to use .filter(Boolean) on. One way to do that is to use something like .match() to return only elements that match what I'm looking for.) 

But maybe you’re receiving input from somewhere else like an API where you can’t control or remove undefined and null elements from your array, using filter(Boolean) might be a nice way to sanitize your input with very little code.