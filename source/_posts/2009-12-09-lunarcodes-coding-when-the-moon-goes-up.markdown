---
author: Arun Manivannan
date: '2009-12-09 03:37:44'
layout: post
comments: true
slug: lunarcodes-coding-when-the-moon-goes-up
status: publish
title: Lunarcodes - Coding when the moon goes up
wordpress_id: '358'
? ''
: - java
  - java
  - lunarcodes
  - lunarcodes
  - personal
  - personal
  - programming
  - programming
---

After a lot of thought over the weekend, I decided to rewrite Fetch2Me in
Java. Not that Python is bad. Python is brilliant. However, i felt that my
code quality in Java (from where i come) is not yet production standard. Over
the past year, i had the opportunity to open up a lot of open source projects
and realised that my code quality is horrible. HORRIBLE !!!

So, this is the plan i came up with.  Bring together our old NIIT gang and -

1)    Rewrite Fetch2Me in Java using HttpUnit and Java Mail API

2)    Expose the core functionality of Fetch2Me as a REST service

3)    Write a front end for web access to the REST service. Typically we
should be writing a Inbox like web page for checking gmail (or any mail for
that case), sending mails (with and without attachments). This front end will
be written using GWT and Guice.

4)    Write a Firefox plugin similar to the requirement in (3)

5)    SMS service should also be exposed as REST service.

Use Maven for build purposes and Git for source control.  Optionally use
Hudson for continuous integration and come up with an Eclipse plugin. Write
lots and lots of of JUnit test cases.  My gut feeling is that this should take
at least a few months development time.

I am sure there are a million products out there which does the same thing but
there are two important highlights in this effort.

1)  We get to learn a lot of new things, open up the source code of lot of
other open source projects, started reading PHP, ASP.net, C#, Ruby, Python
(and convert them to Java) -- all those which we wouldnt have done in our day
job. I thought we could learn by mistakes - both development and design, we
could refactor the code as much as we want at any point of time in the project
(we understand that optimizing early is a crime).

and

2)  Soon after we are done with increments in the project, we'll open source
it. People can just pick our code and host it in their domain and call it a
day. I am sure many will find interest in our work and hopefully start using
it.

