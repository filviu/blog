---
title: Killall for windows :)
author: silviu
type: post
date: 2010-09-11T08:11:59+00:00
url: /2010/09/11/killall-for-windows/
categories:
  - old
tags:
  - kill
  - process
  - temp_on
  - Windows

---
Ever wanted to kill a process from the command line in windows? Here's how:

If you know the name of a process to kill, for example firefox.exe, use the following command from a command prompt to end it:

```shell
taskkill /IM firefox.exe
```

This will cause the program to terminate gracefully, asking for confirmation if there are unsaved changes. **To forcefully kill the same process**, add the /F option to the command line. Be careful with the /F option as it will terminate all matching processes without confirmation.

To kill a single instance of a process, specify its process id (PID). For example, if the desired process has a PID of 1227, use the following command to kill it:

```shell
taskkill /PID 1227
```

Using filters, a variety of different patterns can be used to specify the processes to kill. For example, the following filter syntax will forcefully kill all processes owned by the user **User:**

```shell
taskkill /F /FI "USERNAME eq User"
```

The following table shows the available filters and their use.

```shell
Filter Name Valid Operators Valid Value(s)
---- ----- -----
STATUS eq ne RUNNING | NOT RESPONDING
IMAGENAME eq ne Image name
PID eq ne gt lt ge le PID value
SESSION eq ne gt lt ge le Session number.
CPUTIME eq ne gt lt ge le CPU time in the format
of hh:mm:ss.
MEMUSAGE eq ne gt lt ge le Memory usage in KB
USERNAME eq ne User name in [domain]user
format
MODULES eq ne DLL name
SERVICES eq ne Service name
WINDOWTITLE eq ne Window title
```