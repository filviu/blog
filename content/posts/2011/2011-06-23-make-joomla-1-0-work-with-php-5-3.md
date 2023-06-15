---
title: Make Joomla 1.0 work with PHP 5.3
author: silviu
type: post
date: 2011-06-23T10:43:03+00:00
url: /2011/06/23/make-joomla-1-0-work-with-php-5-3/
dsq_thread_id:
  - 340121199
categories:
  - old
tags:
  - apache
  - joomla
  - linux
  - php
  - temp_on

---
With the recent posts regarding resurrecting old stuff, recently I had to resurrect a Joomla 1.0 site. Soon enough I discovered that the home page doesn't display correctly. No errors, just lots of white space :). The problem is that Joomla 1.0 is not really made for PHP 5.3. Of course I could have started a virtual machine with the right environment but I wanted it running along some newer sites. Here's an easy fix:

Edit **./includes/Cache/Lite/Function.php**, find the line reading

[ccNe_php]
$arguments = func_get_args();
[/ccNe_php]

and replace with:

[cce_php]
$arguments = func_get_args();
$numargs = func_num_args();
for($i=1; $i < $numargs; $i++){
$arguments[$i] = &$arguments[$i];
}
[/cce_php]
Check now, it should be working. Enjoy your new _old_ site 🙂

 