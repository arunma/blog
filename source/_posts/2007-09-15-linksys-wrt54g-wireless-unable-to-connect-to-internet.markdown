---
author: Arun Manivannan
date: '2007-09-15 01:27:53'
layout: post
slug: linksys-wrt54g-wireless-unable-to-connect-to-internet
status: publish
title: Linksys WRT54G wireless unable to connect to internet
wordpress_id: '280'
? ''
: - internet
  - linksys
  - windows xp
  - wrt54g
---

Strange but i had to face this. I was using my wireless Intel 3945 with Vista
and Kubuntu to connect to internet.  Fed up with Vista and wanting to install
my "old Vista-unsupported" games, i installed Windows XP SP2. I was able to
connect to my other desktop using my Wireless but it doesnt connect to
internet. At last I found this **[wonderful page ][1]**and here is the
solution that gave me results. I am now working on my wireless happily.

For these commands click on **Start.**...** Run**..... type in...**CMD**
....to open a command prompt box

Reset WINSOCK entries to installation defaults...type in ... **netsh winsock
reset catalog ** .... press ...enter

Reset TCP/IP stack to installation defaults...type in...... **netsh int ip
reset reset.log** ... press ...enter

__________________

   [1]: http://forums.techguy.org/networking/556167-unable-connect-internet-
via-wireless.html

