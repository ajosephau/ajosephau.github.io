---
layout: post
section-type: post
has-comments: true
title: 'Casting integers from objects... (and other primitives too)'
category: posts
tags: ['Java']
---

In Java, if you are 100% sure you've got an Integer in the form of an Object and you want to convert it to an "int" type...

```
Object obj;
int val = ((Integer) obj).intValue();
```And this works with other primitive data types also.