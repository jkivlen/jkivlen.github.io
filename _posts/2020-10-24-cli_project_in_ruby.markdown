---
layout: post
title:      "**CLI Project in Ruby**"
date:       2020-10-24 19:51:07 +0000
permalink:  cli_project_in_ruby
---


Like anyone else born in the 90s, I was very familiar with Pokemon growing.  I had many of the cards, games and watched the TV show so this made it a good choice for the API for the first coding project.  Even if I hadn't thought about Pokemon much in the last 20 years, I would still be familiar with the basic idea so going through the API would not be too confusing.  
Beginning

While looking over the project guidelines, it was clear that I was still shaky on some of the concepts I would need to know to complete the lab so I went back through the material to get more comfortable with everything we had gone over so far.  
After feeling feeling more confident in that area I initally struggled for a while getting the project set up in the IDE environment.  I could get the libraries and files to push to github but not the code for some reason.  After trying to figure this out for a while, I decided to just switch to a local environment.  This solved all the problems with getting things to push to github that I could not figure out with tutorial or google before.  

### File Set Up

I was able to set up the bin and library folders.  I then set up the run file inside the bin folder and api, cli, and pokemon_ditto files inside the library folder.  I also set up the basic classes for the api, cli and pokemon_ditto files.  I also created the environment and README files.  I used require relative to connect the relate the environment file to the cli, api and pokemon_ditto files.  I then added require pry,  json and httparty to the environment file.  I had an issue with downloading json gem and needed to use google to figure out what the issue was.  Stackoverflow provided a solution to the problem.  It was just a small problem with my local environment that required me to download a few things to solve.  This took about 15 minutes to download.

### Choosing an API

After everything was finally set up correctly I was ready to begin the actual project.  At first I chose a pokemon API that did not have many hashes or attributes.  This became an issue a little bit later on as the code could not be parsed through.  I asked my cohort lead Madeline, for instruction and she suggested to choose a different API that would be better suited for the project.  After going through a few of the makeup and movie API's I decided to go back to Pokemon and choose an API for Ditto, a weird looking purple pokemon.  This API had several different hashes and attributes and would work just fine.  

### Finally Coding

In the run file, I was able to set up the Shebang line and require_relative to the environment file with no hiccups.  I also added a start instance method to the CLI class which I instanciated in the run file using `CLI.new.start` so the CLI would begin after entering `ruby bin/run` in the terminal.  

The next step was the begin working in the API class so I could get the data from the pokemon API.  I looked through our resources guide and found this link(https://www.twilio.com/blog/2015/10/4-ways-to-parse-a-json-api-with-ruby.html) about the best ways to parse a JSON API with Ruby.  After looking through this I decided to choose HTTParty to parse through the API.  I looked at a few walk through tutorials that flatiron instructors had uploaded to youtube and got to work.  The result was creating a class method called `self.catch_pokemon_ditto` (gotta catch 'em all right?) and calling on that method with `API.catch_pokemon_ditto` in the start instance method in the CLI class.  I was able to use binding.pry to get through some mistakes to return the parsed API.  

After this was complete, it was time to work on the Ditto class.  I added the reader and writer for the attributes in the API as well as setting a class @@all variable set to an empty array, an initialize method that will put the new Ditto instance into that array, and a self.all method to be able to call on the array.  

It took a while for me to figure out which array of hashes to focus on iterating through.  The first one I chose was abilities.  There were 4 ability attributes but only 2 hashes to choose from.  This proved for having an underwelming list later in while building out the CLI.  I decided to choose game indices as there were 20 of these hashes that had 3 attributes each which worked much better.  I initially made some mistakes iterating through the hashes because some of the values were 1 level deep and some were 2.  I was able to figure this out with binding.pry after being stumped as to why some values were coming up as nil for a little bit.  After all the hashes were set iterated through and set to instance variables, it was time to build the CLI. 

Building the CLI was a little bit more straight forward for me than the previous parts.  I am more comfortable with coding and creating instance methods than I was working with API's, setting up folders, committing to github, installing gems, and all the other things I had to work on earlier.  I was able to create all the instance methods to ask the user if they would like to see the list of Ditto game indeces, list the games, choose which game they wanted to learn more about, make sure they gave correct inputs, return the information about the game they chose, start again and exit.  I was able to get through roadblocks here involving things like using gets and iterating with index by using google and going back to previous lessons and videos in learn.co.   

This first project was challenging for me but rewarding to finally get through and have the CLI work the way I intended to.  It was a bit overwelming at first but using the resources flatiron provided and google were able to get me through to the finish.  
