---
title: libgdiplus-2.10.9 build fails on slacware current64 (2012-06)
author: silviu
type: post
date: 2012-06-13T06:01:08+00:00
url: /2012/06/13/libgdiplus-2-10-9-build-fails-on-slacware-current64-2012-06/
dsq_thread_id:
  - 723808677
categories:
  - old
tags:
  - configure
  - libgdiplus
  - make
  - mono
  - slaclware
  - temp_on

---
Installing <a href="http://www.mono-project.com/Main_Page" target="_blank" rel="noopener">mono</a> I needed to install libgdiplus. It failed with the following error:  
[cce_bash]  
/usr/lib64/gcc/x86\_64-slackware-linux/4.7.0/../../../../x86\_64-slackware-linux/bin/ld: testgdi.o: undefined reference to symbol &#8216;g_free&#8217;  
/usr/lib64/gcc/x86\_64-slackware-linux/4.7.0/../../../../x86\_64-slackware-linux/bin/ld: note: &#8216;g_free&#8217; is defined in DSO /usr/lib64/libglib-2.0.so.0 so try adding it to the linker command line  
/usr/lib64/libglib-2.0.so.0: could not read symbols: Invalid operation  
collect2: error: ld returned 1 exit status  
make[2]: \*** [testgdi] Error 1  
make[2]: Leaving directory \`/usr/local/src/libgdiplus-2.10.9/tests&#8217;  
make[1]: \*** [all-recursive] Error 1  
make[1]: Leaving directory \`/usr/local/src/libgdiplus-2.10.9&#8242;  
make: \*** [all] Error 2  
[/cce_bash]  
The fix is simple, thanks to a mention in <a href="https://www.slacky.eu/asche64/pkgreports/" target="_blank" rel="noopener">slacky</a> pkg reports:

After running **./configur**e edit **tests/Makefile** and at line 130 replace **LIBS = -lpthread -lfontconfig** with **LIBS = -lpthread -lfontconfig -lglib-2.0 -lX11**

Until a patch is made this means we&#8217;ll have to install it manually.

http://www.mono-project.com/Main_Page