---
title: mono 3.10 on slackware 64 bit
author: silviu
type: post
date: 2015-03-24T07:28:03+00:00
url: /2015/03/24/mono-3-10-on-slackware-64-bit/
dsq_thread_id:
  - 3621732512
categories:
  - old
tags:
  - mono
  - slackware
  - temp_on

---
I installed mono using sbopkg and found the following issue while trying to run keepass:

```bash
System.TypeInitializationException: An exception was thrown by the type initializer for Mono.Unix.Native.Syscall &#8212;> System.DllNotFoundException: /usr/lib/libMonoPosixHelper.so
at (wrapper managed-to-native) Mono.Unix.Native.Syscall:get_at_fdcwd ()
at Mono.Unix.Native.Syscall..cctor () [0x00000] in <filename unknown>:0
&#8212; End of inner exception stack trace &#8212;
```

The fix was to edit [cci]/etc/mono/config[/cci] and remove the [cci]/usr/lib/[/cci] path from the [cci]libMonoPosixHelper.so[/cci] definition so that it looks like this:

```xml
<dllmap dll="MonoPosixHelper" target="libMonoPosixHelper.so" os="!windows" />
```