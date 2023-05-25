---
title: Add a logging function to your bash script
author: silviu
type: post
date: 2012-06-27T12:56:22+00:00
url: /2012/06/27/add-a-logging-function-to-your-bash-script/
dsq_thread_id:
  - 742254268
categories:
  - old
tags:
  - bash
  - logfile
  - temp_on

---
I write a lot of scripts that do various jobs and most of the time I&#8217;d like to have some log of what happened. So for most of them I add a function that helps logging.

[cce_bash]  
#!/bin/bash  
\# log date format, customize it to your wishes  
\# see man date for help  
DATE=&#8217;date +%Y/%m/%d:%H:%M:%S&#8217;  
\# log file  
LOG=&#8217;/var/log/script.log&#8217;

function echo_log {  
echo \`$DATE\`&#8221; $1&#8243; >> $LOG  
}  
\# start  
echo_log &#8220;Script running&#8221;  
\# do something  
echo_log &#8220;Doing this&#8221;  
\# done  
echo_log &#8220;Script ended  
[/cce_bash]