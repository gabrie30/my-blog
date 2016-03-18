---
layout: post
title: "Splats for Strings"
excerpt: "Ruby trick!"
tags: [Ruby, Tricks]
comments: true
---

My last post I wrote about how you can use “&” to turn a block to a proc, and vis versa. This is handy because blocks are not objects you can’t store them in a variable to pass around. Splat does something similar to “&” but for arrays and strings. 

```
a = ["a", "b", "c", "d"]
def something( a ) 
   p *a
end

something(a)
```

Here the splat operator turns the array into a list, when its an argument in the something method. 

Doing this the opposite way, the splat can used to accept an unknown amount arguments into a method, storing them in an array once inside the method.

```
a = ["a", "b", "c", "d"]
def something(*a)
   p a
end
something("I", "could", "use", "more")
```

This will return ["I", "could", "use", "more"]