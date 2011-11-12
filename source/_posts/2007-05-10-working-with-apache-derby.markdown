---
author: Arun Manivannan
date: '2007-05-10 02:09:34'
layout: post
comments: true
slug: working-with-apache-derby
status: publish
title: Working with Apache Derby
wordpress_id: '221'
? ''
: - java 6.0
  - Uncategorized
---

As you know, Java 6.0 comes bundled with Apache Derby.  The "db" folder inside
the JDK 6.0 directory is our bundled Database. Here is the list of things i
did on the db.

**1) Connect **

    But before connecting we need to set the classpath for Apache Derby. Just
add the following lines to your classpath.

     **$JAVA_HOME\db\lib\derby.jar;$JAVA_HOME\db\lib\derbytools.jar;**

    Basically, the **derby.jar** is the core apache derby db purely written in
Java. (comes around 2 MB).  [More on Apache Derby >>][1]

    And the** derbytools.jar** gives one interesting tool called the "ij" for
that command line db access.

      **java org.apache.derby.tools.ij ** will give you a "ij" prompt.  Type
help and you will get a list of commands you can play with.

      ij> help;

[![ij help list of commands][2]][3]

      Finally, to connect to a database, use the following command.

      **connect 'jdbc:derby:myfirstdb;create=true'; **

     The String following the "connect" keyword just tells us that you are
using **org.apache.derby.jdbc.EmbeddedDriver** (jdbc:derby) to connect to
**myfirstdb **(your database), which has not been created yet. So you create
it (create=true).  So, the next time you want to connect to the same database,
**connect 'jdbc:derby:myfirstdb' ; **will do.

**2) Create table**

**ij> show tables;**

TABLE_SCHEM |TABLE_NAME |REMARKS

------------------------------------------------------------------------

0 rows selected

**ij> create table emp (empname varchar(20), empno int);**

0 rows inserted/updated/deleted

**3) Insert a row to table and query it**

**ij> insert into emp values ('arun',101);**

1 row inserted/updated/deleted

**ij> select * from emp;**

EMPNAME |EMPNO

--------------------------------

arun |101


1 row selected

[**>>more on how to use Java to connect to Derby in embedded and network
mode**][4]** **

   [1]: http://db.apache.org/derby/

   [2]: http://www.arunma.com/wp-content/uploads/2007/05/ij-help.thumbnail.JPG

   [3]: http://www.arunma.com/wp-content/uploads/2007/05/ij-help.JPG (ij help
list of commands)

   [4]: http://db.apache.org/derby/papers/DerbyTut/embedded_intro.html

