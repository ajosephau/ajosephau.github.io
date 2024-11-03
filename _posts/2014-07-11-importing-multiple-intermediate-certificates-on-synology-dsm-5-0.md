---
layout: post
section-type: post
has-comments: true
title: 'Importing multiple intermediate certificates on Synology DSM 5.0'
category: posts
tags: ['Synology', 'Systems Administration']
---

I recently bought an SSL certificate from Comodo, and when I got my certificate I also received two intermediate certificates...

The problem came when trying to import the two intermediate certificates... on the Synology DSM 5.0 firmware, there's only one field for the intermediate certificates...

[![Screen Shot 2014-07-11 at 12.09.35 pm](/img/images/screen-shot-2014-07-11-at-12-09-35-pm.png)](/img/images/screen-shot-2014-07-11-at-12-09-35-pm.png)

So how did I get both certificates into the one file? It's actually really simple - I combined the two certificates into a single, .crt file and then selected the combined file as the "intermediate certificate". The web server reboots and then there are no nasty Firefox/Crome errors like "sec\_error\_unknown\_issuer".

Thanks to this [serverfault](http://serverfault.com/questions/562369/how-to-install-multiple-intermediate-ca-certificate-files-on-apache) answer!
---
### Comments:
#### 
[David]( "djhalling@gmail.com") - <time datetime="2014-11-21 00:23:57">Nov 5, 2014</time>

Thank you so much. This was really helpful.
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2014-11-21 14:55:36">Nov 5, 2014</time>

You're more than welcome :-), I'm glad you found my post useful!
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2015-05-08 08:50:03">May 5, 2015</time>

I know, right? I'm glad you found it useful - and thank you for your tips too!
<hr />
#### 
[Vita]( "veris@volny.cz") - <time datetime="2015-05-06 19:32:18">May 3, 2015</time>

As unlikely as it seems this does actually work. Thank you very much. I wanted to install Starfield certificate with the intermediate but it was not easy. Thanks to your article I was able to resolve the last issue I had. I exported the two intermediate certificates from the p7b file - note for newbies, it has to be exported as Base-64 .cer file. Then merged them together in Notepad and saved as UTF-8. The I was finally able to import it. Thanks again
<hr />
