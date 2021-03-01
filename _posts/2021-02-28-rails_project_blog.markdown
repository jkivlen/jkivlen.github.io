---
layout: post
title:      "Rails Project Blog"
date:       2021-03-01 01:05:42 +0000
permalink:  rails_project_blog
---


Before this project, I was very excited to finally begin working with Rails.  From my understanding, Ruby on Rails is actually how most developers use Ruby in their day to day jobs because of how powerful and "magical" it is.  I had listened to a few interviews with David Heinemeier Hansson earlier in the curriculum and was looking forward to actually using his framework.  It did not disappoint.  

## Project Planning

For my Rails project I decided to build an app that would allow a user to add cars, the maker of the car, the price and color attributes.  The user would have to be able to edit and delete cars but only for the cars in which they added.  This would be set up by having models for the user, car and make which would be connected with has_many, belongs_to and has_many :through relationships.  

In addition to this the user would have to be able to sign up and log in in a standard way as well as using their Gmail account if they wish to do so.  

### Planning the Tables and Associations

I wanted to have an idea of what the tables and associations for the app would be before writing any code.  After writing it out on a sheet of paper, I came up with the following associations that would work.  

Car
```
belongs_to :make
belongs_to :user
```

Make
```
has_many :cars
has_many :users, through: :cars
```

User
```
has_many :cars
has_many :makes, through: :cars
```

After having these figured out along with the attributes that would belong to each table, I began the project.  

### Beginning the Project

Starting the project with Rails was far easier than using Ruby without rails before thanks to the "rails new" command.  It was also far easier and quicker to set up all of the model, routes, controller and views files for each table thanks to the powerful model and controller generators.

I began by creating the controllers, routes, models, and views for the User model.  Before setting up normal login functionality I set up the ability to sign up and login with google using omniauth.  A few gems were needed to be added to the gemfile but overall it was a pretty easy process thanks to guidance from Jenn Hansen on [this medium blog](http://www.google.com/url?q=https://medium.com/@jenn.leigh.hansen/google-oauth2-for-rails-ba1bcfd1b863&sa=D&source=editors&ust=1614561728626000&usg=AFQjCNFVkz5eusLxVB0kcHxAllPsuoCAqQ).  After this was all smoothly set up I set up the basics for signing up and logging.  I set up some helper methods for a "current_user" method and "logged_in?" method in the application_helper file to make this easier.  I also set up routes manually for login and signup because "/signup" and "/login" make for a more intuitive and better user experience than the routes that would have been set up for "users/new" or "sessions/new" that would have been created from using resources :users and resources :sessions.  

### Setting Up Cars and Makes

Setting up the models, routes, views and controllers for the Cars and Make tables ended up being more difficult and tricky than expected due to the associations.  While setting up the basic CRUD functionality for the cars model, I seeded in data so that I would have something to work with in the server to make sure my code was working.  Although this was good for getting a visual of what I was doing early on, it became and issue when having to nest attributes later on.  Car objects that I initially set up using the car model with the make attribute would not be displayed after I connected the car model with the make model using the name attribute.  

From here, I decided to just start over and plan better with the seed data as I was still having issues with errors even after removing my seed data.  From here I set up all the user functionality again and built the car and make models at the same time with the correct attributes from the beginning.  From here everything went smoothly.  

I was able to build out full CRUD functionality with both the make and car models.  I was also able to set up an "expensive" method that would display the most expensive car listed using an order by price ActiveRecord query.  All of the models had validations that made sense with error messages that would explain why certain fields need to be filled out.  

### Making it DRY

A lot of my code was repeating itself in the cars controller and views.  From here I made a few before actions for the show, edit, update, destroy and create methods to help fix this problem.  In addition to this I rendered partials within forms to reduce repetition.  Specifically in the create and edit views.  Some helper methods were also added to help with the show and index views for cars.  

## Wrapping it Up

Overall this project was much more challenging than the previous two.  Rails is very powerful but with that comes with much more learning.  As Uncle Ben said in SpiderMan, "With Great Power Comes Great Responsibility".  I will continue to create more applications in Rails and use the guides to become more famliar with everything that is possible to do within this very interesting framework.  

