---
layout: post
title: "Lots of Blocks"
excerpt: "Looking at blocks in Ruby"
tags: [Ruby]
comments: true
---

Some of the most useful built in Ruby methods like #each, #map, and #select, all have one thing in common, they all except blocks. Lets take a look at a simple block in ruby.

```ruby
def say_hello
  yield
end

say_hello { puts ”hello” } #=> "hello”
```

What happens here is that when the yield keyword in the say_hello method is called it will run the { puts “hello” } block that was passed in. Resulting in the output of “hello”

The yield keyword can also take a parameter to pass into the block outside the function.

```ruby
def say_hello
  yield “hello there”
end

say_hello { | m | puts m } #=> “hello there”
```

This time the yield is passing “hello there” into m which is then being outputted to the screen with “puts m”

Cool right?

You can even call yield multiple times within the same function.

```ruby
def say_hello
  yield
  yield
end

say_hello { puts “hello” }

#=> hello
#=> hello
```

And lastly what if you forget provide a block to some method containing a yield? If you thought it would error, you’d be correct (more precisely it would be a LocalJumpError) unless you use the handy ruby method block_given?

```ruby
def say_hello
  yield if block_given?
  puts "Anyone there?"
end

say_hello #=> "Anyone there?"
```

Yes this methods function fits its name perfectly. It will only allow the yield to happen if a block is given in the first place, otherwise it will simply skip the yield and move on.