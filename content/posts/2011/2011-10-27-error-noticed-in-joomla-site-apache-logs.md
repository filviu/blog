---
title: Error noticed in Joomla site apache logs
author: silviu
type: post
date: 2011-10-27T17:50:23+00:00
url: /2011/10/27/error-noticed-in-joomla-site-apache-logs/
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
```apacheconf
[Mon Oct 17 13:49:16 2011] [error] [client aaa.aaa.aaa.aaa] PHP Notice: Array to string conversion in aaa/libraries/joomla/html/parameter.php on line 83
```

One suggestion found [online](http://www.joomseo.com/forums/4711.html) was:

Edit parameters.php and change the line 83 as follows:

Before:
```php
if (trim( $data )) {
```

After:

```php
if ($data) {
```

But modifying core joomla files isn't such a hot idea as one user notices. So the solution is fixing the plugin causing the problem in the first place:

Edit plugins/system/JoomSEO.php at line 46

```php
$this->params = new JParameter($params);
```

replace with

```php
$this->params = new JParameter($params['params']);
```
