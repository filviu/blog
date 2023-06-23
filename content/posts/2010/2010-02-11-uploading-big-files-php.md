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
![phpupload](/blog/images/2010/phpupload.jpg) I'm updating a site for a client that only has file access to his hosting account via a php file manager (extPlorer for Joomla to be precise). He needed uploaded a few flash videos (in excess of 15 Mb each) but extPlorer stated that the file limit for php was set to 8 Mb.

I already knew that .htaccess overrides were allowed since I used .htaccess to enable a seo component for the site. So adding the following lines to .htaccess (in the root folder of his site) was enough to allow large uploads using a php upload.

If it doesn't exist you'll need to create a text file named .htaccess in the root of the site containing the following code:

```apacheconf
php_value upload_max_filesize 30M
php_value post_max_size 30M
php_value max_execution_time 250
php_value max_input_time 250
```

If you don't see an increase of the allowed upload size it means that you are not allowed to override this settings and you'll need to contact your hosting provider.
