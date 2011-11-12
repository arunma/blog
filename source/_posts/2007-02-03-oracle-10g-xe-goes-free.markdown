---
author: Arun Manivannan
date: '2007-02-03 12:42:38'
layout: post
comments: true
slug: oracle-10g-xe-goes-free
status: publish
title: Oracle 10g XE goes free
wordpress_id: '9'
? ''
: - opensource
  - oracle
  - Uncategorized
---

If you are Oracle user at home, you should have really felt the pain of the
database server eating most of your system resources. Added to it, in all
possibilities, we are using an illegal copy of the Personal Edition or the
Enterprise Edition.

You would never imagine running Java applications against Oracle just because
of the simple reason we can never run our application servers and database
server and, of course, our IDE in a single machine. So, we just move in for
MySQL, Postgre or other open-source alternatives.

You would have already known that DB2, just a few months back, came up with a
free edition of its Database. And Microsoft is also coming up with its free
edition of SQL Server 2005 as 'Express Edition'

Oracle now joins the bandwagon. And, as always, Oracle is our favourite
database.

(Please go through the document (at least the faq) and the pdf attachment for
more details). The twp_general_10gdb_product

_family.pdf has a wonderful "feature comparison" table at the end of it.

Please dont get alarmed when they say Java development is not possible in
Oracle 10g XE. They just mean that we cannot write Oracle PL/SQL stored
procedures in Java. And i've still not seen anybody writing

"CREATE PROCEDURE DEPT_PROCEDURE AS LANGUAGE JAVA"

That because Oracle XE doesnt come with an inbuilt JVM. (You know Oracle 9i
came up with JRE 1.4 bundled inside). Regular SQL, (ALL) PL/SQL, JDBC calls
will just work fine.

Best part, Oracle 10g XE comes just as a 250MB iso image.

Linux users, who were denied of the privilege of using Oracle, just because we
dont get a pirated version of the full database, can now download their RPM
installers direct from the oracle site. Debian users (Ubuntu, Kubuntu, MEPIS,
Mandriva, CentOS) can download their .deb installers. All installers are
around the same size.

Good luck.

