---
author: Arun Manivannan
date: '2007-05-01 20:25:30'
layout: post
comments: true
slug: windows-vista-home-premium-unable-to-uninstall-software
status: publish
title: Windows Vista Home Premium — Unable to uninstall software
wordpress_id: '217'
? ''
: - gpedit
  - nortel contivity
  - The system administrator has set policies to prevent th
  - vista home premium
---

Yeah. This is a post on Windows Vista by a Linux user. (I am forced to use
Windows temporarily due to this Flex Builder trap by Adobe). I bought this
Dell Inspiron notebook which came bundled with Vista Home premium. I was
trying to uninstall some useless software and I got this error.

**"The system administrator has set policies to prevent this installation"**

[![Vista Home Premium uninstall][1]][2]

Called up Microsoft support and the Dell support. No use.

Here is the fix i found from **[this site][3].**

1- Click Start, and type **"cmd" **in the search area, right click on
**"Command Prompt" **and select **"Run as Administrator".**

2- In the command prompt type **"net users Administrator /active:yes" **(Note
the capital "A" in Administrator) and press Enter, you will get a confirmation
as **"The command completed successfully".**

3- Click Start, and type **"regedit" **in the search area and click Enter,
navigate to:

**[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\****Windows\CurrentVersion\Policies\S
ystem]** Double click on **"FilterAdministratorToken" **and set it to **"0"**
Log off and you will have your Administrator account activated. Login in and
uninstall.

Linux is always sweet here. First, you can just "sudo" to Administrator. And
second, you need not to log off/restart for anything.

Vista Ultimate users, you always have the **gpedit.msc. **Forgot to mention
something, I am not able to use my **Nortel Contivity client on Vista**.
However, There is a beta version for the client [**here**][4]. Try your luck.

   [1]: http://www.arunma.com/wp-content/uploads/2007/05/vista-home-premium-
uninstall.thumbnail.jpg

   [2]: http://www.arunma.com/wp-content/uploads/2007/05/vista-home-premium-
uninstall.jpg (Vista Home Premium uninstall)

   [3]: http://www.neowin.net/forum/lofiversion/index.php/t537806.html

   [4]: http://993399.com/resources/nortel_contivity_vpn_client_for_vista

