---
layout: post
section-type: post
has-comments: true
title: 'Adding a configure link to a Drupal module'
category: posts
tags: ['Drupal 7', 'Module development']
---

If you want to add a "Configure" link to a module's entry in the 'Administration >> Modules' page, add the following line to a module's ".info" file:

> configure = path/to/admin/page

This path'll be in your hook\_menu() implementation.

Thanks to this bug report I found https://drupal.org/node/1582464