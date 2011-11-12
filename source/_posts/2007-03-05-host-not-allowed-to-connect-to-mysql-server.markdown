---
author: Arun Manivannan
date: '2007-03-05 23:36:47'
layout: post
comments: true
slug: host-not-allowed-to-connect-to-mysql-server
status: publish
title: Host not allowed to connect to mysql server
wordpress_id: '125'
? ''
: - host not allowed
  - mysql
  - Uncategorized
---

The reason that we get this error in mysql when a remote machine tries to
connect to mysql server is that by default mysql does not support remote
access.

So, we need to specify the details of the host machine in the mysql server
(the actual machine where mysql runs).

So, my machine's IP is 192.168.1.10 and my friend's machine (in which mysql
runs is 192.168.1.20)

`$ mysql -u root -p mysql> use mysql; mysql> grant all privileges on *.* to
arun@192.168.1.10 identified by 'orange' with grant option; mysql> exit`

If you are not sure of the hostname, just replace the 192.168.1.10 with '%'

