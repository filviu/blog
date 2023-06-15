---
title: Apache2 mpm-itk maxclients settings
author: silviu
type: post
date: 2013-04-18T06:09:05+00:00
url: /2013/04/18/apache2-mpm-itk-maxclients-settings/
dsq_thread_id:
  - 1221598618
categories:
  - old
tags:
  - apache2
  - httpd
  - itk
  - maxclients
  - maxrequestsperchild
  - temp_on

---
I run the [mpm-itk apache2][1] module on my server since it's shared between a few sites. A few rogue crawlers brought it down a few days ago and while I was checking the logs I noticed a lot more apache children processes running than I had defined. One quick look in apache2.conf and I noticed my mistake. I had configured under a different prefork module since the default config shipping with debian has no section for itk. So I added it myself:

[cce_apache]

<IfModule mpm_itk_module>
StartServers          8
MinSpareServers       8
MaxSpareServers      10
MaxClients           100
MaxRequestsPerChild  1000
</IfModule>

[/cce_apache]

Of course adjust values according to your resources.

 [1]: http://mpm-itk.sesse.net/