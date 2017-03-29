---
layout: post
title: Regular Expression in Ruby on Rails
---

In this post, I intend to write down some basic Regex knowledge, especially for Ruby..

##### Syntax

A regular expression literal is a pattern between slashes or between arbitrary delimiters followed by %r as follows:

{% highlight ruby %}
  /pattern/
  /pattern/im    # option can be specified
  %r!/usr/local! # general delimited regular expression
{% endhighlight %}
