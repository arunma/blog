---
author: Arun Manivannan
date: '2007-03-16 22:36:42'
layout: post
comments: true
slug: all-peers-crashes-firefox
status: publish
title: AllPeers crashes Firefox
wordpress_id: '170'
? ''
: - Firefox
  - Uncategorized
---

After installing AllPeers and using it for a few days, I had my firefox
crashed giving me a core dump.

When i tried to open my firefox from my terminal, i got this.

`arun@arun-desktop:~$ firefox
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''' AllPeers
initiated successfully
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''' Segmentation
fault (core dumped)`

Now, will tell you how i solved this issue..

Type `arun@arun-desktop:~$ firefox -safe-mode`

You will have a dialog giving a few options.

Do not load your plugins. And once your firefox is up, uninstall or disable
All Peers. All Peers knows that there is a bug in there and they are already
working on it.

For windows users, get inside the Mozilla Firefox folder and there you can see
firefox.exe. Then stay in the Firefox folder and issue the above commands. I
dont use Windows. So, if this fix did work, please do leave a comment.

