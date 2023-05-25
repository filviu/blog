---
title: Remove duplicates from the current folder
author: silviu
type: post
date: 2012-09-04T12:01:28+00:00
url: /2012/09/04/remove-duplicates-from-the-current-folder/
dsq_thread_id:
  - 830859529
categories:
  - old
tags:
  - clean
  - cleaner
  - command line
  - duplicate
  - fdupes
  - linux
  - remove
  - remover
  - script
  - temp_on

---
I needed today to remove duplicate files from a big folder (8Gb+, 10000+ files). I use the nice <a href="http://code.google.com/p/fdupes/" target="_blank" rel="noopener">fdupes</a> program written by Adrian Lopez  
[cci\_bash]fdupes -rdN .[/cci\_bash]  
Note the point after the parameters. That means to search inside the current folder. A path could be provided instead of it. The options are:

  * **-r** means search recursively
  * **-d** means delete. use carefully and read the man page to understand what could go wrong!
  * **-N** means &#8220;no prompt&#8221;, i.e. the program will not ask which file to keep when multiple are found (I didn&#8217;t care, you might)