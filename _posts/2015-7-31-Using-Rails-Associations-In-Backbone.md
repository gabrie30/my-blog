---
layout: post
title: "Using Rails Associations in Backbone"
excerpt: "A work in progress"
tags: [Rails, Backbone]
comments: true
---

## Associations in Backbone.js

I wanted to go over how you can set up associations in your backbone app. This is an important aspect to know when using rails as an api for a backbone app. I couldn't find any good guides out there so I thought I'd write my own, hopefully this will help fill the void.

As a fair warning the example app I'm using was just for my own experimention and learning. I was making things up as I went, so the naming conventions are terrible. Moving on!

### Schema ###

![schema]({{ gabrie30.github.io }}/images/schema.png)

So Someitems have items and many Todos. Todos belong to Someitems. Great, now in the controller we can do something like... 

```
  @something = Someitem.first
```

```
  @something.todos
```

This will give us all of the todos for Someitem. Great, not much interesting here just basic rails associations. Now our goal is to get this data over to backbone. We're going to do that using JBuilder.

If check out this Railscast on [JBuilder](https://www.youtube.com/watch?v=52jERwqKNE0) if you're not familiar. It will allow you to use json in the rails views. Notice in the controller (line 21) how I commented out the normal way to render json. With JBuilder we can have more control over the JSON and we can use rails views as normal.

### Controller ###

![controller]({{ gabrie30.github.io }}/images/controller.png)

Now just create a views/todos/show.json.jbuilder and we can pull out whatever JSON we want.

```
json.(@something, :id, :item, :created_at, :updated_at)
```

```
json.todos(@todos, :id, :title, :created_at, :updated_at)
```

Here is the result of the JBuilder from above.

### Rendered JSON ###

![json]({{ gabrie30.github.io }}/images/json.png)

Now what we have to do is get this JSON into our backbone app. I'm sure there is a better way to do this so if you know, leave it in the comments below. 

The first thing I did was change the routes file so I can just use the something/1, to grab the something data, and something/1/todo to grab all of its todos.

###Routes###
![routes]({{ gabrie30.github.io }}/images/routes.png)

The models and collections are straightforward.

### Collections ###

-![todocollection]({{ gabrie30.github.io }}/images/todocollection.png)

The cool thing here is line 9. You can turn the url into a fucntion. That way all you need is the something id to access the todos for that specific id. We'll get the something id by passing a something in as an option when we initialize the collection. See the models section to make this more clear.

-![somethingcollection]({{ gabrie30.github.io }}/images/somethingcollection.png)

### Models ###

-![todomodel]({{ gabrie30.github.io }}/images/todomodel.png)

On line 4 we create a todos function. This will serve as our hook into a somethings todos. In rails we would write something.todos, in backbone we will write something.todos() where the todos() function will return a collection of todos that is specific to that something.

-![somethingmodel]({{ gabrie30.github.io }}/images/somethingmodel.png)

That is the basic gist of how to create associations in backbone. Hopefully this helps someone.
















