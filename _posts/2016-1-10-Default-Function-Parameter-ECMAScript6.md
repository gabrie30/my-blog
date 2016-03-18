---
layout: post
title: "Pigeonhole Principle"
excerpt: "What is the Pigeonhole Principle and new JavaScript goodies"
tags: [JavaScript, Ruby, Algorithms]
comments: true
---

### Pigeonhole Principle

I'm going to try to explain the Pidgeonhole Principle using this example, but it might be easier just to look it up at Wikipedia. The TLDR; is something like this. If you have n number of openings (for the pigeon to fit inside), and p number of pigeons, if p > n, then its guarunteed that in one of the openings you will have to fit at least 2 pigeons. Seems pretty logical and can be applied algorithmically.

Given an array arr of n unique non-negative integers, how can you find a non-negative integer that is not in the array?

The easiest way to demonstrate this principal at work is initialize an array, which in Ruby, by default will have non existant values set to nil. Say we have the original array arr = [1,2,4,0,7]. To solve this problem you will create a new array, call it my_arr and iterate over each element of arr taking its value and mapping it to the corresponding index of my_arr. Let me just show you and it should make sense - my_arr = [0,1,2,nil,4,nil,nil,7] now you just scan my_arr for a nil value and the index of that nil value is not in the original arr.  I'm not sure this answer is completely satisfying, because if you have a couple of very large numbers you are creating a very memory intense array. However, it is a good demonstration of the pigeonhole principal at work, after each iteration of arr you are squeezing or "pigeonholeing(sp?)" the numbers that are not in arr.

### Function Parameters in JavaScript

New in ECMAScript6 is the ability to give your functions default parameters. This is a very common thing to do in Ruby, but I was working on some older JavaScript and was wondering how I could do it if this feature wasn't available.

```

function example(a,b) {
  b = typeOf b != 'undefined' ? b : 10

  return a * b //=> 50
}

example(5);
```

In this case you can set be to either what was passed in or the defualt value, in this case 10.  Thankfully in the newest version of javascript you can assign them much more easily, like conventional Ruby.

