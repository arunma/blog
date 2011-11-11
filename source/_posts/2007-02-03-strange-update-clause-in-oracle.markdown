---
author: Arun Manivannan
date: '2007-02-03 12:56:01'
layout: post
slug: strange-update-clause-in-oracle
status: publish
title: Strange UPDATE clause in Oracle
wordpress_id: '23'
? ''
: - merge clause
  - oracle
  - update clause
---

[![master table][1]][2]

[![staging_table.png][3]][4]

I had this problem at work a few weeks back and thought i could share with
you. Most of you must have known this. But yet, I thought this post could be
useful so that i could come back here and refresh myself. `` I have a staging
table, a few colums of which are populated from direct flat file loads (Oracle
SQL Loader utility). I need to populate a few other columns of this table
looking up from a master table. Finally, after all columns has been populated,
i move the staging table records to a "fair copy table".

Let me give you an example. Our staging table will be staging_table. Four
columns of it (key_to_all_locks, flat_file_load_colm_1, flat_file_load_colm_2
and flat_file_load_colm_3) are flat file loads. (please look the screenshot
for full description)

I have a master table master_table which has many columns. Out of which i need
to lookup three columns (lookup_colm1, lookup_colm2 and lookup_colm3) using
the key_to_all_locks column.

And i will do a lookup only when the lookup_or_not_flag is 'Y'. And i should
not unnecessarily lookup for the 'already populated records' from the
master_table.

One other information, a single flat file load will populate a minimum of 10K
records into the staging_table.

Simple problem. But if i had to do this the Java way, i need to execute a
select query for the records whose values are not yet populated from the
master_table and then loop through the ResultSet. Meaning, i should avoid
lookups for those records for which the flat_file_load_colm_1,
flat_file_load_colm_2 and flat_file_load_colm_3) are not null and loop through
the rest of the records who needs lookup (lookup_or_not_flag is 'Y').

While looping through the ResultSet, i should fetch the key_to_all_locks
column and then execute a select on the master_table to fetch all the columns
which needs to be populated in the staging_table. And finally, execute an
update query on the staging_table with the newly fetched values.

Looks like a lot of job for the Garbage collector.

Doing it the PL/SQL way would also mean the same thing. Only advantage over
the Java way is that we could escape with lesser number of Java-DB bridge
hits).

I was planned to use a MERGE statement for this scenario. For the benefit of
those, who just like me, forgot what MERGE statement really does, here is an
explanation from the Oracle Handbook.

Merge statements 1) provides the ability to conditionally update or insert
data into a table 2) performs an UPDATE if the row exists and an insert if its
a new row.

Syntax

MERGE INTO table_name AS table_alias USING (table|view|sub_query) AS alias ON
(join_condition) WHEN MATCHED THEN UPDATE SET col1=col_val1, col2=col2_val
WHEN NOT MATCHED THEN INSERT (column_list) VALUES (column_values);

and this is what i did. Since i just want an UPDATE and not an INSERT, this is
the query i derived.

MERGE INTO staging_table AS st USING master_table as mt ON
st.key_to_all_locks=mt.key_to_all_locks WHEN MATCHED THEN UPDATE SET
st.lookup_colm_from_master_table1=lookup_colm1,
st.lookup_colm_from_master_table2=lookup_colm2,
st.lookup_colm_from_master_table3=lookup_colm3 WHEN NOT MATCHED THEN INSERT
VALUES (NULL,NULL,NULL)

(WHEN MATCHED AND WHEN NOT MATCHED are optional clauses only from Oracle 10g.
Unfortunately i was working on 9i)

Only later did i find that i was in deep trouble when i came to know that in a
MERGE statement, the source and the target tables should have the same
structure. But i had some 11 columns in the master_table and 8 columns in
staging_table. And the MERGE INTO clause cannot follow a VIEW. A Table name is
needed. Only a USING clause can follow a VIEW.

So, the oly alternative i had is to use the UPDATE clause. I can use one
subquery per column like  UPDATE staging_table SET
st.lookup_colm_from_master_table1=(SELECT lookup_colm1 FROM master_table where
key_to_all_locks=?), st.lookup_colm_from_master_table2=(SELECT lookup_colm2
FROM master_table where key_to_all_locks=?),
st.lookup_colm_from_master_table3=(SELECT lookup_colm3 FROM master_table where
key_to_all_locks=?)

Meaning there is one table level SEARCH for master_table per column.
master_table actually is a huggeeeeeeeee table.

Then i came across this particular UPDATE clause which i guess you might find
helpful. I dont really know whether this is ANSI standard and could be used
for other RDBMS. But this is really cool. And best of it, it solved by
problem.  UPDATE staging_table SET (lookup_colm_from_master_table1,
lookup_colm_from_master_table2, lookup_colm_from_master_table3)= (SELECT
lookup_colm1, lookup_colm2, lookup_colm3 from master_table where
key_to_all_locks=?) WHERE lookup_colm_from_master_table1 IS NOT NULL AND
lookup_or_not_flag='Y' AND key_to_all_locks=? I know i am setting the same
value of key_to_all_locks twice. Of course they are value inputs for two
different tables. Just let me know if its possible to set key_to_all_locks
only once.

   [1]:
http://beanpicks.wordpress.com/files/2007/02/master_table1.thumbnail.png

   [2]: http://beanpicks.wordpress.com/files/2007/02/master_table1.png (master
table)

   [3]:
http://beanpicks.wordpress.com/files/2007/02/staging_table.thumbnail.png

   [4]: http://beanpicks.wordpress.com/files/2007/02/staging_table.png
(staging_table.png)

