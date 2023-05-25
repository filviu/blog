---
title: Easily send mail from a bash script
author: silviu
type: post
date: 2010-03-18T14:03:51+00:00
excerpt: |
  Did you ever need to have e-mail's sent from within a bash script? Maybe alert you of errors encountered? Me too.
  
  Here's an easy way on how to do it:
url: /2010/03/18/easily-send-mail-from-a-bash-script/
dsq_thread_id:
  - 326448579
categories:
  - old
tags:
  - automation
  - bash
  - email
  - error
  - message
  - script
  - temp_on

---
Did you ever need to have e-mail&#8217;s sent from within a bash script? Maybe alert you of errors encountered? Me too.

Here&#8217;s an easy way on how to do it:  
[ccNe_bash]  
#!/bin/bash  
\# email send script example  
#  
\# subject of email  
SUBJECT=&#8221;BASH SAYS HELLO&#8221;  
\# destination  
EMAIL=&#8221;user@yourdomain.com&#8221;  
\# Email body  
EMAILMESSAGE=&#8221;/tmp/messagebody.txt&#8221;  
echo &#8220;Email sent from BASH&#8221; > $EMAILMESSAGE  
echo &#8220;Another text line&#8221; >> $EMAILMESSAGE  
\# send message using /bin/mail  
/bin/mail -s &#8220;$SUBJECT&#8221; &#8220;$EMAIL&#8221; < $EMAILMESSAGE  
[/ccNe_bash]  
Easy.