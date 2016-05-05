---
layout: post
title: "Object Generation, Randomized Values, and Uniqueness Validations"
description: "What happens if you're not careful."
category: testing
tags: [rspec, fabrication, faker, validations, testing]
---
{% include JB/setup %}

Intermittantly failing specs are infuriating.

So, a word of warning: If you're using `FFaker` or something to generate values
in your object generation library (in our case, that would be
`Fabrication`), be careful with uniqueness validations.

Yes, it's obvious how to fix now. But it's not so obvious when you add a
uniqueness validation, forget to change the object generator, run the tests,
find that they happen to pass (that time), and then later you're
wrestling with intermittantly failing specs. And because it's no longer fresh
in your mind, you have no idea why.

Here's the obvious fix, implemented in `Fabrication` (with `FFaker`, still):

{% highlight ruby %}
Fabricator :account do
  # this column has a uniqueness validation
  name { sequence(:account_name) { |i| "#{Faker::Company.name} {i}" } }
end
{% endhighlight %}

That's a bit paranoid, but consider that originally we had

{% highlight ruby %}
name Faker::Lorem.word
{% endhighlight %}

instead, which was causing lots of random collisions.

Well, I hope that helps someone.
