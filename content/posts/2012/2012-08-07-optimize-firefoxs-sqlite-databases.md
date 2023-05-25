---
title: Optimize Firefox’s sqlite databases
author: silviu
type: post
date: 2012-08-07T11:51:25+00:00
url: /2012/08/07/optimize-firefoxs-sqlite-databases/
dsq_thread_id:
  - 796875152
categories:
  - old
tags:
  - database
  - firefox
  - mozilla
  - oneliner
  - optimize
  - sqlite
  - temp_on

---
Here&#8217;s a handy one-liner to tune a bit your Firefox:  
[cc_bash]  
for file in ~/.mozilla/firefox/\*/\*.sqlite; do sqlite3 $file &#8216;VACUUM;&#8217;;done  
[/cc_bash]

What this does ie optimize every sqlite database in your account&#8217;s profiles. You can even add this line to a script to start on boot or by cron. Worth noting that Firefox should probably not run while you do this.