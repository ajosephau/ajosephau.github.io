---
layout: post
section-type: post
has-comments: true
title: 'Converting ESRI Shapefiles to CSVs using QGIS'
category: posts
tags: ['Programming', 'QGIS']
---

So I've been trying to export the data from the AMSA (the digital data from https://www.operations.amsa.gov.au/Spatial/DataServices/DigitalData which contains about 1 million data points per month). And I found a way to export the shapefile's data to a CSV file :D!

1.  Install QGIS from Kyngchaos for Mac users!! http://www.kyngchaos.com/software/qgis
2.  Drag the ".shp" and drop it into the "Layers" panel on the left hand panel
3.  Click on the layer and then on the menu item, and select Layers --> Save As
4.  Select "Comma Separated Values", and select a file to save to. It might probably pay to check which projection you're saving it to, but I found it's smart enough to use the same projection the source file uses.
5.  Click OK.
---
### Comments:
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2014-01-31 17:16:59">Jan 5, 2014</time>

I'm glad you are glad :-)!
<hr />
#### 
[Justin]( "justin.d.beck@hotmail.com") - <time datetime="2014-01-29 20:30:00">Jan 3, 2014</time>

I'm glad I found out you know how to do this!
<hr />
