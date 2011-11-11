---
author: Arun Manivannan
date: '2007-08-03 19:48:59'
layout: post
slug: interchange-column-values-in-a-single-update-query
status: publish
title: Interchange column values in a single update query
wordpress_id: '251'
? ''
: - strange
  - update multiple columns
  - update query
---

Have you ever met with a situation, wherein a single SQL update query should
interchange the values of two columns? If you have had a chance to look at the
update statement's syntax, you would have immediately answered this.

UPDATE {table_name | view_name} SET [{table_name | view_name}] {column_list |
variable_list | variable_and_column_list} ... [, {column_listN |
variable_listN | variable_and_column_listN}]] [WHERE clause]

Consider a table named CLIENT. The table has two columns named first_name and
last_name. If you want to interchange the two column values i.e, assign
first_name to the last name and vice-versa, here is the query..

UPDATE client SET first_name = last_name, last_name = first_name

You could alternatively set a value to the columns like this..

UPDATE client SET first_name = 'Arun', last_name = 'MA'

Remember, the datatypes and the width of the two columns must fit within each
other..!!!

