---
title: Put an Online – Offline Yahoo Messenger button on your website
author: silviu
type: post
date: 2010-01-16T20:46:31+00:00
url: /2010/01/16/yahoo-messenger-online-now-button-on-your-website/
categories:
  - old
tags:
  - button
  - online
  - temp_on
  - Web
  - yahoo messenger

---
![t_yahoo_messenger_1](/blog/images/2010/t_yahoo_messenger_1-150x150.jpg) If you run an online business like an e-store or something similar you might want to show a button showing if your are available to chat via Yahoo Messenger.

This is a fairly easy job to do. All you have to do is to show this code somewhere on your site:
```html
<a href="ymsgr:sendIM?YOUR_YM_ID">
<img src="http://opi.yahoo.com/online?u=YOUR_YM_ID&m=g&t=1" border="0" alt="" /> </a>
```

Remember to replace  YOUR_YM_ID with your Yahoo Messenger id and give t a value reflecting the button choice you like:


- t=0 - <img decoding="async" src="http://opi.yahoo.com/online?u=YOUR_YM_ID&m=g&t=0" border="0" alt="" />
- t=1 - <img decoding="async" src="http://opi.yahoo.com/online?u=YOUR_YM_ID&m=g&t=1" border="0" alt="" />
- t=2 - <img decoding="async" src="http://opi.yahoo.com/online?u=YOUR_YM_ID&m=g&t=2" border="0" alt="" />
- t=5 - <img decoding="async" src="http://opi.yahoo.com/online?u=YOUR_YM_ID&m=g&t=5" border="0" alt="" />