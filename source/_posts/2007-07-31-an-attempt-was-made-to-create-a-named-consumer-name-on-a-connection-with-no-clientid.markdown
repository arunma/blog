---
author: Arun Manivannan
date: '2007-07-31 23:48:30'
layout: post
comments: true
slug: an-attempt-was-made-to-create-a-named-consumer-name-on-a-connection-with-no-clientid
status: publish
title: An attempt was made to create a named consumer (name) on a connection with
  no clientID
wordpress_id: '247'
? ''
: - IllegalStateException
  - JMS
  - Uncategorized
---

While creating a DurableSubscriber please do specify the client id before
specifying a named consumer. Please have a look at the small code i wrote. Do
remember to set the ClientID before creating a session from it. The clientID
becomes null and immutable after the session is created. Also remember to give
the same client id while creating a DurableSubscriber.

[![ClientID][1]][2]

   [1]: http://www.arunma.com/wp-
content/uploads/2007/07/clientid.thumbnail.JPG

   [2]: http://www.arunma.com/wp-content/uploads/2007/07/clientid.JPG
(ClientID)

