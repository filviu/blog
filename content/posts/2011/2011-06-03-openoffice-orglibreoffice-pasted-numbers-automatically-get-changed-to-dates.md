---
title: OpenOffice.org / Libreoffice pasted numbers automatically get changed to dates
author: silviu
type: post
date: 2011-06-03T12:12:01+00:00
url: /2011/06/03/openoffice-orglibreoffice-pasted-numbers-automatically-get-changed-to-dates/
dsq_thread_id:
  - 326854326
categories:
  - old
tags:
  - automatic
  - calc
  - date
  - libreoffice
  - openoffice
  - temp_on

---
<img decoding="async" loading="lazy" class="alignleft size-thumbnail wp-image-1454" title="Open Office Calc" src="http://blog.silviuvulcan.ro/wp-content/uploads/sites/2/2011/06/openoffice_calc_3D-150x150.png" alt="" width="150" height="150" />I&#8217;ve been pasting some information from some weblogs into Calc (the <a href="http://www.openoffice.org/" target="_blank" rel="noopener">OpenOffice</a> / <a href="http://www.libreoffice.org/" target="_blank" rel="noopener">LibreOffice</a> Excel equivalent) and some version numbers like 1.5.30 got changed to dates. All the documentation pointed me towards changing the cell format to **text**. That only works if you **type** the numbers, not if you paste them. When you paste them the cell format get changed to **number** again. Read more for the solution&#8230;

<!--more-->

One sollution would be to paste as unformatted text. Unfortunately this didn&#8217;t work for me as I couldn&#8217;t get the data to align (columns kept overflowing).

The solution I found was to set the **Default** style. Press **F11**, right click on **Modify** and change the format on the **Numbers** tab to text.

No matter how many explanations I read about how this behaviour is a Good Thing (TM) I still consider this type of behaviour brain dead and there should be a switch to disable automatic date formatting.

<div id="_mcePaste" class="mcePaste" style="width: 1px; height: 1px; overflow: hidden;">
  Are all entries in the document text entries? If so, try changing the default format to text. Press F11, right click &#8220;Default&#8221; in the list in the dialog, choose &#8220;Modify&#8221; and change the format on the Numbers tab. You could save such a document as a template.
</div>