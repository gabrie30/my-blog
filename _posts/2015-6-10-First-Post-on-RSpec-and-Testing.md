---
layout: post
title: "RSpec and TDD"
excerpt: "Love to test!"
tags: [RSpec, Ruby, TDD]
comments: true
---

The most popular testing framework for ruby (according to google analytics) is rspec. If you’ve never done done TDD testing can seem daunting. However the purpose is to save you time in the long run, by building code that is more manageable. For instance if you are looking to add additional features your tests will help track down bugs or help catch them before a small mistake becomes unmanageable. 

When testing the Red, Green, Refactor is the name of the game. That means build a test, watch it fail (because there is no actual code), write the code, watch the tests turn green, then finally refactor!