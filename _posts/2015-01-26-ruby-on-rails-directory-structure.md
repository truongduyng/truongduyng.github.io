---
published: true
title: Ruby on Rails Directory Structure
summary: Ruby on Rails is a web framework written in the Ruby programming language. Rails is used by Airbnb, Basecamp, Disney, Github, Hulu, Kickstarter, Shopify, Twiiter. Ruby on Rails is 100% open-source, available under the MIT lisence, and as a result it costs nothing to download and use.
layout: post
author: Duy
category: coding
tags: technical
---

### Setup Ruby on Rails in Ubuntu<br><br>
<img src="http://i.imgur.com/LCeAWzb.jpg" alt="rails"><br><br>
You can setup Ruby on Rails in Ubuntu by following the inductions in [https://gorails.com/setup/ubuntu/14.10](https://gorails.com/setup/ubuntu/14.10) .
 <br><br>

### Ruby on Rails Directory Structure<br><br>

After setting up Ruby and Rails, you can new a Rails app with command: ```rails new your_app_name```. So you can see that rails generates automatically a bunch of directories and files. I will show you what they use for.<br><br>

```
|-- app
|   |-- assets
|   |   |-- images
|   |   |-- javascripts
|   |   |   `-- application.js
|   |   `-- stylesheets
|   |       `-- application.css
|   |-- controllers
|   |   |-- application_controller.rb
|   |   `-- concerns
|   |-- helpers
|   |   `-- application_helper.rb
|   |-- mailers
|   |-- models
|   |   `-- concerns
|   `-- views
|       `-- layouts
|           `-- application.html.erb
|-- bin
|   |-- bundle
|   |-- rails
|   |-- rake
|   |-- setup
|   `-- spring
|-- config
|   |-- application.rb
|   |-- boot.rb
|   |-- database.yml
|   |-- environment.rb
|   |-- environments
|   |   |-- development.rb
|   |   |-- production.rb
|   |   `-- test.rb
|   |-- initializers
|   |   |-- assets.rb
|   |   |-- backtrace_silencers.rb
|   |   |-- cookies_serializer.rb
|   |   |-- filter_parameter_logging.rb
|   |   |-- inflections.rb
|   |   |-- mime_types.rb
|   |   |-- session_store.rb
|   |   `-- wrap_parameters.rb
|   |-- locales
|   |   `-- en.yml
|   |-- routes.rb
|   `-- secrets.yml
|-- config.ru
|-- db
|   `-- seeds.rb
|-- Gemfile
|-- Gemfile.lock
|-- lib
|   |-- assets
|   `-- tasks
|-- log
|-- public
|   |-- 404.html
|   |-- 422.html
|   |-- 500.html
|   |-- favicon.ico
|   `-- robots.txt
|-- Rakefile
|-- README.rdoc
|-- test
|   |-- controllers
|   |-- fixtures
|   |-- helpers
|   |-- integration
|   |-- mailers
|   |-- models
|   `-- test_helper.rb
|-- tmp
|   `-- cache
|       `-- assets
`-- vendor
`-- assets
    |-- javascripts
    `-- stylesheets
```

* app : contains 6 directory. They are assets, controllers, helpers, mailers, models, views. They contains codes of your app. This folder is where most of your application code will go into.
	1. assets: contain your app's assets which are images, javacripts, stylesheets.

	2. controllers: It is the C in MVC. It can be thought of as a middle man between models and views. It receives the request, process logics, get or save data from model and use a view to create HTML output.

	3. helpers : It contains methods of the controllers which are used so many times, in manywhere.

	4. mailers: It is for mailing controllers.

	5. Models: It is the M in MVC. It manage your database of your app. It uses Active Record to communicate with your database.

	6. views: contains your template of your controllers and layouts. The template begins with _ is partials. It help you to DRY up your views.
 <br><br>

* bin : contains binary executable script for your rails project. These are the files that get exceuted when you run rails, bundle or rake from the command line.
 <br><br>

* config: Configures of your app.
	1. enviroments: config for your development, productions, test enviroments.
	2.initializers: initializes to your appications sush as cookies, sessions, assets,...
	3. locales: config multiple languages for your app.
	4. application.rb: config your app.
	5. database.yml: config database you use in app.
	6. routes.rb: config route of your app.
<br><br>

* db: contains config of your database
	1. migrate: contains of your migrations. Migrations are a convenient way to alter your database schema over time.
	2. schema.rb : contains your database table. This file is auto-generated from the curret state of the database. If you need to create the application database on another system, you only should be using db:schema:load, not running all the migrations.
	3. seed.rb: This file should contain all the record creation needed to seed the database with its default values.
<br><br>

* lib: contains your library from you or third party. lib/assets: Library assets such as cascading style sheets (CSS), JavaCript files, and images
<br><br>

* log: contains your logs file of app.
<br><br>

* public: contains public assets sush as robot, icon, static pages,...When you build your app, your assets in app directory will be build and put in here. Data accessible to the public such as error pages
<br><br>

* test: contains your code of test for your app.
<br><br>

* tmp: contains temporary file such as cache, sessions,...
<br><br>
* Vendor: Third-party code such as plugins and gems.
<br><br>

* README.rdoc: A brief description of the application.
<br><br>

* Gemfile: It is used for configuring gems you want to use in your app.
<br><br>

* Gemfile.lock: A list of gems used to ensure that all copies of the app use the same gem versions.
<br><br>

* config.ru: A configuration file for Rack middleware.
<br><br>

* .gitignore: Patterns for files that should be ignored by Git
<br><br>

Referrences: [https://www.railstutorial.org](https://www.railstutorial.org), [https://thinkster.io/angular-rails/](https://thinkster.io/angular-rails/)
