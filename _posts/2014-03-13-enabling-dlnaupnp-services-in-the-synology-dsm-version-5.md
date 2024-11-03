---
layout: post
section-type: post
has-comments: true
title: 'Enabling DLNA/uPnP services in the Synology DSM version 5'
category: posts
tags: ['Synology', 'Systems Administration']
---

So something new I noticed in the latest Synology firmware: there's a firewall feature now available. But I found it conflicted with my DLNA/uPnP server. So how did I fix this?

Firstly, I restarted the "Media Server" (it's at the Package Center, selecting the Media server and then stopping and starting the server).

[![screen-shot-2014-05-06-at-7-16-37-pm](http://anthonythecoder.files.wordpress.com/2014/05/screen-shot-2014-05-06-at-7-16-37-pm.png?w=300)](http://anthonythecoder.files.wordpress.com/2014/05/screen-shot-2014-05-06-at-7-16-37-pm.png)

When I started the server, the very intelligent firewall opened a prompt to let me know that the firewall was blocking the DLNA/uPnP server which needed to allow the service.

Need to check the firewall settings? Go to the Control Panel, and under Connectivity select Security - the firewall settings has a separate tab.