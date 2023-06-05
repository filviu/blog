---
title: Use nagios to track and graph your twitter followers
author: silviu
type: post
date: 2014-10-20T08:23:31+00:00
url: /2014/10/20/use-nagios-to-track-and-graph-your-twitter-followers/
dsq_thread_id:
  - 3135809939
categories:
  - old
tags:
  - monitoring
  - nagios
  - temp_on
  - twitter

---
I've been using [Nagios][1] to monitor servers and devices for years now. Lately as an exercise to learn more about nagios I installed a private instance that I use to monitor everything I can think of - from my personal servers to the number of hours we watch TV.

A nice use I found is to monitor the number of followers my twitter bots and personal account have. For that I wrote a custom plugin, available in my small repository of plugins at: <https://github.com/silviuvulcan/nagios-plugins>

The plugin pulls the number from the public site - no API access required. Since the data is not changing frequently you could use a custom setting to check less often. My entry looks like this:

[cce_nagios]

define host{  
use                     linux-server  
host_name               twitter  
alias                   twitter  
address                 twitter.com  
}

define service{  
use                             local-service,graphed-service         ; Name of service template to use  
host_name                       twitter  
service_description             Twitter followers: @rtjolla  
normal\_check\_interval           60                    ; check hourly  
check\_command                   check\_twitterfollowers!rtjolla  
}

[/cce_nagios]

This creates a host named twitter, and graphs (provided you have [nagiosgrapher][2] up and running) the number of followers. Of course you have to install the plugin and create a custom command for it. Mine looks like this:

[cce_nagios]  
define command{  
command\_name check\_twitterfollowers  
command\_line $USER1$/check\_twitterfollowers.sh -u $ARG1$  
}  
[/cce_nagios]

Below is the code of the plugin if you are not interested in cloning the repo:

[github file="/silviuvulcan/nagios-plugins/blob/master/check_twitterfollowers.sh"]

<figure id="attachment_3060" aria-describedby="caption-attachment-3060" style="width: 860px" class="wp-caption aligncenter">[<img decoding="async" loading="lazy" class="wp-image-3060 size-large" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/twitter-nagios-1024x244.png" alt="Twitter followers graphed by nagios sample" width="860" height="205" />][3]<figcaption id="caption-attachment-3060" class="wp-caption-text">Twitter followers graphed by nagios sample</figcaption></figure>

 [1]: http://www.nagios.org/
 [2]: http://nagiosgraph.sourceforge.net/
 [3]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/twitter-nagios.png