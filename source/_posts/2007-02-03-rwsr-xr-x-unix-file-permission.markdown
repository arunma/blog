---
author: Arun Manivannan
date: '2007-02-03 13:06:10'
layout: post
comments: true
slug: rwsr-xr-x-unix-file-permission
status: publish
title: -rwsr-xr-x Unix file permission
wordpress_id: '31'
? ''
: - Sticky bit
  - SUID
  - Unix
---

Everybody handling a Unix operating system would very well know what chmod 777
means. That the owner, group and the user of the file is given all permissions
(Read, Write and Execute on a particular file). This could otherwise be
written as "chmod ugo+rwx ". Meaning that you are giving User, Group and Owner
of the file, the rights to Read, Write and Execute the file.

Here comes the rws scenario. Best example that is available for this rws is
/usr/bin/passwd command (just issue a "ls -l /usr/bin/passwd") .

Normally, any user is allowed change HIS password. Meaning he can make an
entry or change HIS entry in the /etc/passwd file. But he can never be given
'WRITE' permissions on the file because he might end up disturbing other
person's password too. Only a ROOT user is allowed permissions on the
/etc/passwd file.

This is where the "rws" comes to picture. When we give "rws" permission to the
/usr/bin/passwd command, Unix would assume that the command is executed by the
ROOT user. (the user doesnt have permissions on the /etc/passwd file but the
root user has). Root user (RWS) permissions could be given on a file as chmod
4700 .

arun@arun-desktop:~/Desktop$ chmod 4700 hi.txt arun@arun-desktop:~/Desktop$ ls
-l hi.txt -rws------ 1 arun arun 0 2007-01-17 06:48 hi.txt

If you need to act as a group user of a file and not a normal user when
executing a particular command (as against the root user) then user "chmod
2700 "  arun@arun-desktop:~/Desktop$ chmod 2700 hi.txt arun@arun-
desktop:~/Desktop$ ls -l hi.txt -rwx--S--- 1 arun arun 0 2007-01-17 06:48
hi.txt

The 4 and 2 in the front of the chmod commands are called as SUID and SGID
bits.

What if we put a 1 instead of 4 and 2 (chmod 1700 ).

arun@arun-desktop:~/Desktop$ chmod 1700 hi.txt arun@arun-desktop:~/Desktop$ ls
-l hi.txt -rwx-----T 1 arun arun 0 2007-01-17 06:48 hi.txt

It shows a "T" in the place of "x" for a normal user. This "T" bit is called
as the Sticky bit.

"When the sticky bit is turned on for a directory users can have read and/or
write permissions for that directory, but they can only remove or rename files
that they own. The sticky bit on a file tells the operating system that the
file will be executed frequently. Files like this are kept in swap space even
when they aren't being executed. Although this takes up swap space it greatly
reduces the time it takes to execute the program. Some programs such as _vi_
have the sticky bit turned on by default on some Unixes."

[source : http://www.uwsg.iu.edu][1]

   [1]: http://www.uwsg.iu.edu/UAU/files/sticky.html

