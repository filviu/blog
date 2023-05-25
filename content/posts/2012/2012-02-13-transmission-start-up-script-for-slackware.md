---
title: Transmission start-up script for slackware.
author: silviu
type: post
date: 2012-02-13T08:54:42+00:00
url: /2012/02/13/transmission-start-up-script-for-slackware/
dsq_thread_id:
  - 574277761
categories:
  - old
tags:
  - headless
  - script
  - slackware
  - start-stop-daemon
  - startup
  - temp_on
  - transmission. bittorrent

---
I installed transmission on a headless server so I need it to start on boot. The included start-up script was dependent on start-stop-daemon that is mission on Slackware. The examples on the transmission forums were ok but would resulted in transmission running as root and I want it to run as a non-privileged user. So I modified an example script to read like this:

&nbsp;  
[cce_bash]  
#!/bin/bash  
#Slackware startup deamon script

\# Name of Service  
NAME=&#8221;Transmission Daemon&#8221;

\# Command to run  
CMD=&#8221;/usr/bin/transmission-daemon&#8221;

\# Option to run with deamon  
\# -a means from where to accept incoming connections, comma separated  
\# you may want to add your local network if you have multiple clients  
OPTIONS=&#8221;-a 127.0.0.1&#8243;

\# Process name of daemon, for killing it.  
PROCESSNAME=&#8221;/usr/bin/transmission-daemon&#8221;

\# The name of the user that should run Transmission.  
\# It&#8217;s RECOMENDED to run Transmission in it&#8217;s own user,  
\# by default, this is set to &#8216;transmission&#8217;.  
\# For the sake of security you shouldn&#8217;t set a password  
\# on this user  
USERNAME=&#8221;transmission&#8221;

func_stop() {  
if [ &#8220;$(ps aux | grep $PROCESSNAME | grep -v grep)&#8221; ]; then  
echo -n &#8220;Stopping $NAME &#8230; &#8221;  
killall $PROCESSNAME  
sleep 2  
fi

if [ ! &#8220;$(ps aux | grep $PROCESSNAME | grep -v grep)&#8221; ]; then  
echo &#8220;Done!&#8221;  
else  
echo &#8220;Error!&#8221;  
fi  
}

func_start() {  
echo -n &#8220;Starting $NAME &#8230; &#8221;  
su &#8211; $USERNAME -c &#8220;$CMD $OPTIONS&#8221;  
sleep 2

if [ &#8220;$(ps aux | grep $PROCESSNAME | grep -v grep)&#8221; ]; then  
echo &#8220;Done!&#8221;  
else  
echo &#8220;Error!&#8221;  
fi  
}

case $1 in  
&#8220;start&#8221;)  
func_start  
;;

&#8220;stop&#8221;)  
func_stop  
;;

&#8220;restart&#8221;)  
func_stop  
sleep 2  
func_start  
;;  
*)  
echo &#8220;Usage; start|stop|restart&#8221;  
;;  
esac  
[/cce_bash]

After you test this script (make sure it starts as the user you want it to) be sure to add stop calls in /etc/rc.d/rc.6 , rc.K and start calls in rc.M (if you have a look at how rc.ntpd is called for example you&#8217;ll know how to add this one). Take care, breaking those scripts could leave you with a non functional system.