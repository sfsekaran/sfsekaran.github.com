---
layout: post
title: "RMagick Can't Find the ImageMagick Library"
description: "Yeah, stop using RMagick for now."
category: rubygems
tags: [rubygems, imagemagick, rmagick]
---
{% include JB/setup %}

The gist of it is `RMagick` is way out of date and isn't even compatible
with the latest `ImageMagick` anymore. So do yourself a favor and switch
to `mini_magick`. It purports to be faster and as far as I know, is
less brittle regarding future compatibility.
