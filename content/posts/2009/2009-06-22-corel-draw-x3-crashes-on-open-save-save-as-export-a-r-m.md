---
title: Corel DRAW X3, X4 and X5 crashes on Open, Save As, Export. A.R.M. error.
author: silviu
type: post
date: 2009-06-22T10:21:02+00:00
url: /2009/06/22/corel-draw-x3-crashes-on-open-save-save-as-export-a-r-m/
subtitle:
  - The bigger they are, the harder they fall
dsq_thread_id:
  - 48858356
dsq_needs_sync:
  - 1
categories:
  - old
tags:
  - corel
  - crash
  - draw
  - fix
  - temp_on
  - x3

---
_Corel Draw is one of the most expensive pieces of junk I ever saw._ **I take that back 🙂 Considering that still X3 was decent compared to 11 and 12 and also that X5 is pretty good considering Corel&#8217;s history and also most important because I&#8217;ve seen much more expensive piles of junk since I wrote this.**

 ****Nevertheless I, and probably you too have to use and maintain it. I had the following problem on a fresh installation of Windows XP SP3: every time I wanted to export, save as or open a drawing Corel Draw X3 would crash regularly with it&#8217;s darned Crash Wizard.I tried applying the patches found on the Corel support page but it didn&#8217;t help. After some digging I found that it&#8217;s a problem related to the **Common Dialogue** function found in **comdlg32**.

You must launch regedit (**ALT+R** or **START->RUN** and type **regedit** and press **enter**) and go to:  
[HKEY\_CURRENT\_USERSoftwareMicrosoftWindowsCurrentVersionPoliciescomdlg32]  
and change **NoFileMru** from **0x00000001** to **0x00000000** 

[ccNe_reg]  
Windows Registry Editor Version 5.00

[HKEY\_CURRENT\_USERSoftwareMicrosoftWindowsCurrentVersionPoliciesComDlg32]  
&#8220;NoFileMru&#8221;=dword:00000000

[/ccNe_reg]

**_If on your computer it&#8217;s already 0 it&#8217;s worth trying the other way around, just remember to set it back if it doesn&#8217;t help._** 

**UPDATE:** I encountered the very same problem with Corel Draw X4 (even after applying the Corel Service Pack for X4) with the ugly difference that the cause of the crash is not reported. Fortunately repeated crashes on open, save, save as and export made me remember this article and sure enough this was the cause.

**UPDATE:** Users are reporting the same problem of crashing with Corel X5 and Windows XP.

Am I the only one thinking Corel is getting crapier and crapier by the version? Well not really, updating this article now, after some time I feel that x4 is really an improvement over the x3.

**UPDATE:** Some users reported the same problem on other Windows versions. Also X5 had the same issues.

<p style="text-align: center">
  <strong>If this article saved you a session of hair pulling you could buy me a beer or a coffe 🙂</strong>
</p>

[<img decoding="async" src="https://www.paypal.com/en_US/i/btn/btn_donate_LG.gif" alt="" />][1]

&nbsp;

&nbsp;

 [1]: https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=NM3TEVVVV7D52&lc=RO&item_name=sgvulcan%2ecom&item_number=corel&currency_code=USD&bn=PP%2dDonationsBF%3abtn_donate_LG%2egif%3aNonHosted