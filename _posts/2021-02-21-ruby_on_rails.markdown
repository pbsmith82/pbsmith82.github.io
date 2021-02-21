---
layout: post
title:      "Ruby On Rails"
date:       2021-02-21 19:36:30 +0000
permalink:  ruby_on_rails
---


There is a lot of magic behind rails. As the we have progressed through the program, we have seen what a little coding in rails is really producing behind the scenes. I would like to explain some of the basics I really enjoyed in Rails...

**Routes**
Routes in Rails make it so much easier to work with controllers and direct users. Not only is a developer able to designate paths that can be useful and obvious to endusers, they can use tools like Nested Routes. This would allow the application to capture ID's and pass them along. 

SAMPLE:
```
get '/dogs/needs_walked' => 'dogs#needs_walked'
  get '/dogs/by_breeds' => 'dogs#by_breeds'
 
  resources :dogs do 
    resources :walks, only: [:index, :new, :create]
  end
  
  resources :users
  resources :walks
```

**Helpers**
Helpers are great in assisting with views. At first, I was trying to figure out what the difference was between methods in the Model versus methods in the Helpers. When should a method be in a Model and when should it be in the Helper. This was simplified for me, but understanding Helper methods should help keep clean views, while Model methdos are more data driven. 

SAMPLE:

```
module DogsHelper


    def needs_walked_active_nav
        # byebug
        if params[:action] == "needs_walked"
            "nav-link active"
        else
            "nav-link time"
        end
    end

    def breeds_active_nav
        # byebug
        if params[:action] == "by_breeds"
            "nav-link active"
        else
            "nav-link time"
        end
    end

    def all_dogs_active_nav
        # byebug
        if params[:action] != "by_breeds" && params[:action] != "needs_walked"
            "nav-link active"
        else
            "nav-link"
        end
    end
    

end
```

**Form Helpers**
Form helpers in rails allow developers to pass along Model details among other details. This allows us to code less, and pass more. Developers can use form_tag, form_with, or even form_for. 

SAMPLE:

```
<%= form_with(model: @user, url:'/signup', local: true) do |f|%>
            
           <%= f.label "First Name:"%>
           <%= f.text_field name="first_name"%>

           <%= f.submit "Sign up"%>
					 
<%end%>
```


In short, I have find rails very useful. The tools to help keep code DRY is quite abundant. The larger the application the more rails would be a desired framework. A simpler app might find sinatra enough and simpler to maintain, but the more complex and larger an app becomes the tools Rails provides is most ideal.  
