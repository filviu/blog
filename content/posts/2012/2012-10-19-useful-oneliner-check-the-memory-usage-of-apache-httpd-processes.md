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

[cc\_bash]ps -ylC httpd | awk &#8216;{x += $8;y += 1} END {print &#8220;Apache Memory Usage (MB): &#8220;x/1024; print &#8220;Average Proccess Size (MB): &#8220;x/((y-1)*1024)}'[/cc\_bash]