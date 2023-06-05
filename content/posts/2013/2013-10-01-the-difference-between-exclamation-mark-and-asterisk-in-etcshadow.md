---
title: The difference between exclamation mark and asterisk in /etc/shadow
author: silviu
type: post
date: 2013-10-01T10:45:29+00:00
url: /2013/10/01/the-difference-between-exclamation-mark-and-asterisk-in-etcshadow/
dsq_thread_id:
  - 1814064859
categories:
  - old
tags:
  - account
  - crypt
  - disable
  - lock
  - password
  - shadow
  - temp_on

---
So, with a terrible case of memory lapsus while wanting to disable password login for a user I couldn't remember what the difference between "!" and "*" is in the **/etc/shadow** file.

<p style="padding-left: 30px">
  Well <a href="http://manpages.sgvulcan.com/shadow.5.php"><strong>man 5 shadow</strong></a> to the rescue
</p>

<p style="padding-left: 30px">
  <em>Refer to <b>crypt</b>(3) for details on how this string is interpreted.</em>
</p>

<p style="padding-left: 30px">
  <em>If the password field contains some string that is not a valid result of <b>crypt</b>(3), for instance ! or *, the user will not be able to use a unix password to log in (but the user may log in the system by other means).</em>
</p>

<p style="padding-left: 30px">
  <em>This field may be empty, in which case no passwords are required to authenticate as the specified login name. However, some applications which read the /etc/shadow file may decide not to permit any access at all if the password field is empty.</em>
</p>

<p style="padding-left: 30px">
  <em>A password field which starts with a exclamation mark means that the password is locked. The remaining characters on the line represent the password field before the password was locked.</em>
</p>

This means that both won't allow password login the account but ! (exclamation mark) means that the account is locked and can be followed by the password the account had before it was locked. When unlocked the ! is removed and the old password could be kept.

Now we both know 🙂