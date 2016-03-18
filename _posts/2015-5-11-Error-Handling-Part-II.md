---
layout: post
title: "Error Handling Part II"
excerpt: "More than just the methods"
tags: [Ruby, Errors]
comments: true
---


The first part of error handling is to create a new class that will handle an error you’d expect to arise in your program. When you create this class it will inheirit from StandardError which gives it all of the methods that are in standard error and you also have the ability to overwrite its methods.

```
class UserInputError < StandardError
end
```

This is really all you have to do to create a new error class, then you can create instance of the UserInputError class by calling UserInputError. If you raise an error with this class the default error will be the name of the class…UserInputError

If we want to override the default message all we have to do is change its initialize method.

```
class UserInputError < StandardError
    def initialize( msg = “The new default message for UserInputError” )
        super
    end
end
```

Since there are no arguments being passed into super, ruby will take the default method parameters and pass those automatically. Now when a UserInputError is raised we will use our custom made message instead of just returning the class name.

If you wanted you could create your methods inside your error class to hold your messages too.