---
layout: post
section-type: post
has-comments: true
title: 'A basic setup for Log4j when using Freemarker'
category: posts
tags: ['Freemarker', 'log4j', 'Programming']
---

So I'm using Log4j in a project I'm working on, and I kept getting warnings from log4j when starting to use Freemarker...

```
log4j:WARN No appenders could be found for logger (freemarker.cache).
log4j:WARN Please initialize the log4j system properly.
log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
```In order to resolve these issues, I had to import the following classes:```
import freemarker.log.Logger;
import org.apache.log4j.BasicConfigurator;
```...And run the following commands:```
Logger.selectLoggerLibrary(Logger.LIBRARY\_LOG4J);
BasicConfigurator.configure();
```Happy logging and templating!!
---
### Comments:
#### 
[Bill]( "william.nelson.dev@gmail.com") - <time datetime="2018-12-05 04:33:37">Dec 3, 2018</time>

Hi- Thanks for posting this, I am getting the same error and hope that your solution will solve my issue as well. When you say, "and run the following commands...", where exactly did you run those commands, or put those lines in your code? Thanks in advance, -Bill
<hr />
