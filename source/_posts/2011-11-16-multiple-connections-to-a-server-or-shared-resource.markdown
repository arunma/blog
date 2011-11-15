---
layout: post
title: "Multiple connections to a server or shared resource"
date: 2011-11-16 02:31
comments: true
categories: tech tips
description: "Multiple connections to a server or shared resource by the same user"
keywords: "multiple, connections, server, shared, resource, same user, network, folder, different, user name, password, disconnect, existing mappings, network share"
---

I was trying to connect to my NAS drive from my Windows 7 machine and got an interesting error.  A little googling told me that a restart of the PC should solve the problem. I don't want to and I know that is why you are here too. 

So, if your problem as stated [here][1] is this

`The network folder specified is currently mapped using a different user name and password. To connect using a different user name and password, first disconnect any existing mappings to this network share.`

and this

`Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.`

then all you have to do is this

1) Open your Run window or Hit Window+R and type `cmd`. That should open your command window.

2) Type `net use` as in 

{%codeblock%}
C:\Users\Jason>net use
New connections will be remembered.


Status       Local     Remote                    Network

-------------------------------------------------------------------------------
OK                     \\192.168.1.7\IPC$        Microsoft Windows Network
The command completed successfully.
{%endcodeblock%}

3) Type `net use /delete <your serverpath\sharedfoldername>` as in 

{%codeblock%}

C:\Users\Jason>net use /delete \\192.168.1.7\IPC$
\\192.168.1.7\IPC$ was deleted successfully.

{%endcodeblock%}

Now, try reconnecting. 

*I am still experimenting with octopress and don't know how to trackback to the [original source][2]. Apologies.*


[1]: http://support.microsoft.com/kb/938120
[2]: http://www.howtogeek.com/forum/topic/how-to-disconnect-vista-from-a-shared-resource

