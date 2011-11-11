---
author: Arun Manivannan
date: '2007-02-19 00:52:54'
layout: post
slug: lshw-hardware-details-on-ubuntulinux
status: publish
title: lshw - Hardware details on Ubuntu/Linux
wordpress_id: '101'
? ''
: - linux
  - lshw
  - Uncategorized
---

This is a wonderful tool for Linux users. Know all your hardware details with
this superb tool called  “lshw”

Try it now: `$sudo lshw`

You can get specific details by using the -C flag: `$sudo lshw -C disk` will
list all you hard disks.

To create an html page with your hardware details, then type: `$sudo lshw
-html > your-file-name.html`

[This][1] is what I got when i used the last command on my machine.

   [1]: http://www.arunma.com/files/your-file-name.html

