---
title: Authentication problems with postfix, courier, mysql and virtual domains
author: silviu
type: post
date: 2010-03-15T20:54:44+00:00
url: /2010/03/15/authentication-problems-with-postfix-courier-mysql-and-virtual-domains/
dsq_thread_id:
  - 333377518
categories:
  - old
tags:
  - authentication
  - courier
  - mysql
  - password
  - postfix
  - temp_on

---
<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-729" title="Hash" alt="" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/03/Hash-150x150.png" width="150" height="150" />I outgrew my shared hosting and decided to go for a dedicated virtual server. I chose [Linode][1] but I will leave that for another article.

I decided to use postfix + courier + mysql and virtual domains for my mail setup. Everythig was configured fine and dandy according to the documentation. But I kept getting this in the logs:  
[ccNe_bash]  
Mar 6 13:54:42 saslauthd [5734]: pam\_mysql - required option "db" is not set Mar 6 13:54:42 saslauthd [5734]: DEBUG: auth\_pam: pam_authenticate failed: Error in service module  
Mar 6 13:54:42 saslauthd \[5734]: do_auth : auth failure: [user=test@xxxxxxx.com\] \[service=smtp\] \[realm=xxxxxxx.com\] \[mech=pam\] [reason=PAM auth error]  
[/ccNe_bash]  
I went over the config files over and over again searching for mistakes, because I usually mix something up but nothing worked. After some time I realized that the error_ **"db" not set**_ is more important than I thought. It meant that it's not about wrong passwords copied from examples.

Well, the problem was that in **/etc/pam.d/smtp  the password for the mysql user cannot contain the # character.** And my password had. I have used a random password generator and by luck it contained a #. Everything after that was ignored, that's why it said **db not set**. That's a lost hour for nothing. Everywhere elese in the many config files containing this password it's ok to have a # but not here.

 [1]: http://www.linode.com/?r=16a04aa4c234b0d0edf8bf518ca11356448e1975