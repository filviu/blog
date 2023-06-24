---
title: BackupPC – can’t find Compress::Zlib
author: silviu
type: post
date: 2011-12-13T07:19:55+00:00
url: /2011/12/13/backuppc-cant-find-compresszlib/
dsq_thread_id:
  - 502765320
categories:
  - old
tags:
  - backuppc
  - compress
  - cpan
  - perl
  - temp_on
  - zlib

---
![we_hate_perl150](/blog/images/2011/we_hate_perl150.jpg) 
It all started with an update for perl by our lovely CentOS. After that backuppc complained about `Compress::Zlib`. I tried installing it from CPAN but it didn't work: 

```bash
Undefined subroutine &Compress::Zlib::gzopen called
```

One [proposed fix](http://d.hatena.ne.jp/lopnor/20071120/1195522440) was to remove everything Zlib related from the perl folder in /usr/lib. It did work, as CPAN started working but Zlib refused to install due to errors.

I finally stumbled to this [fix](http://www.backupcentral.com/phpBB2/two-way-mirrors-of-external-mailing-lists-3/backuppc-21/backuppc-cant-find-compress-zlib-after-recent-update-on-cen-106280/):

> Turns out it's a problem with List::Util. The perl-Scalar-List-Utils
> rpm conflicts with perl-5.8.8-32.el5_5.1.i386 rpm. Upgrading List::Util
> from 1.19 to 1.23 from CPAN solved the problem.

Close enough, but my version of `List::Util` was up to date. Still it was worth a shot; a force install List::Util in [perl](http://manpages.sgvulcan.com/perl.1.php) CPAN shell - `perl -MCPAN -e shell` I was back up and running!