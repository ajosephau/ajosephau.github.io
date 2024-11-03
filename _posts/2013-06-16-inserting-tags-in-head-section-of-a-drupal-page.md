---
layout: post
section-type: post
has-comments: true
title: 'Inserting tags in HEAD section of a Drupal page'
category: posts
tags: ['Drupal 7', 'Module development']
---

The "[hook\_html\_head\_alter()](https://api.drupal.org/api/drupal/modules!system!system.api.php/function/hook_html_head_alter/7)" can let you add tags to the HEAD section of a Drupal page. Despite some of the comments, I found that if you need to put it into a module in Drupal 7, you do need to name the hook after the module's name, instead of just "template\_"....

If you want to build tags... the _Drupal_ way :-P... try the function [theme\_html\_tag()](https://api.drupal.org/api/drupal/includes!theme.inc/function/theme_html_tag/7).

I found this was useful for a module I was writing... stay tuned people :-).