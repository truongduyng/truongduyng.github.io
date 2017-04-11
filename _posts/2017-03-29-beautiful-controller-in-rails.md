---
layout: post
title: Beautiful controller in rails
tag: rails
---

Your controllers is too fat and messy. You want to make them better. You should be follow these rules:

* Short, DRY, easy to read
* Minimum amount of glue code between request and model
* Unless there is good reason, controller should be follow a standard

When user's interactions are normalized to CRUD. Our controller could be like this

```ruby
class ObjectController < ApplicationController

  def index
    load_objects
  end

  def show
    load_object
  end

  def new
    build_object
  end

  def create
    build_object
    save or render 'new'
  end

  def edit
    load_object
    build_object
  end

  def update
    load_object
    build_object
    save or render 'edit'
  end

  def destroy
    load_object
    @object.destroy
    redirect_to objects_path
  end

  private

  def object_params
    obj_params = params[:object]
    obj_params ? obj_params.permit(:id, :attributes) : {}
  end

  def load_objects
    @objects ||=object_scope
  end

  def load_object
    @object ||= Object.find_by_id(params[:id])
  end

  def build_object
    @object || = object_scope.build
    @object.attributes = object_params
  end

  def save
    redirect_to @object if @object.save
  end

  def object_scope
    Object.scoped
  end

end
```

Since there is a lot of user's interactions that don't fit to one model or don't result in database like sign in form. So in order to use the powerful of ActiveRecord (validation, callbacks and views automatically render errors), we could use `activetype` gem.

It allows us to use many features from ActiveRecord:
* Validations
* Attributes setters the cast string to interger, hash, etc
* Transactional-style form submissions where an action is only triggerd once all validations are passed.

Maybe you think this technique will lead us to fat model. Be okay, we will talk about fat model later. We can handle the fat model problem.

References: [Growing Rails Applications in Practice - Henning Koch and Thomas Eisenbarth](https://leanpub.com/growing-rails/)
