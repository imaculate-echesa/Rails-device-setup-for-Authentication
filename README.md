# README
How To Set Up Rails Devise

Usually when I implement authentication I build it from scratch. Most of my projects have been like that. Even though I heard about devise I just felt comfortable building it this way because I felt that I had more choice. Finally after looking for more things to learn about I decided to give devise a try. I was very surprised with how easy it is to implement devise into rails. It makes authentication so painless. Today I am going to show how I set up devise using rails.

First we are going to start with a new application so run rails new like this.

rails new rails_devise rails

First we are going to go inside of our Gemfile and add the devise gem and then bundle. After that run the generator.

bundle installrails g devise:install

When you run the second command you will get a set of instructions that will need to be completed. First you will have to define default url options in your environment file. This is the example that is given in the instructions and will work just fine. Make sure to copy and paste it in config/environments/development.rb

config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

Next we have to make sure that we define a root route. So go to routes.rb and add this.

root to: "home#index"

Next we have to add flash messages in our views layout. This is to make sure we get an alert if something is not right when entering the information into our form. Add this line of code in the body of app/views/layouts/application.html.erb

<p class="notice"><%= notice %></p>
<p class="alert"><%= alert %></p>

The final instruction is optional but I am going to use it to set up the devise views. This will make it easier to get started and show how devise works.

rails g devise:views

We don’t have a home controller yet so let’s get that set up before we run the server.

rails g controller Home index
rails s

We have a home controller with and index action now. Now to finally start signing in users let’s generate a user model with the devise command and migrate.

rails g devise User
rails db:migrate

Now we have to look for the appropriate route. To easily see the needed route for the sign up page type this into the terminal.

rails routes | grep users

Travel to the new_user_registration path and you will see a fully functioning sign up form thanks to devise views.

That was very straightforward and painless. I will be using devise for many of my projects in the future. Thanks for reading and happy coding! 😎

For more in formation you can follow this link:- https://stucklucky.medium.com/how-to-set-up-rails-devise-5bd39732629f
