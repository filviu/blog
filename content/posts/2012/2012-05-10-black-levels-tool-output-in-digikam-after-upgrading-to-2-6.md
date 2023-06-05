---
title: Black levels tool output in digikam after upgrading to 2.6
author: silviu
type: post
date: 2012-05-10T18:30:16+00:00
url: /2012/05/10/black-levels-tool-output-in-digikam-after-upgrading-to-2-6/
dsq_thread_id:
  - 684490927
categories:
  - old
tags:
  - black
  - current64
  - digikam
  - levels
  - slackware
  - temp_on

---
I tested the 2.6-rc version of digikam and found that the levels tool offers a black window instead of proper output. [<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-2190" title="Digikam Levels" src="http://www.sgvulcan.com/wp-content/uploads/2012/05/digikam_levels-145x145.jpg" alt="" width="145" height="145" />][1]First I thought it's a 2.6 issue so I reverted to my 2.5.0 stable version. No luck. I then thought it's because some updates I ran for Slackware (I'm using current64) Not having any luck I opened a bug, thankfully the digikam developers were quick to reply: https://bugs.kde.org/show_bug.cgi?id=299755

To be short the issue will be fixed for 2.6.0 stable but until then edit ~/.kde/share/config/digikamrc and remove the **[adjustlevels Tool]** config group.

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2012/05/digikam_levels-e1336674836945.jpg