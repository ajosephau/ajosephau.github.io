---
layout: post
section-type: post
has-comments: true
title: 'Hack something first: a lesson in input validation'
category: posts
tags: ['Infosec', 'Programming', 'Systems Administration']
---

I wanted to write up a lesson I learnt from a certain app (won't mention which one here, even though the vulnerability was reported and patched rather quickly!) that offered in-app currency if you sent your friends an SMS from your phone's contacts to invite them to the service.

I found that if you gave it a fake number, the app would give you the free credits, without checking if it had a 20 digit number!! So always check that you get valid input: even if it's from a place you'd assume that would be valid like a phone's contacts.