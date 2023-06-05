---
title: Cadsoft Eagle on Slackware Current 64bit
author: silviu
type: post
date: 2012-01-11T09:00:29+00:00
url: /2012/01/11/cadsoft-eagle-on-slackware-current-64bit/
dsq_thread_id:
  - 534787699
categories:
  - old
tags:
  - cadsoft
  - current
  - eagle
  - eaglepcb
  - slackwre
  - temp_on

---
I want to start building some new electronics projects and I wanted to use some tool to build my schematics. Even if not open source <a href="http://www.cadsoftusa.com/" target="_blank" rel="noopener">Cadsoft's Eagle</a> seems to be the de-facto standard between hobbyists.

Unfortunately trying to run the setup on Slackware gives the errors regarding to  
[ccNe_bash]  
/&#8230;/bin/eagle: error while loading shared libraries: libssl.so.1.0.0: cannot open shared object file: No such file or directory  
[/ccNe_bash]  
libssl.so.1.0.0 and libcrypto.so.1.0.0

I run a multilib setup so that's not it. It turns that all I had to do was:  
[cce_bash]  
cd /lib  
ln -s libssl.so.0.9.8 libssl.so.1.0.0  
ln -s libcrypt-2.14.1.so libcrypto.so.1.0.0  
[/cce_bash]  
in **/lib**

Hope that helps.