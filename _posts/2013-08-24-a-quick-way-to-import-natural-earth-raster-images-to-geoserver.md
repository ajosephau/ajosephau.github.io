---
layout: post
section-type: post
has-comments: true
title: 'A quick way to import Natural Earth raster images to GeoServer'
category: posts
tags: ['GeoServer', 'Web']
---

*   Start up your GeoServer instance and log in as an admin.
*   Go to Data --> Workplaces.
*   Click "Add new workplace".
*   Enter a new name and URI.
*   Go to Data --> Stores
*   Click "Add new Store"
*   Click "WorldImage" (under Raster Data Sources)
*   Create a data source name and select the tiff file you want to upload.
*   Under "Coordinate Reference Systems", pick one like "900913" (don't know which one to use, but this one works?)
*   Click save.
*   If you want, go to Data -> Layer  Preview, and select the layer to see it in openlayers.