---
author: Arun Manivannan
date: '2008-06-02 04:59:10'
layout: post
comments: true
slug: is-jcatapult-a-lightweight-spring
status: publish
title: Is JCatapult a lightweight Spring?
wordpress_id: '287'
? ''
: - comparison
  - frameworks
  - jcatapult
  - spring
---

The google code project released its [RC2 ][1]two weeks back and boasts that
the framework is currently being used on many live projects.  From what I see,
JCatapult, just like Spring, is a collection of frameworks.   And the good
thing in it is that it has the power to cater to the technological needs of
even a large scale project.

Webwork has always proved that it is the best framework. Struts 2.0,
therefore, cant be any better.  Hibernate for ORM, Guice for dependency
injection, Freemarker for templating, a brand new feature "Modules" (yet to
give it a try) which enables plugging of features into the main webapplication
-- all sounds very good.

IMHO, there are a couple of notable differences between Spring and JCatapult
though JCatapult might have an altogether different vision.

1) **Spring gives more flexibility.** So, you get to choose whatever set of
tools/frameworks you need to use.  I am really not sure how hard will it be
now to switch the front end to a desktop application than Struts 2.0.  I dont
personally like Spring Webflow but would prefer Struts 2.0 for that. But if i
really wanted to use something totally different, Spring will still make
sense.

2) JCatapult should be very good for new projects considering the fact that
the whole list of frameworks extensively use annotations. **The ground reality
is that many companies still use Java 1.4 **compliant web/application servers.
Spring, on the contrary, still supports 1.4 and becomes a first class
candidate for "pluggable" modules of the already existing applications.

But still, JCatapult is just in its release candidate and it is not fair
enough to compare it with a more mature framework like Spring.  **The
documentation also gives us clues that it will support more and more
frameworks in the future.**

But isn't it "reinventing the wheel"?

   [1]: http://www.jcatapult.org/announcements (Release Candidate
Announcement)

