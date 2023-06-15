---
title: Migrating Gerrit to Google OAuth from Google OpenID
author: silviu
type: post
date: 2015-04-09T10:17:38+00:00
url: /2015/04/09/migrating-gerrit-to-google-oauth-from-google-openid/
dsq_thread_id:
  - 3667336895
categories:
  - tech
tags:
  - gerrit
  - google
  - oauth
  - openid

---
I expect this post to be obsolete pretty soon, but for now I expect this will help you skip many of the issues and questions I had going forward with upgrading Gerrit and switching to Google OAuth from OpenID.

This post is not exhaustive, I trust that you are familiar with Gerrit if you've come so far. I am running a gerrit installation that was stuck at v2.10 as all our users used Google OpenID. With OpenID being retired in a few weeks it was imperative to find a sollution and I really wanted to go with Google OAuth (so we don't have to recreate/merge all our users by hand). The Gerrit developers bounced around the fixes up until the last minute (IMHO) as only 2.10.2 supports the gerrit-oauth-provider plugin out of the box without the need of cherry picked changes.

is required reading and fun to read and see how a thing like this can take a year of missed commits, approvals, etc. 🙂 Why gerrit refuses to have built in user management like any other half-sane web app around is beyond me but happily beyond the goal of this post too.

Let's try to organize what you have to do in steps:

  1. Shut down gerrit and update to 2.10.2 or newer, see [here][1].
  2. Clone the [gerrit repository][2], checkout v2.10.2 (or same version as above) and build with buck. **Use gerrit buck** as they seem to differ from facebook buck, see [gerrit build instructions][3].
  3. Clone [gerrit-oauth-provider][4] inside /plugins (per [build.md][5] instructions, [those are supposed to be valid][6] and at the time of writing this building stand-alone might or might not work) and build it with buck. Add gerrit-oauth-provider.jar in your site's plugins/ folder.
  4. [Create your google project][7] by visiting the [Google Developer Console][8] and obtain api and client secrets, per documentation or wiki.
  5. Following the
  ```bash
  java -jar gerrit.war init -d site/
  ```
  to reconfigure the client-secret is added to  `site/etc/secure.config` [but for now it doesn't work][9], it has to be in `gerrit.config` under the plugin configuration.
  6. Trust the OpenID accounts by adding 
  ```ini
  trustedOpenID=^.*$
  ```
  to the `[auth]` section. See [this issue][10].
  7. You **must** keep the same URL otherwise automatic linking of OpenID<=>OAuth accounts doesn't happend and you end up with new users that have to be merged ([painfully especially if you use mysql][11] as the documentation is [limited to postgress][12]).
  8. Pray, start gerrit, pray some more. Preferably to the [Spaghetti Monster][13].

It might be that some steps are not actually needed because due to confusing or downright missing documentation I had to scour mailing lists, github issues, gerrit commit logs and try each setting one by one until I got it working. When everything worked as expected I refused to go back and check whether some particular step (like building in tree, the need for trustedOpenID, etc.) is actually needed or it was already deprecated.

I'm pretty sure there are better ways to spend those hours.

 [1]: https://code.google.com/p/gerrit/
 [2]: https://code.google.com/p/gerrit/wiki/Source?tm=4
 [3]: https://git.eclipse.org/r/Documentation/dev-buck.html
 [4]: https://github.com/davido/gerrit-oauth-provider/
 [5]: https://github.com/davido/gerrit-oauth-provider/blob/master/src/main/resources/Documentation/build.md
 [6]: https://github.com/davido/gerrit-oauth-provider/issues/17
 [7]: https://github.com/davido/gerrit-oauth-provider/blob/master/src/main/resources/Documentation/config.md
 [8]: https://console.developers.google.com/
 [9]: https://github.com/davido/gerrit-oauth-provider/issues/18
 [10]: https://github.com/davido/gerrit-oauth-provider/issues/4
 [11]: https://groups.google.com/forum/#!topic/repo-discuss/zlwrVzapLi0
 [12]: https://code.google.com/p/gerrit/wiki/SqlMergeUserAccounts
 [13]: en.wikipedia.org/wiki/Flying_Spaghetti_Monster