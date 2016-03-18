---
layout: post
title: "Using BCrypt in Rails"
excerpt: "BCrypt for passwords"
tags: [Rails]
comments: true
---

## The Wonders of BCrypt ##

If you are tinkering around with creating your own authenticaion BCrypt is a wonderful gem to use for the job. Although I would reccomend that if you are building something is not for learning purposes that you stick with one of the numerous auth gems that are tried and true.

That being said if you are still looking for the rush tha comes along with building your own auth lets go over how to use BCrypt.

First things first, lets install the gem, which can be a little bit tricky.

```ruby
gem 'bcrypt-ruby', require: 'bcrypt'
```

There are a few handy methods that will accomplish mostly what we want.

```ruby
bc_obj = BCrypt::Password.create(“actualPassword123”)
```

The nice thing about BCrypt is that the password digest will be salted for us...Our users can thank us later!

This creates a password digest object that we can save to the database, and also call other BCrypt methods on.

This is an important point and one that can easily trip you up. When you save this object to the database, it will be saved as a string. So, when you fetch a users password digest for authentication, you cannot call methods on it. So what you need to do is turn the string back into a BCrypt object. Heres how...

```ruby
bc_obj = BCrypt::Password.new(password_digest)
```

Now you're back to a BCrypt object! Now that we have an object we can call methods on it. Most likely you are going to want to use the password that a user submits to a login form. To see if the password they entered is the same as the password in the database you can use 

```ruby
(bc_obj).is_password?("password-user-entered-in-form")
```

This will return true or false depending on if the passwords match.
