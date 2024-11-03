---
layout: post
section-type: post
has-comments: true
title: 'Accessing Drupal sandbox projects via the web'
category: posts
tags: ['Drupal 7', 'Module development', 'Programming']
---

EDIT: OK so there's an even easier way to do this...  Click on "Repository viewer" on the right hand menu under the "Development" heading

![Screenshot 2013-12-24 14.52.26](/img/images/screenshot-2013-12-24-14-52-26.png)

OK, so for some reason when I want to view Drupal modules I can't access them via the usual "git clone (git\_url\_here)" command.

So instead the source code can be accessed by going to drupalcode.org ... but how? Good question :D!

As an example, let's say you want to check out my sandbox project https://drupal.org/sandbox/ajosephau/2105389 ?

Go to http://drupalcode.org/sandbox/ajosephau/2105389.git

So the format is http://drupalcode.org/sandbox/"USERNAME"/"GIT\_REPO\_ID".git from the URL.

To download a particular version, click on the URL "snapshot" for a particular revision.