---
layout: post
title:  "Eigenclass"
date:   2010-04-03 17:33:11
categories: 
tags: 
---

In Ruby, there’s the concept of eigenclasses, or singleton classes. These are
classes implicitly defined when attaching methods to a single instance.

From [Wikipedia](http://en.wikipedia.org/wiki/Ruby_(programming_language)):

>Ruby is [object-oriented](http://en.wikipedia.org/wiki/Object-oriented): every
>data type is an object, including classes and types which many other languages
>designate as primitives (such as
>[integers](http://en.wikipedia.org/wiki/Integer_(computer_science)), booleans,
>and "[nil](http://en.wikipedia.org/wiki/Pointer_(computing)#Null_pointer)").
>Every [function](http://en.wikipedia.org/wiki/Function_(programming)) is
>a [method](http://en.wikipedia.org/wiki/Method_(programming)). Named values
>(variables) always designate references to objects, not the objects
>themselves. Ruby supports
>[inheritance](http://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))
>with [dynamic dispatch](http://en.wikipedia.org/wiki/Dynamic_dispatch),
>[mixins](http://en.wikipedia.org/wiki/Mixin) and singleton methods (belonging
>to, and defined for, a single
>[instance](http://en.wikipedia.org/wiki/Instance_(computer_science)) rather
>than being defined on the class).

Here I present an example I hope will make it simple to understand. We know
martial artists can fight, right? And we know Jackie Chan can play while
fighting, right? Now suppose there’s no Sammo Hung and Jackie Chan is the only
one who do fancy things while fighting. All other martial artists are Bruce
Lee-like. What do we do? Extend ```MartialArtist``` class to create
a ```FunnyMartialArtist``` class which will get instantiated only once? Instead, we
can just add a method ```do_funny_fighting``` to ```jackie_chan``` object which is an
instance of ```MartialArtist```. This way:

{% highlight ruby %}
class MartialArtist
  ...
end

jackie_chan = MartialArtist.new
bruce_lee = MartialArtist.new

def jackie_chan.do_funny_fighting
  ...
end

{% endhighlight %}

Now we can call ```jackie_chan.do_funny_fighting```, but not
```bruce_lee.do_funny_fighting```. This is a singleton method.

How does this work? Under the hood, there’s a pointer in ```jackie_chan``` to the
```MartialArtist``` class. If Ruby modifies its content to add the new method, it
will also affects ```bruce_lee``` object. So, Ruby creates a new class, adds the
method to it and updates ```jackie_chan``` class pointer to point to this new class
(and this class points to previous ```MartialArtist``` class). This new class is an
eigenclass.

That’s a simple way to say it without dealing with much details. But if you’re
eager to learn more, I recommend Patrick Farley’s post about
[metaclasses](https://web.archive.org/web/20100325081153/http://www.klankboomklang.com/2007/10/05/the-metaclass).
There are also a lot of links there to dig deeper.
