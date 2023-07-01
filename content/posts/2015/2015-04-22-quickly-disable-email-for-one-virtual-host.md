---
title: Quickly disable email for one virtual host
author: silviu
type: post
date: 2015-04-22T09:28:09+00:00
url: /2015/04/22/quickly-disable-email-for-one-virtual-host/
categories:
  - old
tags:
  - apache
  - bash
  - email
  - temp_on

---
If you discover that one site that you host is sending tons of emails there is an easy and quick way to disable email only for one particular virtual host. Add the following line in it's virtual host or .httacess file

 ```apacheconf
php_admin_value sendmail_path "/dev/null"
```

If you add it to the virtual host be sure to reload apache.