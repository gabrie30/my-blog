---
layout: post
title: Basic jQuery
modified:
categories: 
excerpt:
tags: []
image:
  feature:
date: 2015-04-08T12:38:53-07:00
---

Objective: Click on a picture, the picture enlarges on the screen and has a darker background. When you click the picture again, the overlay disappears.

Implementation: I decided to implement this programatically. The best practice is to not add the overlay HTML directly into the DOM, but to create it on the fly with jQuery. The reason for this is because we dont want to bloat the DOM with elements that might never get displayed, such as if someone does not have JS turned on in their browswer. To implement the overlay in jq is pretty straightforward. First you will create a div element with a class of overlay. When a user clicks on the picture, you want to grab the path location of that picture and cache it away. The reason for this is because we'll want to use the path in our overlay element we're are constructing. We bing an event handler to the clicking of the image, that handler will be responsible for caching the path, creating an img tag with a src to the path that we've cached. Once all that is finished we will inject the overlay div into the body, with an absolute position. The position of absolute will take it out of the normal flow of element and we'll stretch the entire div across the screen. We can use a CSS property of color: rgba(0,0,0,0.7) this will add some transparency to the overlay, so its not completely blacked out. The image should be nexted inside the overlay and all we'll have to do is center it and maybe bring it down by 25% from the top to make it look good. Lastly we'll create an even handler when someone clicks on the newly created overlay element, to hide the element. If you want to get fancy you can use the jq effects to make the transition in and out a little easier on the eyes.

Objective: When a user views our page on a mobile device, we want the navigation at the top to collapse to a drop down menu.

Implementation: The best way to get this going is to use the html element of selected. Within the selected tag you will provide an option tag that will hold all of the different navigations you had at the top. I guess you could also do this using UL and LI, this would allow you to nest UL inside of UL's kinda like pressing start on windows 95. But for now lets just focus on the basic select and options tags. So we are going to want to start by making some media queries. When the users screen is below a certain limit we will hide the navigation and show the new dropdown navigation. Before showing the new navigation we have to build it ourselves. Again we don't want this new navigation hanging around in the DOM we will build it programatically. So we use the jQ each method to iterate over the old navigation grabbing each of the links or li's and appending them into the new options tags. We also want to check for which of the navigations is currently selected, because on the newly created navigation we want to build it identical as the old one. Meaning we need to find the currently selected nav in the old and make sure its on the same item in the new. Once we have that figured out and our new nav is built up, we hide the old one and show the new one. Then finally bind another event handler to a change in the options. Once that event is fired we will redirect the browser to the new location.

