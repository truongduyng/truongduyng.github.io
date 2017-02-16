---
layout: post
title: Module vs class in ruby programming language
tag: ruby
---

Modules are about providing methods that you can use across multiple classes - think about them as "libraries" (as you would see in a Rails app). Classes are about objects; modules are about functions. Class is mainly different from Module by 3 main methods: new, allocate, superclass.

The table below show you the different between them.

|         | Class        | Module  |
| ------------- |----| -----|
|instantiation | can be instantiated       | can *not* be instantiated       |
| usage         | object creation           | mixin facility. provide a namespace.|
| superclass    | module                    | object                          |
| methods       | class methods and instance methods | module methods and instance methods|
| inheritance   | inherits behaviour and can be base for inheritance| No inheritance                  |
| inclusion     | cannot be included | can be included in classes and modules by using the include command (includes all instance methods as instance methods in a class/module)|
| extension     | can not extend with extend command (only with inheritance)| module can extend instance by using extend command (extends given instance with singleton methods from module) |

Example codes

{% highlight ruby %}

module A
  class B
    def initialize
      @ins_var = 1
    end
  end
end

a = A.new # undefined method new for A:Module
a = A::B.new
puts a.ins_var # 1

{% endhighlight %}
