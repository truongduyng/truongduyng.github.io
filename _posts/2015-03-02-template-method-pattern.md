---
published: true
title: Template Method Pattern
layout: post
tag: ruby
---

You want to build a program to teach your children to know animals. You write class animal like that:

{% highlight ruby %}
class Animal
  def initalize(name, age, species)
    @name = name
    @age = age
    @species = species
  end

  def say
    if(@species == "dog")
      puts "Gau...gau..gau..."
    end
    if(@species == "cat")
      puts "meo...meo...meo"
    end
  end
end
{% endhighlight %}

After that, you want to add more infomation about animals in your program. It's a nightmare if you want to add more and more species in your old code.

Luckily, you can use template method patter to do it simply, easily. Like that

{% highlight ruby %}
class  Animal
  def initialize(name, age)
    @name = name
    @age = age
  end

  def say
    raise 'Called say method in subclass'
  end
end

class Dog < Animal
  def say
    puts "Gau gau gau"
  end
end

class Cat < Animal
  def say
    puts "meo ... meo ...."
  end
end
{% endhighlight %}

At now, you can test it by

{% highlight ruby%}
dog = Dog.new("some name", 2)
dog.say

Your result will be "Gau gau gau".
{%endhighlight%}

Congratulation! You learnt a pattern in 23 patterns of GoF. It is Template Method Pattern.
