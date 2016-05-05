---
layout: post
title: "Javascript vs CoffeeScript"
description: "Fight!"
category: programming languages
tags: [javascript, coffeescript]
---
{% include JB/setup %}

Recently, we had a big debate about the usefulness of CoffeeScript vs
keeping on with Javascript only. We also had a fit over Backbone, but
I'll leave that discussion for another day.

It came down to one major thing: people were stressed out about using
Coffeescript any further because our deadline was fast-approaching and
people didn't want to learn more things along the way.

I think anyone could sympathize with the fact that learning new
technologies can be an impediment to development. But it made me
wonder--is CoffeeScript hard enough to learn that it's an impediment to
a furious development schedule? Or is it just that new technologies
should _never_ be introduced during such a time?

Well, here are a couple things about CofeeScript that might make a
veteran Javascripter scratch their head at first:

### Functions

They're really nice once you get to know them. I appreciate the terse
syntax, but it can be very confusing to look at for a long-time
Javascript dev.

{% highlight coffeescript %}
(arg1, arg2) ->
  alert 'inside a function'
# or
(arg1, arg2) -> alert 'inside another function'

class MyClass
  myFunc: (arg1, arg2) =>
    alert 'always bound to the "this" of any given instance of MyClass, because of the fat arrow ("=>")'
{% endhighlight %}

### Classes

Not all Javascript devs will love the way CoffeeScript uses prototypical
inheritance in its generated classes. Thankfully, CoffeeScript compiles
to Javascript, so you can roll your own non-prototype-oriented classes
as well.

{% highlight coffeescript %}
MyClass = (constructorArg1, constructorArg2) ->
  # do stuff
  instanceMethod = ->
    alert 'a different type of js class'

  {
    exposedInstanceMethod: instanceMethod
  }
{% endhighlight %}

### Array and Object Comprehensions

This is one thing that I love about CoffeeScript, actually. Then again,
it's something that is quite a bit different than Javascript.

{% highlight coffeescript %}
list = [1, 2, 3]

# The following are equivalent:

for item in list
  doSomething(item)

doSomething(item) for item in list

# Also, you can treat array comprehenions as arrays themselves

x = (item + 1 for item in list)
x == [2, 3, 4] # => true
{% endhighlight %}

### Hmm

Well, not much more to say, really. That's not an exhaustive list of
oddities, so staunch Javascript devs probably won't be happy switching
in a hurry. Is there a compromise?
