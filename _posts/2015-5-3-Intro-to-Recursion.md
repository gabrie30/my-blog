---
layout: post
title: "Introduction to Recursion"
excerpt: "My first thoughts about recursion"
tags: [Ruby, Recursion]
comments: true
---


```
def inserting_obligatory_recursive_joke_here
    inserting_obligatory_recursive_joke_here
end
```

I want to show you two different kinds of recursive problems -- those that need to recurse back up the call stack and those that do not. The problems that don’t need to recurse back up are the easiest to understand so lets start there.

In this example we want to know if our target number is included in an array of digits and we need to solve it recursively. Our strategy will be to test every element in the array, if it matches our target number we can return true, if we get to the end of the array and it hasn’t returned true, it means our number is not in the array so we will return false.

```
def recurse(arr, target)
   if arr.first == target
       return true
   elsif arr.empty?
       return false
   end
   recurse( arr[1..-1], target )
end
recurse([1,2,3,4,5], 5)
```

Again this method does not recurse back up the call stack because we will either hit our target and return, or we will empty our array in which case it will return nil.


The other type of recursion problem does require us to recurse back up the call stack to solve the problem. In this case we assign a base case which will set the last calls value and continue up the chain. Here we are going to look for the nth factorial.


```
def recurse_up(n)
   return 1 if n == 1
   recurse_up(n-1) * n   <--   # when n == 1 recurse_up( n -1 ) becomes 1,
end                                      # this is why we are able to multiply it by n
recurse_up(4)                      
```

Here is a slightly more advanced way of doing the same problem. This time instead of our base case returning an int, we’ll return an array, from which we will add to as we recurse back up the stack. This way our output will be an array of all the factorials up to the nth factorial.

```
def recurse_up(n)
   return [1] if n == 1
   rec_arr = recurse_up(n-1)
   rec_arr << rec_arr.last * (n-1)
end
recurse_up(6)
```

What happening is when we hit our base case the recurse_up(n-1) returns [1] and assigns it to rec_arr. The subsequent returns will use the last element in rec_arr multiply it by (n-1) and add it to the array which will be used in the next call up the stack.


If you prefer the first method of solving recursion -- creating a stack but not recursing back up -- you can look into tail recursion, which will return once the stack is built up. Don’t get too excited, Ruby is not optimized for tail recursion so there is no real performance increase. Other languages are optimized for this so its still worth learning!