---
title: DNS::ZoneParse has an undocumented $ORIGIN
author: silviu
type: post
date: 2011-11-02T13:29:17+00:00
url: /2011/11/02/dnszoneparse-has-an-undocumented-origin/
dsq_thread_id:
  - 459772925
categories:
  - old
tags:
  - bind
  - dns
  - named
  - perl
  - script
  - temp_on
  - zoneparse

---
I was working writing a few scripts that should update a DNS zone file on the fly. I decided to use the <a href="http://search.cpan.org/~mschilli/DNS-ZoneParse-0.99/lib/DNS/ZoneParse.pm" target="_blank" rel="noopener">DNS::ZoneParse</a> perl module for convenience.

The example there is straightforward for changing MX records so I thought modifying it to change an A record should be a piece of cake. Right? **Wrong!**

For the love of it I couldn't get my code to modify the record in question, it would always delete it.

All the beer in the world goes to <a href="https://rt.cpan.org/Public/Bug/Display.html?id=66609" target="_blank" rel="noopener">this guy</a> who found the reason. Basically if the ORIGIN method is not set the record won't be written to the new file.

So, changing for example the record like this will actually erase it

[cce_perl]  
$a->[i] = { host => 'blah.com',  
class => 'IN',  
ttl => '1m',  
name => '@' };  
[/cce_perl]

and like this it will work:

[cce_perl]  
$origin='host.domain.com.';  
$a->[i] = { ORIGIN => $origin,  
host => 'blah.com',  
class => 'IN',  
ttl => '1m',  
name => '@' };  
[/cce_perl]