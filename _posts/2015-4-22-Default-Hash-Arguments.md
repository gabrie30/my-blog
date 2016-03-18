---
layout: post
title: "Default Hash Arguments"
excerpt: "This pattern appears all over Rails"
tags: [Ruby, Rails Patterns]
comments: true
---

Here is a really handy way to create a hash with custom default values using #merge. Below is an example that lets you pass in zero, or all the key value pairs for a hash. If you dont have all the values, there is a default hash just inside the method that will plug any holes that you left in your hash.

The magic is in #merge. Whatever hash object you pass into #merge as an argument will take precedence. Meaning all the key value pairs that are in the #merge(argument) will be included in the returned hash. In the example below the values for the keys :second and :thrid took precedence over the default hash. However since there was  not a ;first being passed into the function, the default hash :first key was included in the return hash.

```ruby
def hash_merge( my_hash = { } )
 default_hash = {
   first: "Hello",
   second: "Mrs",
   third: "Robinson",
 }
 merged_hash = default_hash.merge( my_hash )
 p merged_hash.values.join(" ")
end
hash_merge( second: "Mr.", third: "Bond") 
#=> Hello Mr. Bond
```

One important thing to remember is that you can only pass one hash into a function and it must be the last argument passed. 