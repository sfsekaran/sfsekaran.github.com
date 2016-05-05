---
layout: post
title: "Luka: The duplicitous, silver-tongued proxy."
description: "A new gem that adds a fluent interface on any object."
category: software
tags: [ruby, rubygems, proxy, fluent interface]
---
{% include JB/setup %}

I randomly decided to create a gem. I'm usually pretty bad at executing
on my independent ideas for gems, but this on was so simple I didn't
have an excuse.

**Luka** simply adds a fluent interface on top of any object. It's still
a hatchling, so it doesn't care about return values yet. I'm open to
expanding its functionality, so if you have an idea, leave a comment.

[http://sfsekaran.github.com/luka](http://sfsekaran.github.com/luka)

You can use it like this:

{% highlight ruby %}
class Words
  def initialize
    @sentence = []
  end

  def I
    @sentence << 'I'
  end

  def like
    @sentence << 'like'
  end

  def pie
    @sentence << 'pie'
  end

  def sentence
    @sentence.join(' ') + '.'
  end
end

include Luka

say = luka(Words.new)
say.I.like.pie

say.sentence # => "I like pie."
{% endhighlight %}

Enjoy!
