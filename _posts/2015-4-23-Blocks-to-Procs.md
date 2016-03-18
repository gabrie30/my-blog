---
layout: post
title: "Blocks to Procs"
excerpt: "Passing methods in Ruby, the basics"
tags: [Ruby]
comments: true
---


Something I found interesting about blocks in ruby is that they aren’t objects. The saying that everything in ruby is an object has been beaten into my head since day one, so to learn this was like finding out pigs actually can fly. So if blocks aren’t objects how can we pass them around? Thats where Procs come in. Procs are similar to blocks but are actually objects. You can create a proc by calling Proc.new and giving it a block

```
my_proc = Proc.new { puts “hello” } 
Since a proc is an object we can pass them into methods and invoke them with the call method.

def greet( prc )
  prc.call
end
my_proc = Proc.new { puts “hello” )
greet #=> “hello”
```

You can also pass an argument into the proc when you call it.

```
def greet(x, prc )
 prc.call(x)
end
my_proc = Proc.new { |x| puts "Hello #{x}" }
greet("there!", my_proc) #=> Hello there!
```

But I think the coolest thing about procs and blocks is that you can easily change between the two by using the &, which converts a proc into a block, and also converts a block into a proc.

Here we give a block to the count method.  However since blocks are not objects they cannot be used as arguments. So we turn the block into a proc by using &prc. But .each will not work wtih a proc object, its looking for a block so thats what we'll give it.  When we use the &prc a second time, it converts the proc back into a block so it can be used by each.

```
def count(&prc)
 [1,2,3].each(&prc)
end
count( ){ |x| print x } #=> 123
```