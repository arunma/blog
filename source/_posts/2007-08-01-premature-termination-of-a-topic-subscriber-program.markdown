---
author: Arun Manivannan
date: '2007-08-01 00:28:25'
layout: post
comments: true
slug: premature-termination-of-a-topic-subscriber-program
status: publish
title: Premature termination of a Topic Subscriber program
wordpress_id: '249'
? ''
: - not receiving messages
  - premature termination
  - subscriber
  - Uncategorized
---

Simple threading trick. However, it looked interesting to me. When you look at
my [Subscriber.java,][1] you would see that i wrote something like this Object
ob=new Object(); synchronized(ob) { ob.wait(); }

in my subscribe() method. The reason for writing this is to keep my Subscriber
alive and keep on waiting for the Publisher to push messages. Simply put, I
dont want to end my program. The above code just creates "some" object and
makes the current thread acquire its lock and WAIT !!! Current Thread is
nothing but the main thread which is the only thread that is running in the
Subscriber program. But how does the onMessage called?

Truth is the onMessage( ) is invoked by another thread that is owned by the
JMS provider. Debugging the program, I understood that the main program is in
wait state. However, there are a number of other threads that are running, one
of which calls back the onMessage method.

[![Threads][2]][3]

   [1]: http://www.arunma.com/files/code/jms/Subscriber.java

   [2]: http://www.arunma.com/wp-content/uploads/2007/08/threads.thumbnail.JPG

   [3]: http://www.arunma.com/wp-content/uploads/2007/08/threads.JPG (Threads)

