---
layout: post
section-type: post
has-comments: true
title: 'Interfacing Matlab to Java applications'
category: posts
tags: ['Java', 'Matlab']
---

For existing projects:

*   Open Matlab.
*   Navigate to the directory holding the Matlab project, and open the project file (going by the extension ".prj").
*   The "Deployment Tool" (which can be opened by typing "deploytool" in the prompt) will be opened.
*   If you are updating files, drag the Matlab files off the "Classes" list and drag the Matlab files onto the "Classes" list.
*   Click on :
    *   "Build" icon to make a "Jar" file of the compiled Matlab files or
    *   "Package" icon to make a self extracting executable of the Jar file, Javadoc files and a readme file.

For new projects:

*   Enter "deploytool" into the command window
*   Enter a name for the project, a folder and the target should be "Java Package".
*   Drag Matlab ".m" files that should be accessible to outside classes by dragging them as "Classes". Private functions can be dragged under "Shared Resources and Helper Files".
*   And you can click on either Build or Package by the above steps.

Note the Matlab Compiler Runtime is required to run these packages. More information is available [here](http://www.mathworks.com.au/products/compiler/mcr/index.html): http://www.mathworks.com.au/products/compiler/mcr/index.html.