---
title: New menu items don’t appear in Joomla 1.5.14
author: silviu
type: post
date: 2009-11-03T10:27:47+00:00
url: /2009/11/03/new-menu-items-dont-appear-in-joomla-1-5-14/
dsq_thread_id:
  - 48858518
categories:
  - old
tags:
  - joomla
  - menu
  - php
  - temp_on
  - wamp

---
I was configuring a Joomla installation for a client today and stumbled upon this little problem. No matter how I tried, new menu items refused to appear. Not only in the front-end, but they were missing in the back-end too. I checked to see, but the PHP settings were all correct. Then I noticed that the WAMP installation used PHP 5.3.0. A quick look on the [Joomla Forums][1] confirmed that Joomla has problems with this version of PHP. I went to [WAMP Add-ons](http://www.wampserver.com/en/addons_php.php) and installed PHP 5.2.11 and everything returned to normal.

Hope it helps you too.

 [1]: http://forum.joomla.org/viewtopic.php?f=469&t=426111