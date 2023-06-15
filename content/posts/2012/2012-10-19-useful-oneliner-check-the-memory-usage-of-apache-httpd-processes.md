---
title: 'Useful oneliner: check the memory usage of apache / httpd processes'
author: silviu
type: post
date: 2012-10-19T09:44:20+00:00
url: /2012/10/19/useful-oneliner-check-the-memory-usage-of-apache-httpd-processes/
dsq_thread_id:
  - 891390415
categories:
  - old
tags:
  - apache
  - check
  - httpd
  - memory
  - resources
  - temp_on
  - usage

---
This is a handy one liner that reports the usage of the apache processes (apache2 on debian/ubunto or httpd in slackware, centos, etc)

[cc_bash]ps -ylC httpd | awk '{x += $8;y += 1} END {print "Apache Memory Usage (MB): "x/1024; print "Average Proccess Size (MB): "x/((y-1)*1024)}'[/cc_bash]