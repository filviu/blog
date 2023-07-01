---
title: Use nagios to track and graph your twitter followers
author: silviu
type: post
date: 2014-10-20T08:23:31+00:00
url: /2014/10/20/use-nagios-to-track-and-graph-your-twitter-followers/
categories:
  - old
tags:
  - monitoring
  - nagios
  - temp_on
  - twitter

---
# 2023 Update

With the number of changes since Twitter is under new ownership I'm not sure this can still work.

I've been using [Nagios][1] to monitor servers and devices for years now. Lately as an exercise to learn more about nagios I installed a private instance that I use to monitor everything I can think of - from my personal servers to the number of hours we watch TV.

A nice use I found is to monitor the number of followers my twitter bots and personal account have. For that I wrote a custom plugin, available in my small repository of plugins at: <https://github.com/filviu/nagios-plugins>

The plugin pulls the number from the public site - no API access required. Since the data is not changing frequently you could use a custom setting to check less often. My entry looks like this:

```apacheconf
define host {
    use                      linux-server
    host_name                twitter
    alias                    twitter
    address                  twitter.com
}

define service {
    use                      local-service,graphed-service         ; Name of service template to use
    host_name                twitter
    service_description      Twitter followers: @rtjolla
    normal_check_interval    60                    ; check hourly
    check_command            check_twitterfollowers!rtjolla
}
```

This creates a host named twitter, and graphs (provided you have [nagiosgrapher][2] up and running) the number of followers. Of course you have to install the plugin and create a custom command for it. Mine looks like this:

```apacheconf
    define command{
    command_name check_twitterfollowers
    command_line $USER1$/check_twitterfollowers.sh -u $ARG1$
}
```

![Screenshot of the Twitter followers graphed by nagios sample nagiosgraph](/blog/images/2014/twitter-nagios.png)

 [1]: http://www.nagios.org/
 [2]: http://nagiosgraph.sourceforge.net/
 [3]: http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2014/10/twitter-nagios.png