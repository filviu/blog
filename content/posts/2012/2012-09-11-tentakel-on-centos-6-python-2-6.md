---
title: Tentakel on CentOS 6 / Python 2.6
author: silviu
type: post
date: 2012-09-11T10:25:41+00:00
url: /2012/09/11/tentakel-on-centos-6-python-2-6/
dsq_thread_id:
  - 839550229
categories:
  - old
tags:
  - centos
  - python
  - temp_on
  - tentakel
  - tpg.py error
  - update

---
You probably already know this old, unmaintained but incredibly useful software: [tentakel](http://sourceforge.net/projects/tentakel/). If not check it out, you might like it.

There are two issues we need to tackle:

**1.** Tentakel uses tpg but the bundled version is not compatible with python 2.6

Error thrown:

```bash
return self.lexer[start:stop]
TypeError: object cannot be interpreted as an index
```

The fix is to download this version of tpg from it's developer: [http://cdsoft.fr/tpg/TPG-3.1.2.tar.gz](http://cdsoft.fr/tpg/TPG-3.1.2.tar.gz) From this archive extract `tpg.py` and copy it to `py/lekatnet/plugins` in tentakel's source tree.

_**Don't try the latest TPG version as it will not work probably it's parameters changed and tentakel doesn't work.**_ Basically we take a version old enough to work with tentakel (the built in is from 2003) and new enough to work with Python 2.6

**2.** Hide the md5 deprecation warning. This is not essential but seeing the warning everytime is annoying. Edit **py/lekatnet/config.py** and add around line 49 (after """)
Error shown:
```bash
/usr/lib/python2.6/site-packages/lekatnet/plugins/rsh.py:32: DeprecationWarning: the md5 module is deprecated; use hashlib instead
import md5
```

It's just a warning but it might interfere with automated tasks:

```python
import warnings
warnings.simplefilter("ignore", DeprecationWarning)
```

After that build and install accordingly to INSTALL

**3.** The site-packages are not copied in the right place (at least for CentOS 6) so move `/usr/lib/python2.6/site-packages/lekatnet` to `/usr/lib/python2.6/site-packages/lekatnet`

Enjoy.

After that build and install accordingly to INSTALL