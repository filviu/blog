---
title: Using Xenu with authentication
author: silviu
type: post
date: 2013-01-06T12:10:21+00:00
url: /2013/01/06/using-xenu-with-authentication/
dsq_thread_id:
  - 1010957047
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
I needed to scan a Joomla site that only shows most of its content when logged in in the frontend. Xenu FAQ suggests using Cookies. That didn&#8217;t work for me. So I used <a href="http://www.fiddler2.com" target="_blank" rel="noopener">Fiddler web debugger</a> and it’s scripting engine.

First start Fiddler and set it to capture traffic. Log in in the site using a browser. Check and find the cookie data &#8211; copy it to the clipboard.

Open ‘Customize rules’ in Fiddler and search for

`static function OnBeforeRequest(oSession: Session)`

Before any other code paste:

`oSession.oRequest["Cookie"] = "data you copied earlier";`

Now start Xenu as you would on any other site. Remember to disable Fiddler after that as it might offer weird results later.