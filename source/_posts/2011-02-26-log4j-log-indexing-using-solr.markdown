---
author: admin
date: '2011-02-26 23:02:20'
layout: post
slug: log4j-log-indexing-using-solr
status: publish
title: log4j Log Indexing using Solr
wordpress_id: '437'
? ''
: - indexer
  - java
  - log4j
  - lucene
  - opensource
  - programming
  - searcher
  - solr
---

We are finding it very hard to monitor the logs spread over a cluster of four
managed servers. So, I am trying to build a simple log4j appender which uses
solrj api to store the logs in the solr server. The idea is to use leverage
REST of solr to build a better GUI which could help us

1) search the logs and the display the previous and the next 50 lines or so
and

2) tail the logs

Being awful on front ends, I am trying to cookup something with GWT (a
prototype version). I am planning to host the project on googlecode under ASL.

Greatly appreciate if you could throw some insights on

1) Whether it makes sense to create a project like this ?

2) Is using Solr for this an overkill?

3) Any suggestions on web framework/tool which will help me build a tab-based
front end for tailing.


I owe you guys. Thanks.

