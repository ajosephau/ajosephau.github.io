---
layout: post
section-type: post
has-comments: true
title: 'Monitoring a shell script (external job) running on CentOS with Jenkins'
category: posts
tags: ['Systems Administration', 'Web']
---

So I wanted to setup Jenkins external monitoring on a web server I have on a Centos VM, and I found a combination of these three blog posts worked!

*   [http://kvdev.wordpress.com/2012/03/01/jenkins-monitoring-external-jobs/](http://kvdev.wordpress.com/2012/03/01/jenkins-monitoring-external-jobs/)
*   [http://stackoverflow.com/questions/11830098/setup-jenkins-to-monitor-external-job](http://stackoverflow.com/questions/11830098/setup-jenkins-to-monitor-external-job)
*   [https://gist.github.com/junaid18183/8450761](https://gist.github.com/junaid18183/8450761)

Firstly, run the following commands :```
wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
yum -y install jenkins
```... or download the RPM at [http://pkg.jenkins-ci.org/redhat/](http://pkg.jenkins-ci.org/redhat/) and run "rpm -Uhv jenkinx\*.rpm"

*   run the following:

```
cd /usr/lib/jenkins
unzip /usr/lib/jenkins/jenkins.war
```

*   Install OpenJDK while you're at it.
*   Go to Jenkins and create a "Monitor an external job" called "New Job"

```
\* Create an environment variable by 
$export JENKINS\_HOME=http://jenkins\_host:8080 , replacing "jenkins\_host" with the server running Jenkins
```

*   To have Jenkins monitor a script, run a command like the following...

```
java -jar /usr/lib/jenkins/WEB-INF/lib/jenkins-core-\*.jar “New Job” /path\_to/myreport.sh 2>&1 > /dev/null
```And you can put that command in a cron job too!