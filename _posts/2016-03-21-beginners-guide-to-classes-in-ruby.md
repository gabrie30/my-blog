---
layout: post
title: Beginners Guide to Classes in Ruby
modified:
categories: [Ruby]
excerpt:
tags: []
image:
  feature:
date: 2016-03-21T08:49:14-07:00
---

## What are Classes and what are they good for?

When I was just starting to learn Ruby I had a terrible time understanding the purpose of a class. I didn't have anyone to explain them and everything I found online said the same thing "A class is a blueprint for an object", which meant nothing to me at the time. Furthermore as a beginner and Ruby being my first language, I was not comfortable looking at examples that were made using other languages, which considerably filtered down the examples to choose from. I remember being so frustrated that I made a promise that once I understood what classes were and how they were useful I would make a post explaining it in a way that would have been useful for me to understand.

I think the best way to understand classes and objects is with an example. It was with this example that I finally started understanding how classes would be useful in Ruby.

What we want to build is a deck of cards. Easy enough right? 

We COULD create a deck by hardcoding each of the cards into an array like this...

```
deck = [["ace", "spades"], ["king", "spades"], etc...]
```

Or you could even create your deck iteratively

```
deck = []
suits = ["club", "spade", "heart", "diamond"]
faces = ["ace", "king", "queen", "jack", "ten", ...etc]

suits.each do |suit|
  faces.each do |face|
    deck << [face, suit]
  end
end

```

This would be fine for a small project, but what if we wanted to make an interactive game of blackjack? Well we would need to be able to shuffle the cards, deal cards the players, make bets, determine if a hand is won or lost, etc..

If we wanted to make all this possible it would take a lot of code. I would challenge you to build this game in a single file all without using classes. This is the wrong way, but sometimes its easier to understand the good way of doing things after you experience the bad way yourself.

 I'm sure while trying you'd realize how complicated it would become. Then once you get stuck, try asking someone to help you debug it. No one will want to because it would be a horribly confusing and disorganized codebase to look at. Remember part of good code is that it will be easy for someone else to look at and understand whats going on in a reasonable amount of time. 

So how would you go about organizing the code in such a way that it would break apart each of the different aspects of the game? You would use classes. 

In object oriented programming (OOP) you want each class to be responsible for one thing. Just like you break up functions to only do one thing, you want to organize your code in such a way that each object or class does one thing. Think of it like this. Each class should be its own noun. In the blackjack example we would start by thinking about the nouns. Well we know we'll need a Dealer, Player, Deck, Cards, and maybe a Game class to get the game going. If this doesn't make sense that fine. Just start thinking about classes as being nouns. Now after you figured out all the different classes you will need, you can start thinking about what each class does. What your class does is defined by the methods you put inside of it. So methods are the verbs of the class, or the actions of a noun. A Dealer will need to be able to deal players their hand. That is a verb, its an action of the class Dealer. It will also need to be able to collect bets, another verb! All the actions that the Dealer will perform will be methods on the Dealer class. Can you start to see how this would start to give your code some structure and organization?

This is how you start thinking in an object oriented manner. The example we're going to do will be much less complex than a full game of blackjack and will hopefully start to make this become even more clear to you.

So back to our example of the deck of cards. Again, you could do this any way you wanted, its up to you as the developer to make these choices as to what the Nouns and Verbs are.  For this example were going to make a deck of cards and each card will be its own object. So lets first think about what makes a card a card. Well it has two properties it has a value and a suit. So we'll give our class Card two properies. This is something we haven't yet mentioned, properties. Well each class along with having methods has properties. When you read about objects changing state, all they mean is the properties of the object were changed. So as we said earlier a class is a blueprint for an object. Our card class will be the blueprint for reach card we make. There will be 52 objects or instances of the Card class that we will make up our Deck. Each of our 52 cards will be made using the Card class, so they will all have the same properties. In our example the state of each card will never change. It would be very difficult for someo

```
class Card
  attr_reader :value, :suit
  # we want to be able to read the value and suit, but not be able to change those values. It would be hard to play a game if the values of the cards could change!
  
  def initialize(value, suit)
    @value = value
    @suit = suit
  end

end
```

Now lets create our deck class

class Deck
  
  def initialize  
    build_deck
    @deck = []
  end

  private

  def build_deck
    suits = ["club", "spade", "heart", "diamond"]
    faces = ["ace", "king", "queen", "jack", "ten", ...etc]

    suits.each do |suit|
      faces.each do |face|
        @deck << Card.new(face, suit)
      end
    end






















