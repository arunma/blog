---
author: Arun Manivannan
date: '2007-07-31 00:42:58'
layout: post
comments: true
slug: configure-jms-server-in-weblogic-92
status: publish
title: Configure JMS Server in Weblogic 9.2
wordpress_id: '239'
? ''
: - jms in weblogic 9.2
  - NameNotFoundException
  - Queue
  - Uncategorized
---

I did this homework today. Just wanted to share it with you. I have uploaded
the JMS Sender and the Receiver files and the JMS server in Weblogic 9.2
configuration procedure in a separate pdf file. You can find these files
**[HERE][1]**

As for others who has reached this page after getting a NameNotFoundException
-- Unable to resolve destination queue, what you have to do is to configure a
JMS server under Services --> Messaging and make your DestinationQueue
(configured under SystemModule) a subdeployment of the JMSServer. Details of
configuring is in the above mentioned PDF.

   [1]: http://www.arunma.com/files/code/jms/

