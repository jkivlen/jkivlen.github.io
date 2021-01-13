---
layout: post
title:      "Session Blog"
date:       2021-01-13 15:54:21 -0500
permalink:  session_blog
---


## What is a session?

A session is a hash like object where we store a small amount of data on the server.  The data will be available in future requests from the same browser during the session and can be accessed with any of our application's controllers.  

We enable session in Sinatra by adding `enable :sessions` and `set :session_secret` in the configure block of our application_controller.rb file.  

```
configure do
  enable :sessions
  set :session_secret, "top_session"
end
```

The first line, `enable :sessions`, turns sessions on.  The `set :session_secret, "top session"` line is an encryption key that will be used to create a session id.  The `"top_session"` part of the code can be a string value of your choice.  A session id is a string of letters and numbers that is unique to the current user's session and is stored in cookies. 

## Why do we use sessions in Sinatra?

We use sessions in sinatra to store a user's user id in a hash so the app will remember them in the future.  We use this to log users in.  This way the user does not have to log in each time they go to a new page and are able to do things that would require remembering the user.  

We are also able to code in specific features for the app that only the current user will be able to utilize.  In the Sinatra movie app I made, only users can edit or delete movies that they added themselves.  This would not be possible without sessions.   
# How do sessions relate to HTTP being a stateless protocol?

When we say stateless protocol we mean that HTTP requests are independent, meaning a server can't tell if 2 different requests came from the same browser or user.  They maintain no information in memory which means HTTP can't remember a user's identity as they go to different pages.  This can make things difficult for developers when we need to tie together a series of requests from the same user as they go from page to page on a website.  We get around this by using cookies and sessions.    

HTTP provides us with cookies as a way to store data. A cookie is a hash that gets stored in the browser and sent back to the server along with each request afterwards.  A session is similar in that it is a hash like object but it is stored on the server.    

There are no cookies when a user's browser first connects with a website's server.  The website's server first receives a request from the browser and creates a cookie with information about the user.  The server then sends that information back to the browser, where the data is stored.  Whenever the browser connects with the same server in the future, it includes a cookie which the server can use to connect requests.           

Cookies are used by the server to implement sessions.  As we went over earlier, sessions allow for the application to remember a user as they move to different pages.  A particular session will last from the time you log in as a user to the the time you log out or close your brower.  Relying on the browser and server like this in order to store small amounts of user's data(usually < 4 KB) allows for HTTP to be stateless while providing a good experience for the user.  
# What does it mean to log in a user?
Logging in is just storing a user's ID in the session hash.  We use a key to store a user's ID like this: `session[:user_id] = user.id`.  This means that logging out is also just clearing the session hash: `session.clear`.    
 

![https://imgur.com/a/gXtDNqH]
