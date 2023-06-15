---
title: Windows XP – prevent a user’s password from expiring
author: silviu
type: post
date: 2010-07-06T09:54:46+00:00
url: /2010/07/06/windows-xp-prevent-a-users-password-from-expiring/
dsq_thread_id:
  - 326530981
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

  *<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-1028" title="xp_user_accounts2" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/xp_user_accounts2.jpg" alt="Advanced users control panel" width="404" height="448" />
  * You have to click the **Advanced** tab

<img decoding="async" loading="lazy" class="aligncenter size-full wp-image-1029" title="xp_user_accounts2_advanced" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/xp_user_accounts2_advanced.jpg" alt="Advanced tab of users settings" width="404" height="447" />
  * Unsurprisingly, on the Advanced tab you have to click the **Advanced** button. (Who designs this kind of interfaces?)

[<img decoding="async" loading="lazy" class="aligncenter wp-image-1030 size-medium" title="xp_user_accounts_edit_user" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/xp_user_accounts_edit_user-300x223.jpg" alt="Windows XP Advanced Users Settings" width="300" height="223" />][1]

  * In the window that opens you can see your local users and groups.
  * Click on **Users** and double click **in the right panel the user you want to set the password not to expire.**

[<img decoding="async" loading="lazy" class="aligncenter size-medium wp-image-1031" title="xp_user_accounts_edit_user_expire_password" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/xp_user_accounts_edit_user_expire_password-300x223.jpg" alt="Advanced user settings. Set password expiring time" width="300" height="223" />][2]

  * Finally in the new window that opens check **Password never expires**.
  * **Apply or OK** your way back!

Done. Still it's a good ideea to change all your passwords from time to time, just to be on the safe side.

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/xp_user_accounts_edit_user.jpg
 [2]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/07/xp_user_accounts_edit_user_expire_password.jpg