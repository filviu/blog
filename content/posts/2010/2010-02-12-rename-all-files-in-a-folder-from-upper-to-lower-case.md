---
title: Rename all files in a folder from upper to lower case.
author: silviu
type: post
date: 2010-02-12T10:49:35+00:00
url: /2010/02/12/rename-all-files-in-a-folder-from-upper-to-lower-case/
categories:
  - old
tags:
  - bash
  - folder
  - rename
  - script
  - temp_on

---
Sometimes is needed to have all files in a folder in the same case. Here's a small script to rename all files in the folder to lower case:

```bash
for i in *; do mv $i `echo $i | tr [:upper:] [:lower:]`; done
```