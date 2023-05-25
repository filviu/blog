---
title: Error noticed in Joomla site apache logs
author: silviu
type: post
date: 2011-10-27T17:50:23+00:00
url: /2011/10/27/error-noticed-in-joomla-site-apache-logs/
dsq_thread_id:
  - 454696831
categories:
  - old
tags:
  - apache
  - error
  - joomla
  - php
  - temp_on

---
Browsing trough my web logs I found the following error in the apache error log of a Joomla site:  
[ccNe_apache]  
\[Mon Oct 17 13:49:16 2011\] \[error\] [client aaa.aaa.aaa.aaa] PHP Notice: Array to string conversion in aaa/libraries/joomla/html/parameter.php on line 83  
[/ccNe_apache]  
One suggestion found <a href="http://www.joomseo.com/forums/4711.html" target="_blank" rel="noopener">online</a> was:

Edit parameters.php and change the line 83 as follows:

Before:  
[cceN_php]  
if (trim( $data )) {  
[/cceN_php]  
After:  
[cceN_php]  
if ($data) {  
[/cceN_php]  
But modifying core joomla files isn&#8217;t such a hot idea as one user notices. So the solution is fixing the plugin causing the problem in the first place:

Edit plugins/system/JoomSEO.php at line 46  
[cceN_php]  
$this->params = new JParameter($params);  
[/cceN_php]  
replace with  
[cceN_php]  
$this->params = new JParameter($params[&#8216;params&#8217;]);  
[/cceN_php]