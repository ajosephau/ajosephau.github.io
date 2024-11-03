---
layout: post
section-type: post
has-comments: true
title: 'Changing AWT line thickness'
category: posts
tags: ['AWT', 'Java', 'UI']
---

To change the line thickness from thin bands to thicker bands, like below:

[![line thickness](http://anthonythecoder.files.wordpress.com/2013/06/line-thickness1.png)](http://anthonythecoder.files.wordpress.com/2013/06/line-thickness1.png)

Set the “stroke” size used on the Graphics2D object:

```
 
   Graphics2D graphicsSG2D = ((Graphics2D) graphics);
   if(graphics instanceof Graphics2D) 
   {
      stroke = graphicsSG2D.getStroke();
      graphicsSG2D.setStroke(new BasicStroke(3));
   }

   if(graphics instanceof Graphics2D && stroke != null)
   {
      graphicsSG2D.setStroke(stroke);
   }
```

Don’t forget to save the previous stroke type, using

```
graphics2D.getStroke()
```

and then reset it after drawing this alternative-thickness line.