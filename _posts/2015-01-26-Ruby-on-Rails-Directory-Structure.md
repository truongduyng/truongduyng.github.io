---
published: true
title: Ruby on Rails Directory Structure
layout: post
author: Duy
category: Ruby on Rails
tags: RubyonRails
---
### Setup Ruby on Rails in Ubuntu<br><br>

You can setup Ruby on Rails in Ubuntu by following the inductions in https://gorails.com/setup/ubuntu/14.10 . 
 <br><br>

### Ruby on Rails Directory Structure<br><br>
  
After setting up Ruby and Rails, you can new a Rails app with command: rails new your_app_name. So you can see that rails generates automatically  a bunch of directories and files. I will show you what they use for.<br><br>

![Rails Directory](https://lh4.googleusercontent.com/-32T4Pu-O8RU/VMW1PJXGGNI/AAAAAAABOmA/IDMNPS2p9Xk/s0/railsdirectory.png "Rails Directory")
<br><br>

* app : contains 6 directory. They are assets, controllers, helpers, mailers, models, views. They contains codes of your app.
	1. assets: contain your app's assets which are images, javacripts, stylesheets.

	2. controllers: It is the C in MVC. It can be thought of as a middle man between models and views. It receives the request, process logics, get or save data from model and use a view to create HTML output.

	3. helpers : It contains methods of the controllers which are used so many times, in manywhere.

	4. mailers: It is for mailing controllers.

	5. Models: It is the M in MVC. It manage your database of your app. It uses Active Record to communicate with your database.

	6. views: contains your template of your controllers and layouts. The template begins with _ is partials. It help you to DRY up your views.
 <br><br>

* bin : contains binary of some gems to use in your app's development.
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

* lib: contains your library from you or third party.
<br><br>

* log: contains your logs file of app.
<br><br>

* public: contains public assets sush as robot, icon, static pages,...When you build your app, your assets in app directory will be build and put in here.
<br><br>

* test: contains your code of test for your app.
<br><br>

* tmp: contains temporary file such as cache, sessions,...
<br><br>

* Gemfile: It is used for configuring gems you want to use in your app.
