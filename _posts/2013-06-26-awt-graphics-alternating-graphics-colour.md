---
layout: post
section-type: post
has-comments: true
title: 'Alternating AWT graphics colour'
category: posts
tags: ['AWT', 'Java', 'UI']
---

It is possible to draw 2D colours in such a way that it inverts colours behind it, like in the screenshot below:

[![line colour](http://anthonythecoder.files.wordpress.com/2013/06/line-colour.png)](http://anthonythecoder.files.wordpress.com/2013/06/line-colour.png)

This can be done by enabling “XOR Colour mode” and by using...

```
Color.WHITE
```...this is because white has an RGB value of 255,255,255, and XOR’ing these values will cause the alternating effect.

The following code example shows this:

```
graphics.setXORMode(Color.WHITE);
graphics.drawLine(x, delegate.getXAxisHeight(), x, delegate.getDiagramRect().height + delegate.getXAxisHeight());
graphics.setColor(Color.BLACK);
```Don’t forget to save the previous colour (using graphics.getColor())and then reset it after drawing this alternative-coloured line.