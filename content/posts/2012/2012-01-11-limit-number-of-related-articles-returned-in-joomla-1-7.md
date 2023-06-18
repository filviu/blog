---
title: Limit number of related articles returned in Joomla 1.7 and Joomla 2.5
author: silviu
type: post
date: 2012-01-11T15:39:15+00:00
url: /2012/01/11/limit-number-of-related-articles-returned-in-joomla-1-7/
dsq_thread_id:
  - 535149273
categories:
  - old
tags:
  - articles
  - joomla
  - limit
  - mod_related_items
  - related
  - temp_on

---
Joomla 1.7 has a nice module mod_related_items (Articles Related) that shows articles related to the current one the visitor is browsing. It has one issue though, you can't set a limit.

So a little code hacking is in order. Open `modules/mod_related_items/helper.php` and go to line 94 (right after the `_Filter by language_ if_`) and modify 

```php
$db>setQuery($query); 
```

to read:

```php
$db->setQuery($query,0,10);
```

Of course you can change the limit from 10 with whatever you like. Random order is commented out because using ORDER BY RAND has performance issues. If you think you can handle it feel free to uncomment.

**This hack also works for Joomla 2.5!**

**Homework:**

  * add parameter in the admin interface Feel free to post the solution 🙂