---
title: How to check if TRIM is enabled on your SSD
author: silviu
type: post
date: 2010-07-23T10:07:24+00:00
url: /2010/07/23/how-to-check-if-trim-is-enabled-on-your-ssd/
dsq_thread_id:
  - 326479356
categories:
  - old
tags:
  - fsutil
  - ssd
  - temp_on
  - trim
  - Windows

---
### God a fancy new drive? SSD maybe? TRIM support advertised?

Well, here's how you can check if TRIM support is actually enabled and working in your windows installation:

Start a command prompt window (**WIN+R, type cmd and press enter**)

In the command prompt window type the following:

```shell
fsutil behavior query disabledeletenotify
```

![Checking the state of the TRIM command support  inside the windows command prompt](/blog/images/2010/trim_command_check_command_prompt.jpg) You will get one of the following:

**DisableDeleteNotify = 1 (Means that Windows TRIM commands are disabled)
DisableDeleteNotify = 0 (Means that Windows TRIM commands are enabled)**

### What is TRIM and why do you need it

> In computing, a **TRIM** command allows an operating system to inform a solid-state drive (or "SSD") which data blocks, such as those belonging to a deleted file or affected by a format command, are no longer considered in use and can be wiped internally.
> 
> TRIM was introduced soon after SSDs started to become an affordable alternative for traditional hard disks as permanent storage in PCs. Because low-level operation of SSDs differs significantly from traditional hard disks (see details below), the typical way in which operating systems handle operations like deletes and formats (not communicating the involved sectors/pages to the storage medium) resulted in unanticipated progressive performance degradation of write operations on SSDs. TRIM enables the SSD to handle garbage collection overhead, that would otherwise significantly slow down future write operations to the involved blocks, in advance.

[from [wikipedia.org](http://en.wikipedia.org/wiki/TRIM)]

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/trim_command_check_command_prompt.jpg