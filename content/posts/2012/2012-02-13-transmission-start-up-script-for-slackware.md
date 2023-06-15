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

 
```bash
#!/bin/bash
#Slackware startup deamon script

\# Name of Service
NAME="Transmission Daemon"

\# Command to run
CMD="/usr/bin/transmission-daemon"

\# Option to run with deamon
\# -a means from where to accept incoming connections, comma separated
\# you may want to add your local network if you have multiple clients
OPTIONS="-a 127.0.0.1&#8243;

\# Process name of daemon, for killing it.
PROCESSNAME="/usr/bin/transmission-daemon"

\# The name of the user that should run Transmission.
\# It's RECOMENDED to run Transmission in it's own user,
\# by default, this is set to 'transmission'.
\# For the sake of security you shouldn't set a password
\# on this user
USERNAME="transmission"

func_stop() {
if [ "$(ps aux | grep $PROCESSNAME | grep -v grep)" ]; then
echo -n "Stopping $NAME ... "
killall $PROCESSNAME
sleep 2
fi

if [ ! "$(ps aux | grep $PROCESSNAME | grep -v grep)" ]; then
echo "Done!"
else
echo "Error!"
fi
}

func_start() {
echo -n "Starting $NAME ... "
su - $USERNAME -c "$CMD $OPTIONS"
sleep 2

if [ "$(ps aux | grep $PROCESSNAME | grep -v grep)" ]; then
echo "Done!"
else
echo "Error!"
fi
}

case $1 in
"start")
func_start
;;

"stop")
func_stop
;;

"restart")
func_stop
sleep 2
func_start
;;
*)
echo "Usage; start|stop|restart"
;;
esac
```

After you test this script (make sure it starts as the user you want it to) be sure to add stop calls in /etc/rc.d/rc.6 , rc.K and start calls in rc.M (if you have a look at how rc.ntpd is called for example you'll know how to add this one). Take care, breaking those scripts could leave you with a non functional system.