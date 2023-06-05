---
title: Count traffic from an apache log file
author: silviu
type: post
date: 2014-03-03T07:12:19+00:00
url: /2014/03/03/count-traffic-from-an-apache-log-file/
dsq_thread_id:
  - 2350040141
categories:
  - old
tags:
  - apache
  - awk
  - log
  - temp_on
  - traffic

---
I had to count traffic made by a resource from the apache log files. If awstats had been installed it would have been an easy job, but it wasn't hard without it either. I used hints from [here][1] to build the following:

[cce_bash]  
awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }' access_log  
[/cce_bash]

This prints a result like this:

[cce_bash]  
Total  28.4232 MB - Average  0.0108485 Mo - Access 2620  
[/cce_bash]

If you need to search for a particular date:  
[cce_bash]  
grep "02/Mar" access_log | awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }'  
[/cce_bash]

If you need to search for a particular resource:  
[cce_bash]  
grep "silly\_large\_cat\_picture.jpg" access\_log | awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }'  
[/cce_bash]

Of course you can combine:  
[cce_bash]  
grep "silly\_large\_cat\_picture.jpg" access\_log | grep "02/Mar" | awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }'  
[/cce_bash]  
 

 [1]: https://stackoverflow.com/questions/8019742/measure-traffic-from-apache-access-log/21235691#21235691