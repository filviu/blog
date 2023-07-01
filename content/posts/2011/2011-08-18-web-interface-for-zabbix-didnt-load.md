---
title: Web interface for Zabbix didn’t load
author: silviu
type: post
date: 2011-08-18T07:30:27+00:00
url: /2011/08/18/web-interface-for-zabbix-didnt-load/
categories:
  - old
tags:
  - bcmath
  - monitoring
  - php
  - temp_on
  - zabbix

---
I was installing today Zabbix on a CentOS 5.6 machine and hit the following error when trying to load the PHP Web Interface:

```bash
PHP Fatal error: Call to undefined function bcscale() in /var/www/zabbix/include/defines.inc.php on line 797
```

The fix was one package install away:

```bash
yum -y install php-bcmath
```