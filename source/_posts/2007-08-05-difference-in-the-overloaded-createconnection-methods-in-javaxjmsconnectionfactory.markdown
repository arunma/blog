---
author: Arun Manivannan
date: '2007-08-05 16:14:56'
layout: post
slug: difference-in-the-overloaded-createconnection-methods-in-javaxjmsconnectionfactory
status: publish
title: Difference in the overloaded createConnection() methods in javax.jms.ConnectionFactory
wordpress_id: '259'
? ''
: - JMS
  - overloaded
  - password
  - username
---

This is the first thing you do when you work with JMS -- Get a connection. **
`ConnectionFactory factory =
(ConnectionFactory)ic.lookup("MyConnectionFactory");`**

`**conn = factory.createConnection(); **`// You call either this** `conn =
factory.createConnection(userName, password);` **// or this.

But, what is this "username" and "password" in your connection, when you have
already logged into your application server and there are no provisions to use
them in the configured ConnectionFactory either.

Every server has a default (active) security realm. A security realm is a
container that includes users, groups, security roles, security policies, and
security providers, that are used to protect WebLogic resources.

A realm can have one or more users and these users can belong to one or more
groups.

**WebLogic Server has the following groups:**

*** Administrators * Deployers * Operators * Monitors * App Testers**

Your login information for the admin server console is managed in this default
security realm. The user who logs in to the server console is the default
administrator. He belongs to the group "Administrators".

I have a scenario, wherein a wholesaler and retailer are going to make use of
the JMS Server for interchanging their messages on their sales deals.

Neither the wholesaler nor the retailer is the owner of the JMS Server. They
are just guests who make use of this USERNAME and PASSWORD, passed in the
factory.createConnection(userName, password) to create a connection to their
destination(Topic/Queue).

This is a way in which clients are authorized to access their relevant
destinations. In other words, only those clients who are authorized can have
access to the destinations.

Here is how you configure users and groups in the security realm of Weblogic
9.2

[![1.jpg][1]][2]

[![2.jpg][3]][4]

[![3.jpg][5]][6]

[![5.jpg][7]][8]

[![6.jpg][9]][10]

[![7.jpg][11]][12]

   [1]: http://www.arunma.com/wp-content/uploads/2007/08/1.thumbnail.jpg

   [2]: http://www.arunma.com/wp-content/uploads/2007/08/1.jpg (1.jpg)

   [3]: http://www.arunma.com/wp-content/uploads/2007/08/2.thumbnail.jpg

   [4]: http://www.arunma.com/wp-content/uploads/2007/08/2.jpg (2.jpg)

   [5]: http://www.arunma.com/wp-content/uploads/2007/08/3.thumbnail.jpg

   [6]: http://www.arunma.com/wp-content/uploads/2007/08/3.jpg (3.jpg)

   [7]: http://www.arunma.com/wp-content/uploads/2007/08/5.thumbnail.jpg

   [8]: http://www.arunma.com/wp-content/uploads/2007/08/5.jpg (5.jpg)

   [9]: http://www.arunma.com/wp-content/uploads/2007/08/6.thumbnail.jpg

   [10]: http://www.arunma.com/wp-content/uploads/2007/08/6.jpg (6.jpg)

   [11]: http://www.arunma.com/wp-content/uploads/2007/08/7.thumbnail.jpg

   [12]: http://www.arunma.com/wp-content/uploads/2007/08/7.jpg (7.jpg)

