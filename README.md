# Deploying Hyperloop Showcase on Heroku (Fast way)

## Preamble

This tutorial is the fourth in a series of four:

+ Chapter 1 : [Hyperloop Showcase](https://github.com/fzingg/hyperloop-showcase) 
+ Chapter 2 : [Hyperloop Showcase Template](https://github.com/fzingg/hyperloop-showcase-template) 
+ Chapter 3 : [Hyperloop Showcase with Heroku (Debug way)](https://github.com/fzingg/hyperloop-showcase-heroku) 
+ Chapter 4 : [Hyperloop Showcase with Heroku (Fast way)](https://github.com/fzingg/hyperloop-showcase-template-heroku) 

For more information : [Hyperloop Web site](http://ruby-hyperloop.io/)

## INTRODUCTION

This tutorial shows how to deploy quickly the **Hyperloop showcase** on a **Heroku** Server.

This tutorial assumes you already have the **Hyperloop showcase** running successfully on your local environment. If that is not yet the case, please read and follow one of these 2 tutorials: [Hyperloop Showcase](https://github.com/fzingg/hyperloop-showcase) or [Hyperloop Showcase Template](https://github.com/fzingg/hyperloop-showcase-template)

## DEPLOYING TUTORIAL

#### Setup a new Heroku app

```
heroku login
heroku create
heroku addons:create heroku-postgresql
```

```
#config/database.yml


production:
  adapter: postgresql
  encoding: unicode
  database: hyperloop-showcase-template-heroku_production
  username: hyperloop-showcase-template-heroku
  password: <%= ENV['HYPERLOOP-SHOWCASE-TEMPLATE-HEROKU_DATABASE_PASSWORD'] %>
```

```
#Gemfile

	ruby '2.3.1'

```

```
bundle update
```

```ruby
#config/environments/production.rb

config.assets.compile = true

```


```ruby
	#app/policies/application_policy.rb

	# Policies regulate access to your public models
	# The following policy will open up full access (but only in development)
	# The policy system is very flexible and powerful.  See the documentation
	# for complete details.
	class ApplicationPolicy
	  # Allow any session to connect:
	  always_allow_connection
	  # Send all attributes from all public models
	  regulate_all_broadcasts { |policy| policy.send_all }
	  # Allow all changes to public models
	  allow_change(to: :all, on: [:create, :update, :destroy]) { true }
	end

```

```
#Procfile

web: bundle exec puma -C config/puma.rb
```

```
git add .
git commit - m "init"
git push heroku master
```
