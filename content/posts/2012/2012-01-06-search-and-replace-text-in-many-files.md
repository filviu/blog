---
title: Search and replace text in many files
author: silviu
type: post
date: 2012-01-06T07:48:46+00:00
url: /2012/01/06/search-and-replace-text-in-many-files/
dsq_thread_id:
  - 529416655
categories:
  - old
tags:
  - bash
  - perl
  - regexp
  - replace
  - search
  - temp_on

---
This is a handy one liner that searches and replaces text in multiple files. (You can use [find][1] for example to run it in multiple folders)  
[ccNe_bash]  
perl -pi -e &#8216;s/old\_text/new\_text/g&#8217; *.conf  
[/ccNe_bash]  
This line replaces old\_text with new\_text in all the .conf files in the current folder. Of course you can use regular expressions.

 [1]: http://manpages.sgvulcan.com/find.1.php