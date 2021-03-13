---
layout: post
title:      "Search Form in Rails"
date:       2021-03-13 05:22:11 +0000
permalink:  search_form_in_rails
---


Being able to perform searches while using a website is very important and standard operating procedure when using the internet in 2021.  This makes being able to code search forms into any website or application we are working on a necessary skill to have.  I had not attempted or thought about creating a search form before today so it was an exciting challenge to tackle.  


### Getting Started

To begin, I decided to create a "form_tag" form.  I knew from material earlier in the course that "form_tag" forms were good for search as they aren't directly connected with models and take in a url. I had mostly been using "form_for" though so I needed some reminders about how "form_tag" worked.  After some googling, I found the following code and placed it into the index view of my rails cars app:

```
<%= form_tag("/search", method: "get") do %>
  <%= label_tag(:q, "Search for:") %>
  <%= text_field_tag(:q) %>
  <%= submit_tag "Search" %>
<% end %>
```


After reloading the screen the search form appeared.  This was only the first step in the process though as trying to search for a car resulted in an error message.  The next step was to create the search route which was missing.  After a few tries I ended up with the following code which got me past the missing route error.  

`get '/search', to: 'cars#search', as: 'search'`

From here the move was to create a search action in my cars controller.  

### Struggling but Overcoming

At this point, by using Google, rails guides and Youtube I was able to find the solutions to getting search functionality if I was looking for only the car color or make of the car using SQL but I needed to be able to do both and then display the results correctly.  This was proving to be difficult as the make of the car was a nested attribute in the cars model.  I decided to clean up the search form at this point as well with the following code:

```
<h3> Search For Cars </h3>
<%= form_tag search_path, method: :get do %>
    <%= text_field_tag :search, nil, placeholder: "Search" %>
    <%= submit_tag "Search" %>
<% end %>
```

Here there is a "search_path" helper being used instead of the "/search" url.  I also replaced :q with :search to make it easier to understand in the model and controller files.  The placeholder for "Search" might have been a little bit of overkill but I thought it was neat so I left it in.  

I was eventually able to find this blog post: https://melvinchng.github.io/rails/SearchFeature.html#46-search-across-multiple-tables, which showed how to search across multiple tables which saved me.  From the advice here and from several other sources I was able to figure out a solution that worked.  

The following class method needed to be placed in the car.rb models file.    

```
def self.search(params)  
        where("lower(makes.name) LIKE :search OR lower(cars.color) LIKE :search", search: "%#{params.downcase}%").uniq 
     end
```

Here we query using lowercase search the names attribute under the make model and the color attribute under the cars model to see if they match our lowercase search parameters.  From here this class method is used within the search action in the cars controller model like so:


```
def search
    if params[:search].blank?
      @cars = Car.all
    else
      @cars = Car.joins(:make).search(params[:search])
       @cars
    end
  end
```

If nothing is typed into the search bar then all the cars are listed normally.  But if a search is typed in, then the "search" class method is called using the search parameters on the joined tables.  The results are then viewed using the search.html.erb file in the cars views.  The make_color_and_price method I created earlier in the project is used to display the search results.  


```
<h1> Search Results </h1>

<ul>
<% @cars.each do |car| %>
    <li><%= link_to(car.make_color_and_price , car_path(car.id)) %><li>
<% end %>
</ul>
```

### Conclusion

Overall this ended up being more challenging than anticipated because of the nested attributes but it was a good challenge that required more learning.  I definitely need to brush up more on my SQL and build more projects where I create search forms so I can become more familiar with the process.  
