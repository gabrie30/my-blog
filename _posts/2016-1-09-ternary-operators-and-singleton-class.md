---
layout: post
title: "Ternary Operators and Singleton Class"
excerpt: "Chaining ternary opperators and the singleton class"
tags: [JavaScript, Ruby]
comments: true
---

### JavaScript

Recently I've been tinkering around with JavaScript and started looking more into the JQuery source code and one thing that immediately caught my eye is how often they chain ternary opporators. It comes up quite a bit, and is something I've never thought to do. I wouldn't say it reads more clearly so I don't understand the benefit of it yet but I'm thinking about using it in one of my projects.

### Ruby

One other tidbit, however in Ruby, that I've been seeing more of is the use of the Singleton class. Don't confuse the singleton class with the singleton design pattern. The singleton class is a class that every object has in Ruby. Its hidden from view but the parser will check it for methods as it goes up the inheritance chain. The singleton class is actually where all of the class variables are stored [here](https://stackoverflow.com/questions/212407/what-exactly-is-the-singleton-class-in-ruby) is a good stackoverflow explaination.