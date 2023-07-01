---
title: Quickly check if a process is running or not
author: silviu
type: post
date: 2011-12-22T08:29:02+00:00
url: /2011/12/22/quickly-check-if-a-process-is-running-or-not/
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
I like the following code; though I'm sure many ways of doing this exists, what's your favorite?

```bash
if [ -z "$(pgrep process)" ]; then
    echo "process is not running"
else
    echo "process is running"
fi
```