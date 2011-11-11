---
author: Arun Manivannan
date: '2007-03-06 01:13:20'
layout: post
slug: avoid-caching-in-internet-explorer-for-ajax-requests
status: publish
title: Avoid caching in Internet Explorer for AJAX requests
wordpress_id: '126'
? ''
: - ajax
  - caching in IE
  - Uncategorized
---

Internet Explorer and a few other browsers cache GET requests for faster
browsing.  Good for normal pages. Bad for AJAX. So, for repeated AJAX
requests, you will get a cached data instead of the actual response from the
server-side.  (Firefox, the prince of browsers does not seem to have this
problem).

Two Options come up for this problem.

**1) Use POST method for AJAX requests or**

**2) Just append some dummy parameter **which has a different value for
different GET requests. Just gives the browser an impression that its a fresh
request.

So, Instead of this

var url = 'getProducts.jsp?productId=123'

use this:

var url = 'getProducts.jsp?productId=123'  + **"&dummy=" + new
Date().getTime();**

