---
layout: post
title: Two common CSS problems I usually met and solution
---

* ### Footer need to be always at the bottom

Most of web applications have a footer. Footer is for your company or organization's infomation, copyright, etc. And as its name, it need to be at the bottom. But somethime your body content is too short, your footer is still at the bottom of the page, but not the bottom of viewport. Like this

![](https://c1.staticflickr.com/1/779/33033562011_4df0f1a39c.jpg)

###### Solution:

HTML
{% highlight html %}
<div id="container">
   <div id="header"></div>
   <div id="body"></div>
   <div id="footer"></div>
</div>
{% endhighlight %}

CSS
{% highlight css %}
  html,
  body {
     margin:0;
     padding:0;
     height:100%;
  }
  #container {
     min-height:100%;
     position:relative;
  }
  #body {
     padding-bottom:60px;   /* Height of the footer */
  }
  #footer {
     position:absolute;
     bottom:0;
     width:100%;
     height:60px;   /* Height of the footer */
  }
{% endhighlight %}

References: [http://matthewjamestaylor.com/blog/keeping-footers-at-the-bottom-of-the-page](http://matthewjamestaylor.com/blog/keeping-footers-at-the-bottom-of-the-page])

* ### Centering things

Following [this article](https://css-tricks.com/centering-css-complete-guide/), you can center anything totally in CSS. The most common case is centering the unknown height and width element. And for short, this is the solution:

{% highlight css %}
  .parent {
    position: relative;
  }
  .child {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
{% endhighlight %}

Centering things in CSS will be more easier if you use flexbox. flexbox is simple for centering.

{% highlight css %}
  .parent {
    display: flex;
    justify-content: center;
    align-items: center;
  }
{% endhighlight %}
