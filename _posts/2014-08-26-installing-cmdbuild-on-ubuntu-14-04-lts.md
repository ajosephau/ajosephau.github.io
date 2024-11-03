---
layout: post
section-type: post
has-comments: true
title: 'Installing cmdbuild on Ubuntu 14.04 LTS'
category: posts
tags: ['Programming', 'Systems Administration', 'Web']
---

So the instructions on the [Ubuntu wiki](https://help.ubuntu.com/community/CMDBuild) are good, but I found I had to make some slight changes in order to get it to work on the latest (at this time!) Ubuntu LTS version (14.04). I'm not too sure how secure the server is though... comments anyone? Here are the instructions I followed to get it to work

*   Install [ubuntu](http://releases.ubuntu.com/14.04/) on your platform (I'm using VirtualBox).
*   Start up the terminal app.
    *   [![Screen Shot 2014-08-26 at 11.02.46 am](/img/images/screen-shot-2014-08-26-at-11-02-46-am.png)](/img/images/screen-shot-2014-08-26-at-11-02-46-am.png)
*   Install Apache Tomcat by running:

```
sudo apt-get update
sudo apt-get install tomcat6 tomcat6-docs tomcat6-admin
```"tomcat6-docs" is optional.

*   Edit the tomcat user file:

```
sudo vi /etc/tomcat6/tomcat-users.xml
```...comment out the "<!-- ...-->" at the bottom of the <tomcat-users> tag. Copy and paste one of the <user> tags to "add a new user" with the "manager" role.

*   Edit the tomcat settings file:

```
sudo vi /etc/default/tomcat6
```...uncommenting the "TOMCAT6\_SECURITY=no" setting so we explicitly don't use the Java security manager iaw the original instructions. I'm inclined to uncomment the "LOGFILE\_DAYS=14" line to keep logfiles to:```
/var/log/tomcat6
```

*   Install postgresql and pgadmin3 (note to start pgadmin3 once it's installed, just search for it in the Unity search in the top left hand corner).

```
sudo apt-get install postgresql
sudo apt-get install pgadmin3
```

*   Set a password for the postgresql postgres user, replacing "INSERT\_PW\_HERE" with your password.

```
sudo -u postgres psql template1
ALTER USER postgres WITH PASSWORD 'INSERT\_PW\_HERE';
\\q
```

*   Download the [latest JDBC](http://jdbc.postgresql.org/download.html) (at writing time, given it's version 9.3.5 of postgresql and 1.7.0 of Java we'd need version JDBC41 - you can find this out by running "psql --version" and "java -version" respectively) and place it in the /usr/share/tomcat6/lib folder.
*   Download and extract the [cmdbuild](http://www.cmdbuild.org/en) to a folder, and move the <>/extras/tomcat-libs/x.y/\* to the /usr/share/tomcatZZ/lib folder, where x.y is the tomcat version being used (6.0 for me), and "tomcatZZ" is the folder holding Tomcat ie tomcat60 for me.
*   Rename the "cmdbuild.x.y.z.war" to just "cmdbuild.war"
*   Start Tomcat with the following command ("tomcat6" might change):

```
sudo /etc/init.d/tomcat6 start
```

*   Navigate to http://localhost:8080/manager/html , logging in with your credentials you set before in the tomcat-users.xml file.
*   Under "WAR file to deploy", select the "cmdbuild.war" and "Deploy" it. This takes a few seconds.
*   Go to http://localhost:8080/cmdbuild oncethepageis loaded and theWARfileis deployed. You should see the following settings page:
    *   [![Screen Shot 2014-08-26 at 4.09.24 pm](/img/images/screen-shot-2014-08-26-at-4-09-24-pm.png)](/img/images/screen-shot-2014-08-26-at-4-09-24-pm.png)
*   Enter in the following parameters for the database settings, tailoring when you like (especiallyfortheCMDBuild database.
    *   [![Screen Shot 2014-08-26 at 4.10.44 pm](/img/images/screen-shot-2014-08-26-at-4-10-44-pm.png)](/img/images/screen-shot-2014-08-26-at-4-10-44-pm.png)
*   Thenyouwill be prompted to log in with the username "admin" and password "admin" for the demo distribution.
    *   [![Screen Shot 2014-08-26 at 4.12.12 pm](/img/images/screen-shot-2014-08-26-at-4-12-12-pm.png)](/img/images/screen-shot-2014-08-26-at-4-12-12-pm.png)
---
### Comments:
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2015-06-16 16:24:21">Jun 2, 2015</time>

I'm really happy to hear you found my institutions useful!! Thank you :-)
<hr />
#### 
[Rune]( "runelog@outlook.com") - <time datetime="2015-06-16 15:22:23">Jun 2, 2015</time>

Thanks for sharing Anthony! You have saved me for hours of work! As I am a windows-man I found your instructions very helpful. Thank you!
<hr />
#### 
[Laurie Kepford]( "cloudlady911@gmail.com") - <time datetime="2015-04-23 02:57:59">Apr 4, 2015</time>

Anthony, thanks for the instructions. I am sure a lot of people have found this helpful, as I did. I have a question. I am looking for any information on running CMDBuild under Tomcat7. Have you tried that yet?
<hr />
#### 
[Computerlady911]( "laurie.kepford@gmail.com") - <time datetime="2015-04-23 15:33:07">Apr 4, 2015</time>

I haven't actually tried it yet. If I do, I will let you know how it goes.
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2015-04-23 15:22:37">Apr 4, 2015</time>

Laurie, thank you too - comments like yours keep on encouraging me to continue to blog on tech stuff :-). As for running CMDBuild under Tomcat 7, I haven't tried it... did you have any errors installing Tomcat 7, or deploying the .war file to Tomcat?
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "anthonyjoeyjo@gmail.com") - <time datetime="2015-04-23 15:36:11">Apr 4, 2015</time>

Good luck :-).
<hr />
#### 
[asdf]( "martin.lex@oikopolis.lu") - <time datetime="2017-04-29 00:41:36">Apr 6, 2017</time>

Did someone try with Ubuntu 16.04?
<hr />
#### 
[Anthony](http://anthonythecoder.wordpress.com "ajoseph811@gmail.com") - <time datetime="2017-05-03 01:53:44">May 3, 2017</time>

What operating system are you using?
<hr />
#### 
[egal]( "b@c.de") - <time datetime="2017-05-03 01:44:06">May 3, 2017</time>

Hi, after opening http://localhost:8080/cmdbuild i got a mistake: HTTP Status 500 - javax.servlet.ServletException: java.lang.NoSuchMethodError: org.postgresql.Driver.getVersion()Ljava/lang/String;
<hr />
#### 
[egal]( "b@c.de") - <time datetime="2017-05-03 17:16:15">May 3, 2017</time>

Ubuntu 16.04
<hr />
#### 
[William Pinelo Marin](https://plus.google.com/113925112496171531888 "wpinelo@gmail.com") - <time datetime="2017-01-20 03:44:23">Jan 5, 2017</time>

great work, thanks Anthony.
<hr />
