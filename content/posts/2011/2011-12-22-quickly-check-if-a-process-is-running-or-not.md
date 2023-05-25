---
title: Quickly check if a process is running or not
author: silviu
type: post
date: 2011-12-22T08:29:02+00:00
url: /2011/12/22/quickly-check-if-a-process-is-running-or-not/
dsq_thread_id:
  - 513099688
categories:
  - old
tags:
  - bash
  - cli
  - command line
  - linux
  - process
  - temp_on

---
When writting bash scripts one often needs to see if a process is running or not  
I like the following code; though I&#8217;m sure many ways of doing this exists, what&#8217;s your favorite?  
[cce_bash]  
if [ -z &#8220;$(pgrep process)&#8221; ]  
then  
echo &#8220;process is not running&#8221;  
else  
echo &#8220;process is running&#8221;  
fi  
[/cce_bash]