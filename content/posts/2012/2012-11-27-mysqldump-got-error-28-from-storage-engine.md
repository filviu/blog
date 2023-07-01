---
title: 'mysqldump: Got error 28 from storage engine'
author: silviu
type: post
date: 2012-11-27T12:05:07+00:00
url: /2012/11/27/mysqldump-got-error-28-from-storage-engine/
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

```bash
mysqldump: Error: 'Got error 28 from storage engine' when trying to dump tablespaces
mysqldump: Couldn't execute 'show fields from `xxxxxx`': Got error 28 from storage engine (1030)
```

Fortunately the fix was easy, just clean the /tmp folder as it was almost full on that particular server.