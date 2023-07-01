---
title: Easily send mail from a bash script
author: silviu
type: post
date: 2010-03-18T14:03:51+00:00
excerpt: |
  Did you ever need to have e-mail's sent from within a bash script? Maybe alert you of errors encountered? Me too.

  Here's an easy way on how to do it:
url: /2010/03/18/easily-send-mail-from-a-bash-script/
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
Did you ever need to have e-mail's sent from within a bash script? Maybe alert you of errors encountered? Me too.

Here's an easy way on how to do it:

```bash
#!/bin/bash
# email send script example
#
# subject of email
SUBJECT="BASH SAYS HELLO"
# destination
EMAIL="user@yourdomain.com"
# Email body
EMAILMESSAGE="/tmp/messagebody.txt"
echo "Email sent from BASH" > $EMAILMESSAGE
echo "Another text line" >> $EMAILMESSAGE
# send message using /bin/mail
/bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE
```

Easy.