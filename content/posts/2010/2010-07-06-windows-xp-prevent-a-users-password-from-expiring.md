---
title: Windows XP – prevent a user’s password from expiring
author: silviu
type: post
date: 2010-07-06T09:54:46+00:00
url: /2010/07/06/windows-xp-prevent-a-users-password-from-expiring/
categories:
  - old
tags:
  - advanced
  - control panel
  - expire
  - expiring
  - password
  - temp_on
  - Windows
  - xp

---
One of my clients called be mecause every now and then his was bugged by Windows XP to change his password. This seemed weird as XP doesn't do this by default. Probably it was set to expire by someone or by some _friendly_ security suite.

Fortunately the solution for this expiring password problem is easy. You just need to tell Windows that you want your password to **never expire.** This is not necessarily a good practice, nevertheless if you want to, here is how you do it.

  * Go to **START->RUN** or **WIN+R**.
  * Type **control userpasswords2** and hit **ENTER**

You'll get a window like this one showing up:

  *![xp_user_accounts2](/blog/images/2010/xp_user_accounts2.jpg) 
  * You have to click the **Advanced** tab

![xp_user_accounts2_advanced](/blog/images/2010/xp_user_accounts2_advanced.jpg) 
  * Unsurprisingly, on the Advanced tab you have to click the **Advanced** button. (Who designs this kind of interfaces?)

![xp_user_accounts_edit_user](/blog/images/2010/xp_user_accounts_edit_user.jpg)

  * In the window that opens you can see your local users and groups.
  * Click on **Users** and double click **in the right panel the user you want to set the password not to expire.**

![xp_user_accounts_edit_user_expire_password](/blog/images/2010/xp_user_accounts_edit_user_expire_password.jpg)

  * Finally in the new window that opens check **Password never expires**.
  * **Apply or OK** your way back!

Done. Still it's a good ideea to change all your passwords from time to time, just to be on the safe side.
