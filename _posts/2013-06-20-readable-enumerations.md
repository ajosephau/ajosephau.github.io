---
layout: post
section-type: post
has-comments: true
title: '"Readable" Enumerations'
category: posts
tags: ['Java']
---

It is possible to use an enumeration but to also assign a “Human Readable” version of the enumerated values.

```
public enum AutofillType {
NONE("None"),
CATEGORY\_1("Category 1"),
CATEGORY\_2("Category 2"),
CATEGORY\_3("Category 3");

   public final String name;
   private AutofillType (String name)
   {
      this.name = name;
   }
   @Override
   public String toString() {
      return name;
   }
}
Therefore, you can do something like:

```
System.out.println(AutofillType.CATEGORY\_1);
```
And get the following output:
```
Category 1
```
Instead of:
```
CATEGORY\_1
```
I found it was useful for creating a 'taxonomy' style, fixed vocabulary and you want to make it easy to put a 'human-readable' version... might not be internationalize-able (and there's probably smarter ways of doing this out there!)...


```