---
title: Rename all files in a folder from upper to lower case.
author: silviu
type: post
date: 2010-02-12T10:49:35+00:00
url: /2010/02/12/rename-all-files-in-a-folder-from-upper-to-lower-case/
dsq_thread_id:
  - 327467818
categories:
  - old
tags:
  - bash
  - folder
  - rename
  - script
  - temp_on

---
Sometimes is needed to have all files in a folder in the same case. Here&#8217;s a small script to rename all files in the folder to lower case:  
[ccNe_bash]  
for i in *; do mv $i \`echo $i | tr \[:upper:\] \[:lower:\]\`; done  
[/ccNe_bash]