---
layout: post
title: "How to Organize Code in Backbone"
excerpt: "Its not in the documentation!"
tags : [Backbone]
comments: true
---

## Code Organization in Backbone.js

One of the hardest thing for me to figure out with Backbone is how to organize my code. The philosophy of backbone is that there is no correct or incorret way. You are free to organize it however you wish. This leaves a lot up to the programmer and quite frankly if you're not experience with this sort of thing, can be absolutely overwhelming.

The way I've been starting to think about my oranization is thinking about how the DOM itself is organized. The DOM is essentially one large tree, with the root being the HTML tag. In most of my backbone apps this would be my index page. However inside the index page I will have several subviews, the even perhaps within a subview, I will have a subview of the subview. 

My index view's template will mostly have empty divs. I will then use the subviews to populate those divs. This pattern continues down the subview chain.

The only time I replace the contents of the DOM completely is when the user is being redirected to something like the about page. This type of manipulation would be done ony in the router.

Another aspect of code organization that has helped me out is fetching my collection before initializing the app. That way once the app loads I already have all of the models that are stored in the database. Another benefits is that I have access to all the models anywhere in the application. Typically I will store it in something like...MyAppName.Collections.myCollection, which I can then call collection methods on from anywhere in my application.

Thinking about how you should organize your code in backbone is fun since there are so many possibilies. I think the best way to figure out what works best for you is just to experiment. So remember to have fun!

If you have any tips, best practies, or resources please leave them in the comments below!