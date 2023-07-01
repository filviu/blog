---
title: Search and replace text in many files
author: silviu
type: post
date: 2012-01-06T07:48:46+00:00
url: /2012/01/06/search-and-replace-text-in-many-files/
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

```bash
perl -pi -e 's/old_text/new_text/g' *.conf
```

This line replaces old_text with new_text in all the .conf files in the current folder. Of course you can use regular expressions.

 [1]: http://manpages.sgvulcan.com/find.1.php