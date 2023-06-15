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

- the PYTHONPATH had to be exported prior to running, or the script will fail because it requires `gdata-python-client`
- the LANG envronment has to be set otherwise it will spill the following error in the log (if you bother to log the output from cron that is, otherwise it will just not work and you won't know why, because the script works fine when ran manually)

```bash
Traceback (most recent call last):
File "/usr/local/bin/gcp.py", line 541, in
main()
File "/usr/local/bin/gcp.py", line 537, in main
parse_user_input() # Check to see we have the right options or exit
File "/usr/local/bin/gcp.py", line 519, in parse_user_input
export_documents(document_source, document_target, options)
File "/usr/local/bin/gcp.py", line 222, in export_documents
export_filename = target_path + "/" + sanatize_filename(entry.title.text)
File "/usr/local/bin/gcp.py", line 72, in sanatize_filename
filename = filename.decode(sys.getfilesystemencoding())
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc4 in position 3: ordinal not in range(128)
```

In order to fix it my backup script now looks like this:
```bash
#!/bin/bash
echo "Syncing Google Docs"
export PYTHONPATH="/usr/lib64/python2.7/site-packages"
export LANG=en_US
/usr/local/bin/gcp.py -ou -p"xxxxxxxxx" example@gmail.com:/ /backups/google/docs
```

 [1]: https://code.google.com/p/gdatacopier/