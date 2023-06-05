---
title: Graph the number of twitter followers using Nagios
author: silviu
type: post
date: 2014-09-08T13:52:45+00:00
url: /2014/09/08/graph-the-number-of-twitter-followers-using-nagios/
dsq_thread_id:
  - 2998580959
categories:
  - old
tags:
  - nagios
  - temp_on
  - twitter

---
I'm running a nagios instance on a home machine to monitor and graph all kinds of data. Among them I wanted a graph of the twitter followers of some twitter bots I built.

I needed a script to get this number and for now I didn't want to bother using the API.



The script simply uses curl to get a public http page, it doesn't use the API. Use it and call it like below:

Add to commands.cfg

[cce_conf]

define command{  
command\_name    check\_twitterfollowers  
command\_line    $USER1$/check\_twitterfollowers.sh -u $ARG1$  
}

[/cce]

Add the service check to one of your hosts (I use the one running nagios)

[cce_conf]

define service{  
use                             local-service,graphed-service         ; Name of service template to use  
host_name                       localhost  
service_description             Twitter followers: @rtjolla  
normal\_check\_interval           60                    ; check hourly  
check\_command                   check\_twitterfollowers!rtjolla  
}

[/cce]

 

 