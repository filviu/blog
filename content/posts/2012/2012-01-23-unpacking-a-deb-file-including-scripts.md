---
title: Unpacking a .deb file (including scripts)
author: silviu
type: post
date: 2012-01-23T10:11:54+00:00
url: /2012/01/23/unpacking-a-deb-file-including-scripts/
dsq_thread_id:
  - 549495369
categories:
  - old
tags:
  - deb
  - debian
  - extract
  - package
  - script
  - slackware
  - tar.gz
  - temp_on
  - tgz

---
While attempting to install a deb package on a slackware system I wanted to check the install script that the package runs. I tried the deb2tgz utility but unfortunately that only left me the files in the package in a ready to install .tgz file.

Here's how to unpack a .deb to obtain both scripts and files:


```bash
cd /tmp/somefolder
tar x somepackage.deb
```
This leaves you with two files:

`control.tar.gz` and `data.tar.gz` The first contains the pre and post install scripts and the second contains the files.
