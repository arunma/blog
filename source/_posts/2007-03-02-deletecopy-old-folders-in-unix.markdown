---
author: Arun Manivannan
date: '2007-03-02 14:55:01'
layout: post
slug: deletecopy-old-folders-in-unix
status: publish
title: Delete/Copy old folders in Unix
wordpress_id: '113'
? ''
: - Unix
---

It common to get a huge backlog of log files in any application. Worse is the
case when the application has a batch interface too.  And there comes the need
to delete the files which are older comes up. Or you might want to just
copy/move the files to an archive folder for later reference.

Here are the unix commands for them :

**Copy to archive folder**

Consier your log folder is /apps/myapp/data/logs and your archive folder is
/apps/myapp/archive/logs and you want to copy "files" and not directories
which are 5 days old , then

**`find /apps/myapp/data/logs -type f -mtime +5 -name '*.log' `****`- exec cp
{} /apps/myapp/archive/logs \;`**

and/or if you want to delete the files which are 5 days old,

**`find /apps/myapp/data/logs -type f -mtime +5 -name '*.log' - exec rm -f {}
\;`**

