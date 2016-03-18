---
layout: post
title: "Single Responsibilty in OOP"
excerpt: "With methods"
tags: [Ruby]
comments: true
---

I'm going to keep this short and sweet. Methods should be responsible for doing one specific thing. Sometimes in order to accomplish something specific it will require more than one step. When you have a method that requires more than one step don’t try to write each step inside the method. Instead factor it out and create a separate method for each step. One side effect of doing something like this is that other instance methods can use them if needed, thus keeping your code DRY.