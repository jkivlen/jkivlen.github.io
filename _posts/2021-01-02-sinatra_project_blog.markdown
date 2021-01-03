---
layout: post
title:      "Sinatra Project Blog"
date:       2021-01-03 02:31:40 +0000
permalink:  sinatra_project_blog
---

### What is Sinatra?
I was famliar with some of the basics of programming before starting at Flatiron but Sinatra was one part of the syllabus that I had never heard of before outside of the famous singer.  This made me a little nervous at first, but after going through all the couse material and getting more familiar with the open source software, this became the most fun part of my flatiron journey so far.  

Sinatra is an open source software framework used to make web applications, created by Blake Mizerany, that was written specifically for Ruby.  It is best served for building web applications and is the predecessor to Ruby on Rails.  It consists of a MVC(Model-View-Controller) architecture.   

### Starting the Project
With starting the project it was recommended to choose a topic that interests you, so I chose movies for my application.  To begin I used the Corneal gem.  This was fairly easy to do and it set up the file structure for the Sinatra MVP app.  This would have taken a lot of time and going back and forth through my notes to set up manually.  

After this was set up I needed to wire frame the application.  I chose the models of movie and user along with their attributes and associations.  This made it easy to figure out what the app would do which is serve as a place for users to enter in, edit and delete movies by their title, genre and year.  

After all of this was outlined on paper I just had to build my models, migrations and associations in VS code.  

### Beginning Coding
Most the environment.rb, Rakefile, config.ru and other things needed to start were already taken care of by the Corneal gem.  Because of this, I could just start out by building the movie and user models and migrations using ActiveRecord.  After setting those up and creating the tables it, everything appeared correctly in the schema.rb file.  I then used rake to migrate some seed data as well to make sure everything was working.  

### Controller and Views
After getting the models and tables set up, it was time to work on the controller and views for the user and movie classes.  I started with setting up everything with movies first, which in hindsight was the wrong way to do it.  Starting with users would have been far easier.  Nevertheless, I set up the basics for the index, show, new, create, edit, update and destroy actions.  This involved going back and forth between the movies_controller.rb file and views/moves files while looking back at many lectures to correct coding errors.  I also needed to remember to add run ApplicationController and use MoviesController to the config.ru file.

After all of these were set up to the point where you could add, edit, show and delete movies in the app while using shotgun, I then added the user controllers and views.  I created a signup, login and logout capabilities within the app using users_controller.rb and the views/user .erb files.  After these capabilities were figured out and tested using shotgun, it was then time to add user specific capabilities using a combination of helper methods, has_secure_password and the 'sinatra-flash' gem.  With this I was able to make sure that only users can login, log out, create movies, edit their own movies or delete their own movies all after signing up initially with a username and password.  This way non users or those who did not add the movies initially cannot edit movies added by other users.  You would also get messages telling you if you tried to do something you did not have permission to do. 

### Making the App More Usable
The app was capable of everything needed but it did not look great.  I decided to change the background color, change some headings, add links, add a navigation bar in the header, and add a footer.  The navigation bar at the top which allows you to add a movie, see all the movies or log out only appear when a user is logged in.  The links in the footer for home, add a movie, all movies, sign up and log in are there at all times.  The default web page is a sign up or log in page for the user.  Most of these adjustments were made in the layout.erb file.  

### Wrapping Up
This project took a pretty long time to complete but it was not too challenging because of all the great resources provided by flatiron.  I was usually able to find the solution to any issue I was having within lectures, videos or the corriculum.  I got better at making sure to commit my project to github as the project went on and it was cool to see actual visual evidence as my app got better both functionally and visually as the project progressed.  This was my favorite part of the course so far.  


