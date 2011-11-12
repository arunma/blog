---
author: Arun Manivannan
date: '2007-02-19 00:19:01'
layout: post
comments: true
slug: fetch-rows-between-x-and-y-in-oracle
status: publish
title: Fetch Rows between X and Y in Oracle
wordpress_id: '98'
? ''
: - oracle
  - Uncategorized
---

If you want to fetch the results between Xth row and Yth row in an Oracle
resultset, here is the most optimal solution. This works in Oracle 8.1 and
above. ` select * from ( select a.*, rownum rnum from ( YOUR_QUERY_GOES_HERE
-- including the order by ) a where rownum < = MAX_ROWS ) where rnum >=
MIN_ROWS ` source : [Ask Tom ][1]

   [1]: http://asktom.oracle.com

