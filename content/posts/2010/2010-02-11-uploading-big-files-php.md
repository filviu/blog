---
title: Uploading big files via php
author: silviu
type: post
date: 2010-02-11T09:43:45+00:00
url: /2010/02/11/uploading-big-files-php/
dsq_thread_id:
  - 327263128
categories:
  - old
tags:
  - .htaccess
  - apache
  - limit
  - php
  - temp_on
  - upload

---
[<img decoding="async" loading="lazy" class="alignleft size-full wp-image-715" title="phpupload" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/02/phpupload.jpg" alt="" width="200" height="140" />][1]I'm updating a site for a client that only has file access to his hosting account via a php file manager (extPlorer for Joomla to be precise). He needed uploaded a few flash videos (in excess of 15 Mb each) but extPlorer stated that the file limit for php was set to 8 Mb.

I already knew that .htaccess overrides were allowed since I used .htaccess to enable a seo component for the site. So adding the following lines to .htaccess (in the root folder of his site) was enough to allow large uploads using a php upload.

If it doesn't exist you'll need to create a text file named .htaccess in the root of the site containing the following code:  
[ccNe_php]  
php\_value upload\_max_filesize 30M  
php\_value post\_max_size 30M  
php\_value max\_execution_time 250  
php\_value max\_input_time 250  
[/ccNe_php]  
If you don't see an increase of the allowed upload size it means that you are not allowed to override this settings and you'll need to contact your hosting provider.

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/02/phpupload.jpg