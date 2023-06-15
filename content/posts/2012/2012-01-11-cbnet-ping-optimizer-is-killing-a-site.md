---
title: cbnet Ping Optimizer is killing a site
author: silviu
type: post
date: 2012-01-11T10:28:20+00:00
url: /2012/01/11/cbnet-ping-optimizer-is-killing-a-site/
dsq_thread_id:
  - 534870823
categories:
  - old
tags:
  - cbnet Ping Optimizer
  - mysql
  - slow
  - temp_on
  - wordpress

---
Some wise soul decided many moons ago that installing the aforementioned plugin on a site I host is a great ideea. The wise soul is long gone (admining websites for ngo's as a volunteer is no fun for far too many come and goers:) ) Lately the site was getting more and more sluggish with no apparent reason. I decided to clean a bit the many modules he thought in his wisdom to install. Like any major work on a site I started with a backup. I was puzzled to see that [mysqldump][1] would hang. I checked, it was not hanging, it was dumping a really huge .sql file. That was not normal as the site only has a few hundreds of articles. A check in phpmyadmin later and I found the culprit:

**WPPREFIX_cbnetpo_ping_optimizer** table had over **11Gb. Great, 82 million records** for some errors about not being able to ping. Great: no limit on how much you log in the table, no throttling on errors (each error is logged tens of times in the same second) and so on. I could track where this comes from but I simply removed the darn plugin and dropped the table.

So great idea on installing untested plugins and great coding by the plugin author.

 [1]: http://manpages.sgvulcan.com/mysqldump.1.php