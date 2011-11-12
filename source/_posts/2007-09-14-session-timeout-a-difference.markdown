---
author: Arun Manivannan
date: '2007-09-14 23:15:53'
layout: post
comments: true
slug: session-timeout-a-difference
status: publish
title: Session Timeout - A difference
wordpress_id: '279'
? ''
: - java
  - web.xml
  - weblogic.xml
---

The number of _**MINUTES**_ after which a web app times out is defined in the
web.xml this way.

<web-app> .... <session-config> <session-timeout>60</session-timeout>
</session-config> .... </web-app>

The WebLogic Server waits TimeoutSecs (in _**SECONDS**_) before timing out a
session as shown below: The default value, if not specified, is _**3600
secs**_.

<weblogic-web-app> .... <session-descriptor> <session-param> <param-
name>TimeoutSecs</param-name> <param-value>7200</param-value> </session-param>
</session-descriptor> .... </weblogic-web-app>

When timeout is set in both the deployment descriptors, the web.xml entry
**_OVERRIDES_** the one defined in the weblogic.xml. This preference can be
changed by a special value.

<session-config> <session-timeout>**-2**</session-timeout> </session-config>

This will let the app use the TimeoutSecs defined in the weblogic.xml for
session time out. There is yet another special value **-1**, in which case the
_**session never times out**_. Of course, the weblogic entry is overriden in
this case too.

