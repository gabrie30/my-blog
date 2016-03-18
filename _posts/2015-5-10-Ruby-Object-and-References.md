---
layout: post
title: "Ruby Object and References"
excerpt: "Looking at Ruby behavior"
tags: [Ruby]
comments: true
---

If you’re reading this you probably already know that just about everything in ruby is an object. But did you know that every object in ruby is referencing another object. This can be made clear with the following example

```
a = “this_is_a_string_object”
```
Here a is an object thats referencing an instance of the String class.

```
b = a
```

Now b is also referencing “this_is_a_string_object”

So when we modify a, we’re also modifying b.

```
a << “_really?”
p b #=> “this_is_a_string_object_really?”
```

However if we did a += “_really?”, the outcome would be different. Thats because when you use = you are reassigning the object, changing its object_id and thus anything that referenced its old object id.

Here is a particularly neat example of how we can use object references to our advantage. In this example we have a Board class that is initialized to an empty nested array that is n x n. What were going to do is set up the board with instances of the Tile class assigning its coordinates with x,y . As we iterate through the @grid array assigning its coordinates we will also include the grid. This way each tile will know the state of the board at any given time.

But wait, wouldn’t only the last tile object have the entire grid assigned when it gets created? This is where object references come in handy. Its true that as we iterate through the array the first instance of Tile will have an incomplete grid. However, grid is just a reference to the underlying object its pointing to. So as grid get updated through every iteration so does the grid variable that every instance of Tile holds. Every grid object is updated simultaneously because they are all referencing the same thing!

```
class Board
 def initialize(n)
   @grid = Array.new(n) { Array.new(n) }
   setup(n)
 end
 def setup(n)
   (0...n).each do | x |
     (0...n).each do | y |
         grid[ x ][ y ] = Tile.new( [ x , y ], @grid)
       end
     end
 end
 ```