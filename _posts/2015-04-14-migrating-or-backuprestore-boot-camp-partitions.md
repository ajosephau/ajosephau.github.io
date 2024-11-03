---
layout: post
section-type: post
has-comments: true
title: 'Migrating (or Backup/Restore) Boot Camp partitions on OSX Yosemite and older'
category: posts
tags: ['OSX', 'Systems Administration']
---

Update: I tried installing the app on OSX El Capitan, and there's a big warning about OS incompatibility...

![Screen Shot 2015-12-08 at 12.21.56](/img/images/screen-shot-2015-12-08-at-12-21-56.png?w=300)

* * *

I found a (free!) way to migrate my boot camp partition from one hard drive to another. I used Paragon's Boot Camp Backup (http://www.paragon-software.com/home/bootcamp-backup/) and:

*   create a back up of my boot camp partition from the old hard drive,
*   installed OSX and Boot Camp Backup on the new hard drive (with a new partition for Boot Camp),
*   In order to enable the "restore" feature, I selected the newly created Boot Camp partition as the "source" and select the "destination" as the backup image created in the first step... click on the "Restore" tab and then restore the image to the new partition!

Never tried the alternatives like WinClone, but since I don't really do this often I didn't want to pay for it :-).
---
### Comments:
#### 
[neil]( "foreverneilyoung@googlemail.com") - <time datetime="2015-12-08 01:20:05">Dec 2, 2015</time>

Any new information on that? As far as I can see Paragon is not claiming to support El Capitan, so I would expect to have problems
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2015-12-08 11:23:55">Dec 2, 2015</time>

Doesn't look like there's a way to :-(...
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2016-03-03 13:07:08">Mar 4, 2016</time>

That is interesting... Thanks for sharing!
<hr />
#### 
[Allan]( "allan.wl@hotmail.com") - <time datetime="2015-10-14 12:35:58">Oct 3, 2015</time>

Im sorry but that simply doesnt work. I was in OSX Mountain Lion and I made a backup image of the bootcamp drive with paragon bootcamp backup. Then I upgraded the SSD and installed El Capitan. Reinstalled Paragon Backup but the Restore option is grayed-out. No matter what I cant migrate that backup image back to a FAT formatted partition so it becomes bootcamp again.
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2015-10-19 14:49:31">Oct 1, 2015</time>

Hmmm I haven't tried this with El Capitan - I'll give it a shot and let you know what I find out...
<hr />
#### 
[JasonPDX]( "anth-the-coder@getdistracted.net") - <time datetime="2016-03-03 09:54:36">Mar 4, 2016</time>

Might be late to the conversation, but I think you can find on the paragon website that this won't work for El Capitan. What will work however, (according to them) is their new product called Hard Disk Manager for Mac. You might give it a try. I just used it to backup my Win 10 bootcamp partition and it did so very quickly. I will have to see if it will restore it properly when I get the replacement macbook pro.
<hr />
