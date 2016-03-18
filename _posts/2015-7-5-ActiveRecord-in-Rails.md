---
layout: post
title: "ActiveRecord in Rails"
excerpt: "What is it?"
tags: [Rails, ActiveRecord]
comments: true
---

Active Record is another magical part of Rails. It provides an easy way to access the database and connects the your persistent data in meaningful ways. Active Record makes it easy to perform simple database queries. For example instead of using SQL to SELECT * FROM users LIMIT 1 you can simply do Users.first. Both will get you the same information, the later is much simpler and easy to read. Active Record is a powerful part of Rails that is worth understanding.