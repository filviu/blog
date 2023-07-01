---
title: Count traffic from an apache log file
author: silviu
type: post
date: 2014-03-03T07:12:19+00:00
url: /2014/03/03/count-traffic-from-an-apache-log-file/
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

```bash
awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }' access_log
```

This prints a result like this:

```bash
Total  28.4232 MB - Average  0.0108485 Mo - Access 2620
```

If you need to search for a particular date:
```bash
grep "02/Mar" access_log | awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }'
```

If you need to search for a particular resource:
```bash
grep "silly_large_cat_picture.jpg" access_log | awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }'
```

Of course you can combine:
```bash
grep "silly_large_cat_picture.jpg" access_log | grep "02/Mar" | awk '{ s += $10 } END { print "Total ", s/1024/1024 " MB", "- Average ", s/NR/1024/1024 " MB", "- Access ", NR }'
```

 [1]: https://stackoverflow.com/questions/8019742/measure-traffic-from-apache-access-log/21235691#21235691