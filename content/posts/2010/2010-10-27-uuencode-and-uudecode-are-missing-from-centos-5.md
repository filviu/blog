---
title: uuencode and uudecode are missing from CentOS 5
author: silviu
type: post
date: 2010-10-27T10:10:52+00:00
url: /2010/10/27/uuencode-and-uudecode-are-missing-from-centos-5/
dsq_thread_id:
  - 326419707
categories:
  - old
tags:
  - centos
  - temp_on
  - uudecode
  - uuencode
  - yum

---
What a surpriese. I need those sometimes when mailing things from cron so after a quick search around I found the (intuitive named) package that contains those utilities is **sharutils**.

```bash
yum install sharutils

Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
Excluding Packages in global exclude list
Finished
Setting up Install Process
Resolving Dependencies
-> Running transaction check
-> Package sharutils.x86_64 0:4.6.1-2 set to be updated
-> Finished Dependency Resolution

Dependencies Resolved

========================================================================================================================================
Package Arch Version Repository Size
========================================================================================================================================
Installing:
sharutils x86_64 4.6.1-2 base 203 k

Transaction Summary
========================================================================================================================================
Install 1 Package(s)
Upgrade 0 Package(s)

Total download size: 203 k
Is this ok [y/N]: y
Downloading Packages:
sharutils-4.6.1-2.x86_64.rpm | 203 kB 00:00
Running rpm_check_debug
Running Transaction Test
Finished Transaction Test
Transaction Test Succeeded
Running Transaction
Installing : sharutils 1/1

Installed:
sharutils.x86_64 0:4.6.1-2

Complete!
```