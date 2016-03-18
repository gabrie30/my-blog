---
layout: post
title: "Error Handling in Ruby"
excerpt: "The basics"
tags: [Ruby, Errors]
comments: true
---


BEGIN - an optional parameter to begin the error handling block. If BEGIN is not explicit it will start from the beginning of the method

RESCUE - Executes if an error or exception is raised.

RETRY - Will continue to perform an operation if an error was raised

ENSURE - Will automatically run no matter if an error was raised or not. One example of when to use ensure, is to close a file that you’ve opened to prevent data loss.

END - Ends the error handling encapsulation.