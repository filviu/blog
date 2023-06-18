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

I write a lot of scripts that do various jobs and most of the time I'd like to have some log of what happened. So for most of them I add a function that helps logging.

```bash
#!/bin/bash
# log date format, customize it to your wishes
# see man date for help
DATE='date +%Y/%m/%d:%H:%M:%S'
# log file
LOG='/var/log/script.log'

function echo_log {
  echo "`$DATE` $1" >> $LOG
}
# start
echo_log "Script running"
# do something
echo_log "Doing this"
# done
echo_log "Script ended
```