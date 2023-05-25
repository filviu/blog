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
I had to count traffic made by a resource from the apache log files. If awstats had been installed it would have been an easy job, but it wasn&#8217;t hard without it either. I used hints from [here][1] to build the following:

[cce_bash]  
awk &#8216;{ s += $10 } END { print &#8220;Total &#8220;, s/1024/1024 &#8221; MB&#8221;, &#8220;- Average &#8220;, s/NR/1024/1024 &#8221; MB&#8221;, &#8220;- Access &#8220;, NR }&#8217; access_log  
[/cce_bash]

This prints a result like this:

[cce_bash]  
Total  28.4232 MB &#8211; Average  0.0108485 Mo &#8211; Access 2620  
[/cce_bash]

If you need to search for a particular date:  
[cce_bash]  
grep &#8220;02/Mar&#8221; access_log | awk &#8216;{ s += $10 } END { print &#8220;Total &#8220;, s/1024/1024 &#8221; MB&#8221;, &#8220;- Average &#8220;, s/NR/1024/1024 &#8221; MB&#8221;, &#8220;- Access &#8220;, NR }&#8217;  
[/cce_bash]

If you need to search for a particular resource:  
[cce_bash]  
grep &#8220;silly\_large\_cat\_picture.jpg&#8221; access\_log | awk &#8216;{ s += $10 } END { print &#8220;Total &#8220;, s/1024/1024 &#8221; MB&#8221;, &#8220;- Average &#8220;, s/NR/1024/1024 &#8221; MB&#8221;, &#8220;- Access &#8220;, NR }&#8217;  
[/cce_bash]

Of course you can combine:  
[cce_bash]  
grep &#8220;silly\_large\_cat\_picture.jpg&#8221; access\_log | grep &#8220;02/Mar&#8221; | awk &#8216;{ s += $10 } END { print &#8220;Total &#8220;, s/1024/1024 &#8221; MB&#8221;, &#8220;- Average &#8220;, s/NR/1024/1024 &#8221; MB&#8221;, &#8220;- Access &#8220;, NR }&#8217;  
[/cce_bash]  
&nbsp;

 [1]: https://stackoverflow.com/questions/8019742/measure-traffic-from-apache-access-log/21235691#21235691