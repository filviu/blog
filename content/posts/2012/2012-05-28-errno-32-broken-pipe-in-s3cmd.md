---
title: '[Errno 32] Broken pipe in s3cmd'
author: silviu
type: post
date: 2012-05-28T17:21:30+00:00
url: /2012/05/28/errno-32-broken-pipe-in-s3cmd/
dsq_thread_id:
  - 708807693
categories:
  - old
tags:
  - amazon
  - backup
  - broken
  - bucket
  - pipe
  - s3
  - s3cmd
  - temp_on

---
In order to backup a bunch of servers I'm using <a href="http://s3tools.org/s3cmd" target="_blank" rel="noopener">s3cmd</a> to backup files to a Amazon S3 account. s3cmd is a really nice tool as it works from the command line, does encryption on the fly and can use the https protocol for upload.

I used  

```bash
s3cmd -configure
``` 

and set everything up. The first error I got when I tried to test it was:

`s3cmd put file.tar.gz s3://my_bucket_name/file.tar.gz`

```bash
[Errno 32] Broken pipe
```
and it tried throttling down and uploading again. What I didn't know was that:

* if your file is over 5Gb it will give this error
* if you just created the bucket it may take a few minutes to start working
* you get this error if the bucket doesn't exist (you mistyped it)
