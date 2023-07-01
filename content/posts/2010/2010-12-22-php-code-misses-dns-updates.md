---
title: PHP code misses DNS updates.
author: silviu
type: post
date: 2010-12-22T12:26:00+00:00
url: /2010/12/22/php-code-misses-dns-updates/
categories:
  - old
tags:
  - apache
  - dns
  - temp_on

---
## Apache needs a full stop & start on DNS changes.

While working on a test environment I noticed that php code was not finding new hosts. The hosts were served by an internal, private dns server which was configured as default in `resolv.conf`

```apacheconf
Warning: file_get_contents(http://www.testdomain.com/webapp/file.php) [function.file-get-contents]: failed to open stream: HTTP request failed! HTTP/1.1 500 Internal Server Error in /var/www/htdocs/test.php on line 4
```

```bash
[root@jentlaibm01 manager]# cat test.php
```

```php

```

Ping was working so any other test I tried, the only part not resolving the newly added host was the php application. I tried restarting (both graceful and restart) the apache server but to no avail. At some point I simply stopped apache, waited a few seconds and started it again. Suddenly the php code was finding the new host.

**Apparently apache needs a full stop and start in order to update previously obtained DNS entries.**
