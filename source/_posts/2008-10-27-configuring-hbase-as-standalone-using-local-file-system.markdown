---
author: Arun Manivannan
date: '2008-10-27 11:58:57'
layout: post
comments: true
slug: configuring-hbase-as-standalone-using-local-file-system
status: publish
title: Configuring HBase as standalone (using local file system)
wordpress_id: '296'
? ''
: - hbase
  - hbase
  - standalone
  - standalone
  - tutorial
---

For use of HDFS and Hadoop, please see my other [**post**][1].

Setting up HBase as standalone is comparatively simpler.  The only trouble you
would face is the Version Mismatching exception between the server and client
in which case you would have ideally used a different jar on classpath for the
client program and a different version of the HBase server would be running
on.

There is only one thing that you need to do to configure HBase as standalone.

a)  Let JAVA_HOME variable in your hbase-env.sh (bin directory) point to the
right path.

You can then play with the hbase shell utility

**(from the bin folder) > hbase shell**

Type in "**help**" to get a list of options available.

You can also use the example program available in
[**http://hadoop.apache.org/hbase/docs/r0.18.0/api/index.html **][2]to use
Java API to talk with HBase.

For use of the example program, you will be need to create a table on HBase.
Use hbase shell to execute the following DDL statement.

**create ‘myTable’,'myColumnFamily’ **

   [1]: http://arunma.com/2008/10/26/hadoop-and-hbase-setting-up-on-local-
machine/ (HBase and Hadoop)

   [2]: http://hadoop.apache.org/hbase/docs/r0.18.0/api/index.html

