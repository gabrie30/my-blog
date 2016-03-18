---
layout: post
title: "Validations in Rails"
excerpt: "Keep your database clean"
tags: [Rails]
comments: true
---

Validations in rails are an important aspect of keeping your database clean, which ultimately improves performance of your app. There are plenty of useful validations that come standard on rails that you probably have used a thousand times. But what happens when you need to validate for something very specific? This is where custom validations come in handy. A custom validation is basically a helper method that lets you define the terms of what kinds of data should be allowed passed the model and into the database.

You set these methods up by calling validate followed by the name of the method that will test the incoming data.

```
class Test < ActiveRecord::Base

  validate my_method_for_validation

  private

  def my_method_for_validation
    if foo > bar
      errors[ :foobar ] < “Must be less than foo!”
    end
  end
end
```


Now we not only have our own custom validation but we also are able to pass an error message back to the user to indicate the problem with their submitted data. We do this by using the errors hash. The only requirement to get this hash to work is that your model needs to inherit from active record base.