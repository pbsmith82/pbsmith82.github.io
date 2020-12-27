---
layout: post
title:      "Basic Sinatra CMS Application"
date:       2020-12-27 20:03:01 +0000
permalink:  basic_sinatra_cms_application
---


Writing a basic Sinatra CMS application is pretty simply. The base of the application is easy started with the use of the Corneal Gem, which I will explain here in a minute. The more tricky part, is the RESTful routing. It's pretty easy in concept, but the more you application can do, and the more models your's application has, the more you have to think about the users actions and goals. Lets take a look at the bones and get started. 

**Corneal Gem**
The corneal gem will help you build out the base of the application. It quickly generates a Sinatra template with Rails-like simplicity. All the user has to do is add/create the application details (Controllers, Views, Models), and make sure to account for them in setup files (config.ru). Simply get started by typing the following commands into the terminal. 

* Install the gem with `gem install corneal`
* Generate your app with `corneal new APP-NAME`
* Run `bundle install`


**Models**
Once I had the base of the project together, I had to decided what models would I use, and what were their relations. The obvious first option is Users. We have to be able to login and relate information to users, so my first Model should be a User. Now what do we want to relate to the User. In my case I used Cabins. 

**Migrations**
Now that we know at a very basic level what Models we are going to be working with, we should build out the migrations so we can see the details we will be working with. 

With the help of Rake we simply create the migrations by entering
```
rake db:create_migration NAME="create_[modeltype]"
```
Make sure to replace [modeltype] with what the migration will actually be creating. If this was for the user model it would be something like 
```
rake db:create_migration NAME="create_users"
```
Make sure to do this for each Model. 

After our migrations have been created we need to set them up. Simply navigate to the new migrations and lets add the tables. See Below for an Example:
```
 def change
    create_table :users do |t|
      t.string :first_name
      t.string :last_name
      t.string :email
      t.string :password_digest
      t.timestamps
    end
  end
```
In my tables, I used "timestamps" this adds two more columns to my table. "created_at" and "updated_at", and autmatically keeps tracks of those times for us to refrence. 

** Helpful Reminders**

* You will notice ApplicationController inherits from Sinatra::Base
* All other Controllers will inherit from ApplicationController
* Your Models should inherit from ActiveRecord::Base
* Set up your config.ru file. You should only have one "run" controller - and the rest should be "use"
   Example:
	 ```
	 use Rack::MethodOverride
   use UsersController
   use CabinsController
   run ApplicationController
   ```
	 
Take notice of the "Rack:MethodOverrid" - this allows us to use our patch and delete methods to update records. 

**Authentication & Validations**
A couple other key componets of this project is to make sure it's not only secure, but the data is clean. With the help of bcrypt we can use `has_secure_password` with our User class. You will also notice in the sample table setup above, there is key of "password_digest". This lets the system know this is a where the salted and hashed password is stored. 

You will also make sure to enable sessions in the ApplicationController and make sure to set a session_secret. See below for an example:
```
configure do
    set :public_folder, 'public'
    set :views, 'app/views'
    enable :sessions
    set :session_secret, "Very_Private_Session_Secret"
  end
```

*It would recommended to use something like dotenv to store your session_secret in an enviroment variable. This would be secure.

Now that session have been enabled and you can set the session id for users, with the help of "helpers" such as "logged_in?" and "current_user" you can verify who the users are, that are looking at the page, and verify if they are logged in. 

One last note on clean data and validation. It's important to make sure to validate that users have entered the required information as desired so your data is clean. This is easy accomplished through validation on the class. See example below. 

```
    validates :first_name, presence: true
    validates :last_name, presence: true
    validates :email, presence: true
    validates :email, uniqueness: true
```

This is the validation I used on my User class. Notice most of it just validates the "presence". This is to make sure they can't enter a blank name. You will notice on email though, I also validate "uniqueness". This make sure I don't have two users with the same login email. 

** SUMMARY **
The project in of it's self is pretty simple. It's easy to imagine how deep you may want to go and want to create many models, but I would suggest to start off slow. Stick with two models, and build the relations and project out based on those two models. If after you have done all that and would like to make it more complicated, feel free, but if you start complicated it easy to get lost in your relationships. 
