---
author: Arun Manivannan
date: '2007-03-02 15:05:38'
layout: post
comments: true
slug: non-recursive-find-in-unix
status: publish
title: Non-recursive find in Unix
wordpress_id: '114'
? ''
: - find prune unix
  - Unix
---

The find command in Unix always goes recursive. In order to avoid recursion
into subfolders, you have the `find -maxdepth `in certain flavours of Unix.
But `find -prune `is the standard way to restrict recursion into certain
subfolders.

Consider you have a logs folder /apps/myapp/data/logs and a subfolder
/apps/myapp/data/logs/history, you would like to move the files in the logs
folder alone and NOT the files in the history folder, then issue


**`find * \( ! -name history -prune \) -type f - exec cp {}
/apps/myapp/archive \;`**

keeping the pwd as /apps/myapp/data/logs.

If you wish to restrict more than one folder, then use

**`find * \( ! -name history -prune \) -o \( ! -name history -prune \) -type f
- exec cp {} /apps/myapp/archive \;`**

"-o" just says "OR"

