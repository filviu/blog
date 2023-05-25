---
title: 'mysqldump: Got error 28 from storage engine'
author: silviu
type: post
date: 2012-11-27T12:05:07+00:00
url: /2012/11/27/mysqldump-got-error-28-from-storage-engine/
dsq_thread_id:
  - 946249557
categories:
  - old
tags:
  - error 28
  - mysql
  - mysqldump
  - storage
  - temp_on

---
This is a new one for me. I was dumping some databases on a server when I got this:  
[cce_bash]  
mysqldump: Error: &#8216;Got error 28 from storage engine&#8217; when trying to dump tablespaces  
mysqldump: Couldn&#8217;t execute &#8216;show fields from \`xxxxxx\`&#8217;: Got error 28 from storage engine (1030)  
[/cce_bash]  
Fortunately the fix was easy, just clean the /tmp folder as it was almost full on that particular server.