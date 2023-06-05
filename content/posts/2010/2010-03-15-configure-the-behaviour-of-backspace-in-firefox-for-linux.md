---
title: Configure the behaviour of backspace in Firefox for Linux
author: silviu
type: post
date: 2010-03-15T21:18:15+00:00
url: /2010/03/15/configure-the-behaviour-of-backspace-in-firefox-for-linux/
dsq_thread_id:
  - 326479301
categories:
  - old
tags:
  - back
  - backspace
  - firefox
  - temp_on

---
[<img decoding="async" loading="lazy" class="size-thumbnail wp-image-744 alignleft" title="backspace" alt="" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/03/backspace-150x150.jpg" width="150" height="150" />][1]It's a mystery for me why on windows firefox developers have conceived one use for backspace and another for firefox on linux.

If you are coming from windows and moving onto linux you might be used to press backspace to go back one page in Firefox. Well you're in for a small surprise - _**id doesn't work.**_

You need to go to _**about:config**_ 

**browser.backspace_action** as either 0 or 1.

> 0 means that the backspace button will go back a page in the session history  
> 1 means that pressing the backspace key will scroll up one page in the current document

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/03/backspace.jpg