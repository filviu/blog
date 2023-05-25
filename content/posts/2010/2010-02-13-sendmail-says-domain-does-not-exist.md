---
title: Sendmail says “domain does not exist”
author: silviu
type: post
date: 2010-02-13T17:05:44+00:00
url: /2010/02/13/sendmail-says-domain-does-not-exist/
dsq_thread_id:
  - 330958933
categories:
  - old
tags:
  - deliver
  - domain
  - email
  - exist
  - sendmail
  - temp_on

---
[<img decoding="async" loading="lazy" class="alignleft size-full wp-image-722" title="sendmail" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/02/sendmail.jpg" alt="" width="117" height="42" />][1]Recently I set-up a machine in my closet to act as a backup server. One of it&#8217;s jobs is to download via pop3 all the email from our Gmail accounts just in case the cloud goes puf :). For this job I used fetchmail to fetch the emails to local users on the machine. All nice and simple &#8230; you&#8217;d think.

The mail didn&#8217;t get delivered because sendmail complained about this error.  
[ccNe_bash]  
Domain of sender address user@old.domain.com does not exist  
[/ccNe_bash]  
Now this is weird &#8211; I just want to have the mails delivered locally. Well, since spam is such a big problem sendmail likes to check that the domain from which the message _**originated**_ is real.

In my case this fails of course since some of the old emails we have in this accounts are from addresses that no longer exists and so sendmail refused to deliver them. So we just have to tell email to accept email coming from nonexistent domains.

_**Note**_: that this is not safe or recommended in anyway if the sendmail is running on a live email server. (Why are you running sendmail on  live machine anyway?) It&#8217;s acceptable in this case since this sendmail will only get messages downloaded by fetchmail from a few google GMail accounts.

So the setting to change in order to allow messages from nonexistent domains is found in  
[ccNe_bash]  
/usr/share/sendmail/cf/cf/sendmail-slackware.mc  
[/ccNe_bash]  
and it&#8217;s this one:  
[ccNe_bash]  
dnl# Turn this feature on if you don&#8217;t always have DNS, or enjoy junk mail:  
dnl FEATURE(\`accept\_unresolvable\_domains&#8217;)dnl  
[/ccNe_bash]  
and after changing it should read:  
[ccNe_bash]  
FEATURE(\`accept\_unresolvable\_domains&#8217;)dnl  
[/ccNe_bash]  
After changing it you must run:  
[ccNe_bash]  
cd /usr/share/sendmail/cf/cf  
cp sendmail-slackware.mc config.mc  
m4 /usr/share/sendmail/cf/m4/cf.m4 config.mc > /etc/mail/sendmail.cf  
[/ccNe_bash]  
When I did the above again after reinstalling running simply this also worked:  
[CCNe_bash]  
m4 sendmail-slackware.mc > /etc/mail/sendmail.cf  
[/ccNe_bash]

 [1]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2010/02/sendmail.jpg