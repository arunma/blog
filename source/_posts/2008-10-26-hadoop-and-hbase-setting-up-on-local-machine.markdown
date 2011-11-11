---
author: Arun Manivannan
date: '2008-10-26 12:47:51'
layout: post
slug: hadoop-and-hbase-setting-up-on-local-machine
status: publish
title: Hadoop and HBase - setting up as pseudo-distributed
wordpress_id: '294'
? ''
: - distributed
  - hadoop
  - hadoop
  - hbase
  - hbase
  - MasterNotRunningException
  - pseudo
  - setup
  - subrecord
---

For the past many months i have been out of blogging due to personal reasons.
By the Grace of God, things have just turned perfectly good for me.  So, i am
back to experimenting with some really cool stuff.

These instructions are an excerpt from

[http://www.michael-noll.com/wiki/Running_Hadoop_On_Ubuntu_Linux_(Multi-
Node_Cluster)][1]

and Hadoop, HBase API documentation.

1) Download Hadoop (hadoop-0.18.1) 2) Download HBase (hbase-0.18.0) 3) I just
setup the environment as Pseudo-Distributed.

a) Open up the hadoop-env.sh file in the conf directory of hadoop. Change the
JAVA_HOME directory to point to your own machine setup. Mine looks like this :

** export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.07 **

b) Open up the hbase-env.sh file in the conf directory of hbase and set
JAVA_HOME.

c) Edit hbase-site.xml and make your configuration tag look like this :

**<configuration> <property> <name>fs.default.name</name>
<value>hdfs://localhost/hbase</value> </property> </configuration> **

d) Make hadoop-site.xml to look like the following :

**<configuration> <property> <name>fs.default.name</name>
<value>hdfs://localhost/</value> </property> <property>
<name>dfs.replication</name> <value>1</value> </property> </configuration> **

e) Issue the following command inside the bin directory of your hadoop
./start-all.sh

** eg : [arun@arun-laptop:~/softy/hadoop-0.18.1][2]/bin$ ./start-all.sh **

f) Issue the following command to start HBase

** eg : [arun@arun-laptop:~/softy/hbase-0.18.0][3]/bin$ ./start-hbase.sh **

You can play with the shell if you wanted to.

[arun@arun-laptop:~/softy/hbase-0.18.0][3]/bin$ ./hbase shell

There is an example on
[http://hadoop.apache.org/hbase/docs/r0.18.0/api/index.html][4] which

i used to test my setup. The example would need us to create a table 'myTable'
with a column family 'myColumnFamily'

Execute the following command on the shell

** create 'myTable','myColumnFamily' **

Here is what i got as output on execution of the example program :

** Found row: myRow with value: timestamp=1225023942810,
value=columnQualifier1 value! **

Let me know if I could help you with any of the setup problems. I didnt copy
the hadoop-site.xml to hbase conf. Later i learnt that it is useful only on
"truly" distributed environment.

The above setup instructions were just derived from a)
[http://hadoop.apache.org/core/docs/r0.18.1/api/index.html][5] and b)
[http://hadoop.apache.org/hbase/docs/r0.18.0/api/index.html][4]

Food for the bots : Here is the list of exceptions i got during the process of
setting this up :

INFO  20:39:19 [org.apache.hadoop.hbase.client.HConnectionManager$TableServers
(202):getMaster]:

Attempt 0 of 10 failed with <java.io.IOException: Call failed on local
exception>.

Retrying after sleep of 5000

Exception in thread "main" org.apache.hadoop.hbase.MasterNotRunningException:
localhost:60000

The above log just means that the hbase and hadoop are not started at all.
Check the log for exceptions.

Remember, Hadoop must be started first followed by HBase.

   [1]: http://www.michael-noll.com/wiki/Running_Hadoop_On_Ubuntu_Linux_
(Multi-Node_Cluster)

   [2]: mailto:arun@arun-laptop:%7E/softy/hadoop-0.18.1

   [3]: mailto:arun@arun-laptop:%7E/softy/hbase-0.18.0

   [4]: http://hadoop.apache.org/hbase/docs/r0.18.0/api/index.html

   [5]: http://hadoop.apache.org/core/docs/r0.18.1/api/index.html

