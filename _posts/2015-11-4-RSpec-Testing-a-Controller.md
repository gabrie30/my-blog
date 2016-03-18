---
layout: post
title: "RSpec, Testing a Controller"
excerpt: "Testing Rocks!"
tags: [Ruby, Rails, RSpec, Testing]
comments: true
---

Testing a controller can be tricky business. I wanted to go over a couple examples that might help demystify the process. Because controllers are more difficult to test, it makes sense to keep them thin as possible. When refactoring look at the logic in the controller and try to refactor it out to the model. Models are much easier to test and it will make your controllers easier to read.


```ruby
require "rails_helper"

describe PeopleController do
  describe "#edit" do 
    context "success" do 
      it "renders the edit template" do
        @person = Person.create(first_name: "Jay")
        
        put :edit, {id: @person.id, person: {first_name: "Jay"} } 
        expect(response).to render_template :edit
      end
    end
  end

  describe "#update" do 

    context "when save is successful" do 
      it "redirects to the #show" do 
        @person = Person.create(first_name: "Jay")
        
        put :update, {id: @person.id, person: {first_name: "Jayson"} } 
        allow(@person).to receive(:save).and_return(true)

        @person.reload
        expect(@person.first_name).to eq("Jayson")
        expect(response).to redirect_to(person_path(@person))
      end
    end
  end

  describe "#create" do
    context "when person is valid" do
      it "redirects to #show" do
        person = Person.create(first_name: "Bob")
        allow(person).to receive(:save).and_return(true)
        allow(Person).to receive(:new).
          with(first_name: "Bob").
          and_return(person)

        post :create, person: { first_name: "Bob" }

        expect(response).to redirect_to(person_path(person))
      end
    end

    context "when person is invalid" do
      it "redirects to #new" do
        person = double("person")
        allow(person).to receive(:save).and_return(false)
        allow(Person).to receive(:new).with(first_name: "").and_return(person)

        post :create, person: { first_name: "" }

        expect(response).to render_template(:new)
      end
    end
  end
end
```