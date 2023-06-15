---
title: Apache IP based restrictions based on a text list. No restart required.
author: silviu
type: post
date: 2013-10-01T10:31:32+00:00
url: /2013/10/01/apache-ip-based-restrictions-based-on-a-text-list-no-restart-required/
dsq_thread_id:
  - 1814032657
categories:
  - old
tags:
  - access
  - apache2
  - graceful
  - ip
  - temp_on
  - whitelist

---
I run a few services on a remote host that I want to restrict access to. For that I use both a password and IP based restrictions. The issue is that for example at home I have a dynamic allocated IP. One option would be to add a hostname in the apache rule, like this:

[cc_apache]

Allow from example.dyndns.org

[/cc_apache]

But this has some disadvantages:

  * it requires a dns lookup on each access
  * it uglifies your access logs

To get around this I moved away from _Access control_ to a rewrite map. Using the [apache documentation][1] I did the following:

[cc_apache]

\## WHITELIST IPS ##
RewriteEngine On
RewriteMap ipslist txt:/usr/local/etc/apache-whitelist.txt
RewriteCond %{REMOTE_ADDR} ^(.*)$
RewriteCond ${ipslist:%1|black} ^black$ [NC]
RewriteRule (.*) - [F]

[/cc_apache]

What this does is check the client's IP against /usr/local/etc/apache-whitelist.txt **Don't** **rush** like I did and cause your self a lot of headaches :), that file has to look like this (note the "-" after the IP):

[cc_bash]

##
\## ATTENTION! This is a map, not a list, even when we treat it as such.
\## mod_rewrite parses it for key/value pairs, so at least a
\## dummy value "-" must be present for each entry.
##

127.0.0.1 -
198.51.100.1 -
\# below is myhost (the update script checks for this line)
198.51.100.24 -
[/cc_bash]

Changes to this file don't require reloading apache. After this writting a script that updates some dynamic IP in the text file is easy.

When your IP changes you will have a window during witch you won't be able to access the site. (while dyndns updates your record, the change propagates and your update script is triggered). This is ok for me as I have other ways to get in (SSH, vpn, etc). There are ways in which **an attacker could exploit a system like this** (say your home router is down, the IP gets released but dyndns is not updated; a knowledgeable attacker could set the IP as theirs - depending on ISP this is really easy - and from there they are in) so I would suggest to use the above only as an aditional layer of security.

Oh, if you need an example here is the script I use:

```bash
#!/bin/bash
#
\# be sure to have a comment line with your match term
\# in the whitelist file
LIST='/usr/local/etc/apache-whitelist.txt'
MYHOST=$(resolveip -silent example.dyndns.org)

sed '/myhost/{n;d}' $LIST > $LIST.tmp
sed "s/.\*myhost.\*/&n$MYHOST -/" $LIST.tmp > $LIST

/bin/rm $LIST.tmp
```

 [1]: http://httpd.apache.org/docs/current/rewrite/access.html#host-deny