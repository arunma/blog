---
author: Arun Manivannan
date: '2007-03-15 02:10:46'
layout: post
comments: true
slug: duplicate-entry-xxx-for-key-xxx-mysql-and-hibernate
status: publish
title: Duplicate entry xxx for key xxx — MySQL and Hibernate
wordpress_id: '167'
? ''
: - duplicate entry
  - for key
  - hibernate
  - mysql
  - Uncategorized
---

This is one problem which ate around 2 hours of last night. Here are the
possible solutions

1) There is a genuine case of duplication of the id column. Try querying the
max (IDCOLUMN) from the table.

2) If the message says Duplicate entry '127' or '32767' or any of the max
values in the following table

**Type**

**Bytes**

**Minimum Value**

**Maximum Value**



**(Signed/Unsigned)**

**(Signed/Unsigned)**

`TINYINT`

1

`-128`

`127`



`0`

`255`

`SMALLINT`

2

`-32768`

`32767`



`0`

`65535`

`MEDIUMINT`

3

`-8388608`

`8388607`



`0`

`16777215`

`INT`

4

`-2147483648`

`2147483647`



`0`

`4294967295`

`BIGINT`

8

`-9223372036854775808`

`9223372036854775807`



`0`

`18446744073709551615`

then you need to change your datatype. Your next increment value isn't getting
accommodated within the datatype.

3) If you have an increment id in your Hibernate, please check whether your
datatype is varchar in mysql. If it is varchar in mysql and if your hibernate
mapping file maps to an Integer property in your Value Object, this problem is
sure to occur after your 9th record.

