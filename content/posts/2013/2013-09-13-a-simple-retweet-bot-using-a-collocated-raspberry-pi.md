---
title: A simple retweet bot using a collocated Raspberry PI
author: silviu
type: post
date: 2013-09-13T08:57:10+00:00
url: /2013/09/13/a-simple-retweet-bot-using-a-collocated-raspberry-pi/
categories:
  - old
tags:
  - bot
  - jolla
  - raspberry pi
  - retweet
  - temp_on
  - twitter

---
# 2023 Update

With the number of changes since Twitter is under new ownership I'm not sure this can still work.



I have a Raspberry PI freely collocated by the nice people at [pcextreme][1]. Being a Jolla fan I found a new use for it. I made a Retweet bot that retweets everything #Jolla.

1. It's pretty simple. First you need to define your new twitter app [here][2].
2. Install on your raspberry the [tweepy][3] twitter python library. **Warning** usually it would be as easy as pip install tweepy but the current version has a bug which means you have to install a patched version of tweepy [found here][4]:
```bash
git clone https://github.com/knowsis/tweepy.git
cd tweepy
python setup.py install
```
3. Download and configure [retweet-bot][5] to your liking.

Once done I added a cronjob that runs retweet.py every 10 minutes and outputs to a log file. You can see (and follow) the endresult here: <http://twitter.com/rtjolla>

 [1]: http://raspberrycolocation.com/
 [2]: https://dev.twitter.com/apps
 [3]: https://github.com/tweepy/
 [4]: https://github.com/knowsis/tweepy
 [5]: https://github.com/basti2342/retweet-bot