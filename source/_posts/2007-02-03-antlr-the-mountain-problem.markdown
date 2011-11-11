---
author: Arun Manivannan
date: '2007-02-03 18:36:10'
layout: post
slug: antlr-the-mountain-problem
status: publish
title: ANTlr - Weblogic and Hibernate problem
wordpress_id: '41'
? ''
: - hibernate
  - java
  - weblogic
---

Recently, I was trying to integrate Struts with Hibernate 3.2 under Weblogic.
And i had this big pestering exception...

javax.servlet.ServletException: ClassNotFoundException:
org.hibernate.hql.ast.HqlToken [from com.g2h.biz.vo.Category category] at webl
ogic.servlet.internal.ServletStubImpl.createServlet(ServletStubImpl.java:909)
at weblogic.servlet.internal.ServletStubImpl.createInstances(ServletStubImpl.j
ava:873) at weblogic.servlet.internal.ServletStubImpl.prepareServlet(ServletSt
ubImpl.java:812) at weblogic.servlet.internal.WebAppServletContext.preloadServ
let(WebAppServletContext.java:3281) at weblogic.servlet.internal.WebAppServlet
Context.preloadServlets(WebAppServletContext.java:3226) at weblogic.servlet.in
ternal.WebAppServletContext.preloadResources(WebAppServletContext.java:3207)
at weblogic.servlet.internal.HttpServer.preloadResources(HttpServer.java:694)
at weblogic.servlet.internal.WebService.preloadResources(WebService.java:483)
at weblogic.servlet.internal.ServletInitService.resume(ServletInitService.java
:30) at weblogic.t3.srvr.SubsystemManager.resume(SubsystemManager.java:131) at
weblogic.t3.srvr.T3Srvr.resume(T3Srvr.java:966) at
weblogic.t3.srvr.T3Srvr.run(T3Srvr.java:361) at
weblogic.Server.main(Server.java:32)

The reason for this problem is this. Both Weblogic and Hibernate was using
"antrl.jar". Weblogic 8.1, that i was using, had an "antlr" jar bundled inside
its weblogic.jar. Since server libraries had preference over the jars in our
application, hibernate wasnt using the latest antlr jar in my web
application's lib folder.

Solution that i used :

Put the following lines in your ".cfg.xml" inside your session-factory tag

[![classicquery][1]][2] There is a biggggg discussion in the [hibernate
forum][3] on this issue. It also had another solution for weblogic. To add the
following tag inside weblogic.xml

[![weblogic.xml][4]][5]

   [1]: http://beanpicks.wordpress.com/files/2007/02/classicquery.png

   [2]: http://beanpicks.wordpress.com/files/2007/02/classicquery.png
(classicquery)

   [3]: http://forum.hibernate.org/viewtopic.php?t=939468

   [4]: http://beanpicks.wordpress.com/files/2007/02/weblogicxml.png

   [5]: http://beanpicks.wordpress.com/files/2007/02/weblogicxml.png
(weblogic.xml)

