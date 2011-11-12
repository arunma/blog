---
author: Arun Manivannan
date: '2008-01-24 18:44:43'
layout: post
comments: true
slug: processing-files-over-network-slows-down-programs-part-2
status: publish
title: Processing files over network slows down programs — Part 2
wordpress_id: '284'
? ''
: - concurrency
  - copy
  - copy files
  - file
  - java
  - java.util.concurrent
  - mulithread
  - NIO
  - source code
  - threadpoolexecutor
  - Uncategorized
---

There are a few other things i wanted to share. I actually use the
java.util.concurrent.ThreadPoolExecutor to copy files. For those using Java
1.4, here is your gateway to concurrency :  [http://backport-
jsr166.sourceforge.net/][1]

Here goes my ThreadPool code. You surely could write better code than this.

**LinkedBlockingQueue archiverTaskQueue = new LinkedBlockingQueue();
ThreadPoolExecutor archiverExecutor = new ThreadPoolExecutor(50, MAXTHREADS,
50000L, TimeUnit.MILLISECONDS,archiverTaskQueue); File tempCurrentFile=new
File(tempDestinationDir, archiveFileName); archiver = new
Archiver(tempCurrentFile, new File(actualDestinationDir, fileName));
archiverExecutor.execute(archiver);**

Forgot to mention, I use NIO to copy files. I understand that there are people
for and against NIO. My reason for using NIO is just it sounded exciting.

**Source code : [Archiver.java][2]**

   [1]: http://backport-jsr166.sourceforge.net/

   [2]: http://arunma.com/files/code/thread/Archiver.jar (Multithreadable
copier)

