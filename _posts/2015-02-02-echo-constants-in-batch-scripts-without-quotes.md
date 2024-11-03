---
layout: post
section-type: post
has-comments: true
title: 'Echo constants in batch scripts without quotes'
category: posts
tags: ['Systems Administration', 'Windows']
---

Somewhat based on this [Stack Overflow post](http://http://stackoverflow.com/questions/804646/how-do-you-strip-quotes-out-of-an-echoed-string-in-a-windows-batch-file), I wanted to simplify the code to echo a constrant string without the quotation marks to the console in a Windows batch script., Here's the script to output the obligatory, "Hello world!" text

```
@echo OFF
SET variable="Hello World!"
ECHO %variable:"=%
```With the following output```
Hello World!
```
---
### Comments:
#### 
[Seb]( "sno@sno.som") - <time datetime="2018-10-29 18:49:37">Oct 1, 2018</time>

Does not work for me .. with < in the variable value !!! Great windows!
<hr />
