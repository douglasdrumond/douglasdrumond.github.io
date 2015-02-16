---
layout: post
title: "Replacing in bash without sed"
date: "2012-11-6"
categories: ""
tags: ["bash"]
author: "Douglas Drumond"
---

Bash has built-in substitution. For simple tasks it’s easier than piping through sed:

{% highlight bash %}
text="hello world"
echo ${text/hello/ohayou}   # prints ohayou world
{% endhighlight %}

Be aware that just the first word is changed:

{% highlight bash %}
text="hello world hello"
echo ${text/hello/ohayou}   # prints ohayou world hello
{% endhighlight %}

To change all instances of a world, prepend the search pattern with another slash:

{% highlight bash %}
text="hello world hello"
echo ${text//hello/ohayou}   # prints ohayou world ohayou
{% endhighlight %}

Notice there are two slashes before *hello*, one as the separator and one prepending it.

