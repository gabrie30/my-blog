---
layout: post
title: "Ruby Include vs Extend"
excerpt: "Whats the diff?"
tags: [Ruby]
comments: true
---

What is the difference between include and extend in Ruby? This is something that I've read a few times but forget shortly thereafter so I'm hoping this blog post will be enough for it to stick forever. 

The main difference from what I've read is that Include is for making methods in a module accessible inside a class as instance variables. So basically when you include a module all of the instances of that class will have access to those methods.

Extend however, makes those methods into Class methods. Meaning they are not available for the instances of that class, only for the class itself.

Let's just look at an example to make this more clear.

``` ruby

module Thing
  
  def things
    puts "These are all the things"
  end
end


class Thang
  include Thing
end


my_thang = Thang.new
my_thang.things #=> These are all the things

Thang.things #=> NoMethodError => Why? Because we're calling it as a class method but include turns the Thing methods into intance methods.


class Thung
  extend Thing
end

my_thing = Thung.new
my_thing.things #=> NoMethodError => Why? Because we're calling it as an instance method, but extend makes the Thing methods into Class methods.

Thung.things #=> These are all the things

```

Hopefully these examples clear things up.

TLDR: 
extend  => class methods
include => instance methods
