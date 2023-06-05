---
title: How to recover a lost Joomla admin password
author: silviu
type: post
date: 2009-12-18T19:32:41+00:00
url: /2009/12/18/how-to-recover-a-lost-joomla-admin-password/
dsq_thread_id:
  - 330869756
categories:
  - old
tags:
  - admin
  - joomla
  - md5
  - password
  - temp_on

---
<img decoding="async" loading="lazy" class="alignleft size-full wp-image-612" title="joomla_big_logo" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2009/12/joomla_big_logo.png" alt="joomla_big_logo" width="128" height="128" />I administer a few Joomla sites so from time to time I discover that I lost the admin password for the one I hadn't had to update for a long time. There is no way to find out what that password was because they are stored as a one way MD5 but since I usually use random characters anyway I reset the password with a new one. For that you need access to the mysql database of that Joomla site.

You can access your database either through a tool like phpMyAdmin or from the command line. Anyways, how to access your database is beyond the scope of this article.

The password is stored in the MySQL database _jos_users_ table _password_ field. (obviously if you changed the default jos_ database prefix the name will differ) Find the record for the admin user and change his password with the MD5 value of a known password. You can use the following samples or generate your own using an online tool like <a href="http://pajhome.org.uk/crypt/md5/" target="_blank" rel="noopener">this</a>.

  * 123456 - **<span>f96b697d7cb7938d525a2f31aaf161d0</span>**
  * <span>default - </span>**c21f969b5f03d33d43e04f8f136e7682**

Either method you choose I strongly suggest changing the password to something secure immediately after logging in.