---
author: Arun Manivannan
date: '2007-02-03 10:38:35'
layout: post
comments: true
slug: eclipse-the-forgotten-path
status: publish
title: Eclipse.. the forgotten path
wordpress_id: '7'
? ''
: - eclipse
  - equinox
  - java
  - Uncategorized
---

Ever tried opening up the plugins folder of Eclipse 3.1 or greater? What is
the difference between the previous versions and the current ones? Just look
at the screenshots.

[![Equinox bundles][1]][1] Equinox is an Eclipse project to structure Eclipse
software not just as a collection of plugins, but as a collection of OSGi
bundles. OSGi bundles is an approach to break an application into components
(jar files), large collections of classes with a unified interface that is
well-encapsulated and easily reusable amongst multiple applications.

Most important part : OSGi also enables applications to dynamically load (and
better yet, unload as well) these components at runtime as optional
functionality is needed (and no longer needed). Meaning your SQL Plugins or
XML Plugins actually do not get loaded during startup. They are runtime loads.
God... my head rolls.

This helps the application manage its footprint, e.g. the memory that it
consumes in order to run. Rather than using memory to load every option that
any user may ever need, it only loads the kernel functionality and then loads
optional functionality when the user asks for it by loading OSGi bundles.
Equinox helps formalize an approach to developing Eclipse applications as
these OSGi bundles.

A particularly interesting part of Equinox is the Server Side OSGi (sub?)
project. OSGi has mostly been used to create desktop applications. This
enables you to start the application quickly with a small footprint and then
load options as needed. What if you could do the same in a server application?
The application starts quickly, then as client apps invoke optional
functionality, the app dynamically loads components to provide the
functionality. Interesting idea, so check it out at
[http://www.eclipse.org/equinox/server/][2] (project under development)

   [1]: http://beanpicks.wordpress.com/files/2007/02/equinoxbundles.png

   [2]: http://www.eclipse.org/equinox/server/

