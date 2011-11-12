---
author: Arun Manivannan
date: '2007-03-08 04:17:44'
layout: post
comments: true
slug: flashback-and-purge-in-oracle-10g
status: publish
title: Flashback and Purge in Oracle 10g
wordpress_id: '144'
? ''
: - flashback
  - oracle
  - purge
  - restore
  - tables
  - undrop
---

From Oracle 10g, Dropped tables can be restored. Meaning, you can now rollback
one of your DDL statement. This is how you do it. ` **drop table t;**`

Table dropped.

**desc t;**

ERROR: ORA-04043: object t does not exist

**select count(*) from t;**

**select count(*) from t;**

ERROR at line 1: ORA-00942: table or view does not exist ** **

**flashback table t to before drop; **

**Flashback complete.**

You have now restored your table.

Behind the scenes, what happens is that your dropped table is renamed and just
gets restored from the recyle-bin when you "flashback". **` drop table t;`**

Table dropped.

**select table_name from user_tables;**

no rows selected

**select object_name from recyclebin;**

OBJECT_NAME

------------------------------

BIN$7oTtcup30ZfgMAGK/3hjKw==

**flashback table t to before drop;**

Flashback complete.

**select object_name from recyclebin;**

no rows selected

**select table_name from user_tables; ** TABLE_NAME

------------------------------

T

**So, your table will not really be dropped. But just like any operating
system moved to the recycle-bin from which you can restore later. **

If you dont want your tables to be restored and be gone forever, then **` drop
table t purge;`**

Table dropped.

**select table_name from user_tables;**

no rows selected

**select object_name from recyclebin;**

no rows selected

source: [Ask Tom][1]

   [1]: http://asktom.oracle.com

