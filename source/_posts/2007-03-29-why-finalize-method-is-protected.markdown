---
author: Arun Manivannan
date: '2007-03-29 09:22:15'
layout: post
slug: why-finalize-method-is-protected
status: publish
title: Why finalize method is protected?
wordpress_id: '200'
? ''
: - finalize
  - java
  - protected
  - Uncategorized
---

I used to wonder why all methods in the java.lang.Object is public and only
finalize is protected.  Finalize is just a callback method which is supposed
to be called by the JVM.  So, ideally, it should be private.  Here is a mind-
blowing explanation of [why finalize is protected][1]?

   [1]: http://www.me.umn.edu/~shivane/blogs/cafefeed/2005/09/why-is-finalize-
method-protected.html

