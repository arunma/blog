---
author: Arun Manivannan
date: '2010-03-11 11:44:08'
layout: post
comments: true
slug: how-i-met-my-first-nas-qnap-or-synology
status: publish
title: How I met my first NAS - Qnap or Synology
wordpress_id: '418'
? ''
: - 1.5 TB
  - java
  - java
  - nas
  - personal
  - qnap
  - samsung
  - seagate
  - synology
  - western digital
  - ws
---

I have a bad habit.  I buy impulsively.  But the good part about it is that
when the pressure to buy becomes overwhelming, I wait.  I go back home and
read every single word on the planet about what I wanted to buy in the first
place.  Eventually, I end up buying something else.

A couple of weeks back, I read a blog about Thecus NAS drives and immediately
wanted to buy one.  I wanted to own it on that very day.  Then the pressure
built so much that I had to sit and let it mellow.  I googled.

The noise level of most Thecus drives was a huge turn off considering the high
probability of getting murdered by my wife (I fondly remember the days when my
desktop was louder than an average car on the road).  Netgear NVX and NV+
series were good but they are a bit pricey for the features they offer.

Forgot to mention that my drives will be **primarily used for storage and as a
torrent slave**.  I will also be running a few services like **Photo manager,
Tomcat, iTunes **(more services depends on the success in setting up DDNS) .
If it helps, I dont use windows at home (mac and linux) and I am planning for
a RAID 5 setup.

So, I decided to get either the Synology of the Qnap drives.  **Synology 1010
and Qnap 459 **were my choices after long hours of search. These were the
points that I considered.

1)   Buy an **Intel Atom based drive **because of the support for a variety of
software packages.

2)

**QNAP models TS-459, 659, 859**

+ high overall performance + supports scheduled **power on and off **- no RAID
10 support - no hybrid RAID functionality - storage cannot be expanded with a
companion unit (# drivebays is max, you could buy a 2nd unit of course or use
one of the many ports) - No biggie (I backup using my USB drives) + has 5 USB
2.0 ports + has 2 eSATA ports + volume based encryption + built-in DHCP server
+ **handy LCD display ** + USB Copy function on the frontpanel + supports the
EXT4 filesystem (> 16 TB volumes) + supports WebDAV + advanced iSCSI support +
all the drives are lockable with a key + in general, no problem with
downgrading of firmware - one year guarantee + great build quality + already
much experience, add-on software and models available on x86 platform

**Synology DS 1010+**

- only supports scheduled power off + RAID 10 support + hybrid RAID
functionality (SHR) + storage can be expanded (with the extra 5 drivebays
case, however will eSATA connection become bottleneck?) - has 4 USB 2.0 ports
- has 1 eSATA port + folder based encryption - no built-in DHCP server - no
LCD display - no USB Copy function on the front - no EXT4 filesystem support
(volumes > 16 TB volume will not be possible) - no WebDAV support - less
advanced iSCSI support - the drives are not lockable with a key - in general,
very problematic to downgrade firmware - less models, less choice + three
years guarantee - build quality is not as good as QNAP - first model based on
x86 platform

Source : [http://forums.smallnetbuilder.com/showthread.php?t=2855][1]

3)  At the end of the read, I wanted to go for one of those Qnap drives - 459,
509 or 659. 659 was way above my budget but I wanted to keep it in the
background because it had support for 6 drives and I can always buy 4 drives
in the beginning and fill up the other drives on need basis.

Later, I read that **RAID is not a backup** (did i say that I am totally new
to RAID and the whole world of NAS drives) and does not guarantee dataloss and
that I will need to have another plan for backup. I then decided to use my USB
drives for the important backups (mostly my son's photos and videos).  So, it
doesnt make any sense to buy a 659 for an extra 600 SGD. May be later, I can
always go for another NAS for an extra 200 SGD and have it as a backup.

So, 509 and 459. 459 had an Atom Dual core processor and 509 had a Celeron
processor. The best part about 509, though, is that you can upgrade the
processor to something big (say, Core2Duo) but I always have the fear to open
up my system after i burnt a couple of RAMs on my first desktop (a 16 MB was a
100 USD then. that burnt a lot of my fingers) and I found very few people
upgrading their processor on a 509.  So, 459 it is.

**Hard drives : **

Then comes the problem about hard-drives. I wanted to buy the **Seagate 1.5 TB
7200.11** or any other 2 TB drives so that i can make a good 6 TB out of my 4
slot 459 (2 TB gone for parity).  Later, I found that the 1.5 TBs are
notoriously fault prone. The **WD Caviar Greens play horribly with Qnaps
**(Google "site:forum.qnap.com Caviar Green") and so are most of the other WD
drives. The Caviar blacks 1 TB are excellent drives despite their noise level
but some say that the noise and the clicks are that not that troublesome.
schumaku from the forum is known for his expertise in harddrives. He was
suggesting not to buy the highest capacity of any drive - they are known to
create the highest number of problems.

Most were complaining that Seagates gave a lot of problem and they had various
problems with different drives and that they were unlucky.  (my luck factor is
near to zero). I never wanted to take any risk.

The Hitachi Ultrastar A7K2000 is the best for Qnap drives. Everybody agrees to
it but at 513 SGD for a 2 TB, I'll give it a pass. Finally, I decided to go
for Samsung drives F1 or F3.  They say that F3s should work very well but I
dont see them on the Qnap compatibility list
([http://www.qnap.com/pro_compatibility.asp][2]).  So, here is my final
configuration.

**NAS : **

Qnap 459 Pro (Intel Atom D510 1.66 GHz (Dual-Core) - RAM - 1GB DDRII (I might
end up upgrading the RAM alone))

**HDD: **

4 * 1 TB (RAID 5) - Samsung Spinpoint F1 HE103UJ (buying RAID Class depends on
availability)

   [1]: http://forums.smallnetbuilder.com/showthread.php?t=2855

   [2]: http://www.qnap.com/pro_compatibility.asp

