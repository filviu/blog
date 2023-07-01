---
title: Using Xenu with authentication
author: silviu
type: post
date: 2013-01-06T12:10:21+00:00
url: /2013/01/06/using-xenu-with-authentication/
categories:
  - old
tags:
  - authentication
  - fiddler
  - frontend
  - seo
  - temp_on
  - xenu

---
I needed to scan a Joomla site that only shows most of its content when logged in in the frontend. Xenu FAQ suggests using Cookies. That didn't work for me. So I used [Fiddler web debugger](http://www.fiddler2.com) and it’s scripting engine.

First start Fiddler and set it to capture traffic. Log in in the site using a browser. Check and find the cookie data - copy it to the clipboard.

Open ‘Customize rules’ in Fiddler and search for

```js
static function OnBeforeRequest(oSession: Session)
```

Before any other code paste:

```js
oSession.oRequest["Cookie"] = "data you copied earlier";
```

Now start Xenu as you would on any other site. Remember to disable Fiddler after that as it might offer weird results later.