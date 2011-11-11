---
author: admin
date: '2011-03-15 02:17:01'
layout: post
slug: log4j-jsonlayout-and-jlogindexer
status: publish
title: log4j JSONLayout and JLogIndexer
wordpress_id: '439'
? ''
: - java
  - personal project flex adobe log4j solr lucene activemq
  - programming
---

As I mentioned in my previous post, I am working on building a Solr based
log indexing and search.  My idea was simple.  Write a custom appender, use
XML Layout, parse the XML into a Document and use SolrJ to push to Solr.
Very soon reality struck me :

**1)  log4j XML Layout is not a good idea for our requirement**.  I really
dont want to spend time on parsing about 100 XMLs every second.  That is a lot
of time even for a StAX based [Woodstox][2].  So, I just extended log4j layout
and over-rid a couple of methods to create a JSON Layout.

2)  Using [Jackson Streaming API][3] to parse the JSON string from the Layout
opened my eyes.  There were too many external dependency libraries (jackson,
solrj and their dependent jars) that I was adding on to the application which
ultimately will all go to the host application.  That is totally insane.

So, I figured out that way to go is to use

1) log4j JMS appender to put JSON strings into

2) Active MQ running on a app server running Solr.

I am hoping that this should give us the following benefits :

1) **No complications on the host application**. (copying libraries,
classloader issues with library version incompatibility etc)

2) Non-log4j based java applications and non-java applications could use one
of the various **connectivity options available with ActiveMQ t**o put
messages into its queue.

[http://activemq.apache.org/connectivity.html][4]

3)  **Extension and replacing the layout and message parsing**.

4)  **Solr Document construction and the interface **(initial version will
still be on SolrJ) can be customized.


This weekend should be pretty awesome then.


   [2]: http://woodstox.codehaus.org/

   [3]: http://wiki.fasterxml.com/JacksonDownload

   [4]: http://activemq.apache.org/connectivity.html (ActiveMQ connectivity
options)

