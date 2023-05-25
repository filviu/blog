---
title: Akismet troubles traced back to DNS issues.
author: silviu
type: post
date: 2011-06-02T05:50:34+00:00
url: /2011/06/02/akismet-troubles-traced-back-to-dns-issues/
dsq_thread_id:
  - 329724317
categories:
  - old
tags:
  - akismet
  - apache
  - dns
  - mtr
  - php
  - ping
  - temp_on

---
My API key for Akismet was suddenly unconfirmed by reason of not being able to reach akismet.com My provider had indeed troubles with their primary DNS so I switched to the google public one. (8.8.8.8). This is a server not a browsing machine so I don&#8217;t have any privacy worries.

Long storry short, I changed the DNS and expected the problem to go away. Next day I was happy to find out that it didn&#8217;t. I pinged akismet.com from the console, tried http connection to it with links everything was fine. For good measure I tried other DNS entries, tried a mtr to akismet.com but still everything was fine and the key in Akismet Configuration refused to work.

Than, after a slap on my forehead I remembered **[THIS][1].** Right, after  
[cce_bash]  
service httpd stop  
service httpd start  
[/cce_bash]  
Everything went back to normal.

 [1]: http://www.sgvulcan.com/php-code-misses-dns-updates/