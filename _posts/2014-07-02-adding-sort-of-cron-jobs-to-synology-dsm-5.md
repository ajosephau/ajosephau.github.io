---
layout: post
section-type: post
has-comments: true
title: 'Adding sort-of cron jobs to Synology DSM 5'
category: posts
tags: ['Synology', 'Systems Administration']
---

I wanted to write a cron job to run a php script, so I found a way to regularly call a php script.

Go to the Control Panel, and click on "Task Scheduler" under "System". Select "Create" --> "User-defined script".

Under "User-defined script", type in the following...

```
curl "http://example.com/cron.php"
```...replacing```
"http://example.com/cron.php"
```with whatever script you run. I've found it seems to work well with regular cron jobs like a Dynamic DNS (DDNS) update.

**UPDATE: See Simon's comment below for more information on scheduling tasks!**
---
### Comments:
#### 
[Simon Edwards]( "simon@edwardsmail.eu") - <time datetime="2014-12-09 21:21:34">Dec 2, 2014</time>

Many thanks for your explanation. I had missed this section of DSM and was editing the crontab directly to perform the same task. This gui is much less hassle. It may be worth knowing two things about these scheduled tasks: 1) That the actual driver of these tasks is cron itself. Each task gets entered into the crontab as follows:- 0 1 \* \* \* root /tmp/synoschedtask --run id=1 Each time you add a new task a new line goes into the crontab and the id number in the new task increases by one. 2) All tasks will execute as the root user. However the execution environment is not quite the same as the shell path when logged in as root. This means that scripts that run just fine from the command prompt may not run well as a scheduled task. For instance if your script drives "java" you will have to insert the full path to "java" in order for it to execute within the scheduled script. A failure to find a command due to a missing path will result in a silent failure. Followed by much scratching of your head whilst you figure out what went wrong. If your script doesn't work first time, appending 2>&1 >> /volume1/public/logfile.txt to the end of each line should trap most of your errors to the logfile and let you correct them. Even then it didn't catch the missing path error for "java", which was truly a silent failure.
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2014-12-10 13:05:21">Dec 3, 2014</time>

Thank you for your feedback - you hit the nail on the head with all of your points :D.
<hr />
#### 
[Half a Page of Scribbled Linux :: Back Up Trello to Synology NAS](http://www.familytidings.com/blog/?p=1397 "") - <time datetime="2015-02-16 07:44:52">Feb 1, 2015</time>

\[…\] Synology has their own cron and from what I Googled, it’s rather picky. They also have an interface to it in the Control Panel. This was also picky, but here’s how I got it to \[…\]
<hr />
#### 
[danscottc79]( "danscottc79@gmail.com") - <time datetime="2016-02-10 19:56:28">Feb 3, 2016</time>

Hi Anthony, What I am doing is using a programme called mc2xml to generate a xmltv file for my EPG. I copy the file over to one of my shared folders on the NAS. Before I set up a cron job or use the task scheduler I decided to test with Terminal on my Mac first. When I run mc2xml on my Mac it produces 2 files in the directory I run it from. The command I am using is: /volume1/Nas\_share/mc2xml -c gb -g "My postcode" It generates the the files correctly but they end up in the root, where I can't access from Openlec and can't make it NFS because they are not in a actual folder. I'm probably missing something here as I am fairly new to using Terminal. Any help would be great. Thanks.
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2016-02-10 11:22:27">Feb 3, 2016</time>

It depends a little on what process you are running, but you can change the script you are running to either: - tell the process to write the output of the process to a file. Like curl for instance (and some programs tend to do this), you would say "curl http://google.com -o /path/to/file.txt", or - redirect the output of the process using the ">" operator. Like for instance, "ls > files.txt". Hope that helps :-)
<hr />
#### 
[danscottc79](http://gravatar.com/danscottc79 "danscottc79@gmail.com") - <time datetime="2016-02-10 10:44:17">Feb 3, 2016</time>

Hi i was wondering if you could help.When I run a script in Task Scheduler. it is running the file I want but the output is going to the root instead of the folder the file is ran in like it should. Would you be able to shed some light how I can stop this happening? Thanks
<hr />
#### 
[DerZyklop]( "onesie-anthonythecoder.wordpress.com@der-zyklop.de") - <time datetime="2016-10-23 22:39:47">Oct 0, 2016</time>

Thanks for this post, and thanks for your comment on my Blog. I added a hint to my article. http://der-zyklop.de/panel/pages/blog/the-reconnection-of-vpn-profile-onsynology-nas-has-failed/edit
<hr />
#### 
[danscottc79]( "danscottc79@gmail.com") - <time datetime="2016-02-10 19:58:03">Feb 3, 2016</time>

You can ignore the -c and -g commands, they are just to select the right region for the TV guide.
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2016-02-11 11:11:10">Feb 4, 2016</time>

So I looked up mc2xml.hosterbox.net and it looks like adding "-o /path/to/output/file" should work, in addition to your other parameters...
<hr />
