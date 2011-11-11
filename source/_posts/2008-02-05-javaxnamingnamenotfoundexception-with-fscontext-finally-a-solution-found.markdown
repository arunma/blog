---
author: Arun Manivannan
date: '2008-02-05 22:56:16'
layout: post
slug: javaxnamingnamenotfoundexception-with-fscontext-finally-a-solution-found
status: publish
title: NameNotFoundException with FSContext
wordpress_id: '285'
? ''
: - FSContext
  - java
  - javax.naming.NameNotFoundException
  - NameNotFoundException
  - problems
  - programming
  - RefFSContext
  - RefFSContextFactory
---

This was my trace. Never thought i was so dumb. I was breaking my head on this
for about two hours. ` javax.naming.NameNotFoundException; remaining name
'c:\temp' at com.sun.jndi.fscontext.FSContext.checkExists`

`(FSContext.java:860) at com.sun.jndi.fscontext.FSContext.`

`checkIsDirectory(FSContext.java:893) at
com.sun.jndi.fscontext.FSContext.(FSContext.java:148) at
com.sun.jndi.fscontext.FSContext.(FSContext.java:123) at
com.sun.jndi.fscontext.RefFSContext.(RefFSContext.java:136) at
com.sun.jndi.fscontext.RefFSContextFactory.`

`createContext(RefFSContextFactory.java:32) at
com.sun.jndi.fscontext.RefFSContextFactory.`

`createContextAux(RefFSContextFactory.java:37) at
com.sun.jndi.fscontext.FSContextFactory.`

`getInitialContext(FSContextFactory.java:65) at
javax.naming.spi.NamingManager.getInitialContext(Unknown Source) at
javax.naming.InitialContext.getDefaultInitCtx(Unknown Source) at
javax.naming.InitialContext.init(Unknown Source) at
javax.naming.InitialContext.(Unknown Source) at
com.ml.cortex.eds.dao.ConnectionManager.`

`createDataSources(ConnectionManager.java:34)`

**The solution is simple. Before using a url in the FSContext create the
directory. In my case, c:\temp. Create the directory "temp" inside c:\
drive.**

