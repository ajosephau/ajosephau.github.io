---
layout: post
section-type: post
has-comments: true
title: 'A simple way to create arrays for Drupal testing'
category: posts
tags: ['Drupal 7', 'Module development']
---

So after not playing Company of Heroes.... I'm back on Drupal module development, in particular how to create tests as quickly as possible.

I found two things:

You can print out php arrays, classes etc pretty easily by using the "var\_export($array,TRUE)" function (thanks Stack overflow! stackoverflow.com/questions/6759864/how-to-create-an-array-from-var-dump-result )

And when you get things like "stdClass::\_\_set\_state()" you can replace it with a cast to object, like "(object)". Thanks Drupal forums... https://drupal.org/node/584672

Now there's no excuse for not testing your code :-)!