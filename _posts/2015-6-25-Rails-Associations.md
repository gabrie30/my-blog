---
layout: post
title: "Rails Associations"
excerpt: "belongs_to and has_many"
tags: [Rails]
comments: true
---

Associations are a powerful concept in rails which give a lot more functionality to your applications. Two of the most used and related associations are the belongs_to and the has_many associations. Lets start off with an example to demonstrate what these associations represent.

In this example we’ll be using a swim club. If you are a member of the club you can use the pool whenever you want. In rails we could say that a member belongs_to the club. We could store each one of the members in our database, and they would all have some things in common that we can treat as rows in this database. Things like when they last visited, age, name, phone number, and pool id number to get them in. The ID number would be the users foreign_key. Something that is unique to them, that relates them back to the pool.

Likewise we could say that the club, has_many members. Each member has their own unique pool id (foreign_key) for which the pool is associated with its members. The pool could look up its users with the ID, or foreign key. In fact just by knowing the key, they can find out the users age, name, phone number, etc. It can also count all its members by querying the total number of ID’s in its database.

Associations are like the veins that let the data flow.
