---
title: WebSVN and Mantis integration
author: silviu
type: post
date: 2011-04-19T11:20:19+00:00
url: /2011/04/19/websvn-and-mantis-integration/
dsq_thread_id:
  - 327199838
categories:
  - old
tags:
  - mantis
  - temp_on
  - websvn

---
While installing the above I found the following obscure error:

The environment under which I run Mantis is a little broken I think and so svn can only work if called with -config-dir /home/svnuser/.subversion otherwise it tries to read /root/.subversion which of course fails

Even if the above parameter is set in configuration the svn_check function appears to ignore it and calls svn help without it. Unintuitively svn help fails if it cannot read the configuration folder so the -config-dir must be applied here too.

I found this by replacing the svn binary with a wrapper that recorded the parameters it's called with. Adding the necesarry code to svn_check to use config_dir fixed the issue.