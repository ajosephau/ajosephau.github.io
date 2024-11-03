---
layout: post
section-type: post
has-comments: true
title: 'Deploying your own copy of Bushfire Connect'
category: posts
tags: ['Bushfire Connect', 'Web']
---

[![logo3](/img/images/logo3.png)](/img/images/logo3.png)

So I worked on this awesome community startup Bushfire Connect. It is with a bit of sadness that I write this, given that we shut down our service a few years ago, but I wanted to put a note here on how to redeploy Bushfire Connect on your web server.

Please note this is a somewhat cut-down version of the Bushfire Connect we ran: all of the usernames and passwords have been stripped and a sole "admin" account is included.

Prerequisites
=============

Your standard Linux/Apache/MySQL/PHP web server. Please note this hasn't had many security patches applied so it's likely to have unpatched security vulnerabilities, so be careful!

Loading the database
====================

Go to [https://github.com/ajosephau/Bushfire-Connect/blob/master/database/bushfireconnect\_live.sql](https://github.com/ajosephau/Bushfire-Connect/blob/master/database/bushfireconnect_live.sql) and download the SQL file and import it to a MySQL database using your database management app of choice (like phpMyAdmin).

Uploading the web files
=======================

Download all the files at: https://github.com/ajosephau/Bushfire-Connect/tree/master/ushahidi and upload them to your web server (let's say you upload it to your a subfolder called "bushfireconnect" in your web root folder (like /var/www/html).

edit the application/config/database.php with the appropriate config as below for the database (replace "TODO\_TEXT" with relevant parameters.)

```
$config\['default'\] = array
 (
 'benchmark' => TRUE,
 'persistent' => FALSE,
 'connection' => array
 (
 'type' => 'mysql',
 'user' => 'TODO\_TEXT\_DATABASE\_USERNAME',
 'pass' => 'TODO\_TEXT\_DATABASE\_USERNAME\_PASSWORD',
 'host' => 'TODO\_TEXT\_DATABASE\_HOSTNAME',
 'port' => FALSE,
 'socket' => FALSE,
 'database' => 'TODO\_TEXT\_DATABASE\_NAME'
 ),
 'character\_set' => 'utf8',
 'table\_prefix' => '',
 'object' => TRUE,
 'cache' => FALSE,
 'escape' => TRUE
 );
```From the web server's console run the following commands```
chmod 777 application/config/config.php
chmod 777 application/config
chmod 777 application/cache
chmod 777 application/logs
chmod 777 media/uploads
chmod 777 .htaccess
```Edit application/config/config.php so it has:```
$config\['site\_domain'\] = 'localhost/bushfireconnect/';
$config\['site\_protocol'\] = 'http';
$config\['index\_page'\] = 'index.php';
$config\['internal\_cache'\] = FALSE;
```Changing "localhost" to whatever your domain name is, and "bushfireconnect" to the subdirectory you uploaded the files to. And lastly login as an administrator at http://localhost/ushahidi/index.php/login with the username "admin" and password "adm1n1st2011"

Some pretty usage statistics
============================

[![screenshot1](/img/images/screenshot1.png?w=274)](/img/images/screenshot1.png)

[![screenshot2](/img/images/screenshot2.png?w=300)](/img/images/screenshot2.png)

[![screenshot3](/img/images/screenshot3.png?w=300)](/img/images/screenshot3.png)