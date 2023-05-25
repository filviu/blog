---
title: Adding pcntl_fork support on a cpanel server
author: silviu
type: post
date: 2012-02-01T09:20:13+00:00
url: /2012/02/01/adding-pcntl_fork-support-on-a-cpanel-server/
dsq_thread_id:
  - 560433998
categories:
  - old
tags:
  - cpanel
  - easyapache
  - pcntl
  - php
  - temp_on

---
A php application on a cpanel server kept throwing this:

[cceN_bash]  
Fatal error: Call to undefined function pcntl_fork() in /path/blah.php on line 5  
[/cceN_bash]

The fix requires recompiling php with **&#8211;enable-pcntl** Fortunately cpanel offers the Easy Apache script. The bad part is that it doesn&#8217;t have an option for pcntl. So you have to specify it as a custom compile time option. Edit (or create &#8211; for PHP5) and add **/var/cpanel/easy/apache/rawopts/all_php5**  
[cceN_bash]  
&#8211;enable-pcntl  
[/cceN_bash]  
On one line

Then rebuild Easy Apache.

&nbsp;