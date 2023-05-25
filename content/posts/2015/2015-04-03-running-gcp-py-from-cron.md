---
title: Running gcp.py from cron
author: silviu
type: post
date: 2015-04-03T10:16:22+00:00
url: /2015/04/03/running-gcp-py-from-cron/
dsq_thread_id:
  - 3651623792
categories:
  - old
tags:
  - backup
  - bash
  - drive
  - google
  - sync
  - temp_on

---
On my backup server I run gcp.py from [gdatacopier][1] to backup my google docs. I had to fix two issues in order to get it to run from a bash script:

&#8211; the PYTHONPATH had to be exported prior to running, or the script will fail because it [cci\_bash]requires gdata-python-client[/cci\_bash]

&#8211; the LANG envronment has to be set otherwise it will spill the following error in the log (if you bother to log the output from cron that is, otherwise it will just not work and you won&#8217;t know why, because the script works fine when ran manually)

[cce_bash]  
Traceback (most recent call last):  
File &#8220;/usr/local/bin/gcp.py&#8221;, line 541, in  
main()  
File &#8220;/usr/local/bin/gcp.py&#8221;, line 537, in main  
parse\_user\_input() # Check to see we have the right options or exit  
File &#8220;/usr/local/bin/gcp.py&#8221;, line 519, in parse\_user\_input  
export\_documents(document\_source, document_target, options)  
File &#8220;/usr/local/bin/gcp.py&#8221;, line 222, in export_documents  
export\_filename = target\_path + &#8220;/&#8221; + sanatize_filename(entry.title.text)  
File &#8220;/usr/local/bin/gcp.py&#8221;, line 72, in sanatize_filename  
filename = filename.decode(sys.getfilesystemencoding())  
UnicodeDecodeError: &#8216;ascii&#8217; codec can&#8217;t decode byte 0xc4 in position 3: ordinal not in range(128)  
[/cce_bash]

In order to fix it my backup script now looks like this:  
[cce_bash]  
#!/bin/bash  
echo &#8220;Syncing Google Docs&#8221;  
export PYTHONPATH=&#8221;/usr/lib64/python2.7/site-packages&#8221;  
export LANG=en_US  
/usr/local/bin/gcp.py -ou -p&#8221;xxxxxxxxx&#8221; example@gmail.com:/ /backups/google/docs  
[/cce_bash]

 [1]: https://code.google.com/p/gdatacopier/