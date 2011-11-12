---
author: Arun Manivannan
date: '2007-02-03 10:33:22'
layout: post
comments: true
slug: war-of-the-worlds-ripples-from-openjdk
status: publish
title: War of the worlds — Ripples from OpenJDK
wordpress_id: '6'
? ''
: - ibm
  - java
  - openjdk
  - sun
  - Uncategorized
---

Part 1

As we all know, Sun, after two years of meditation, broke its silence last
November crowning itself as the torchbearer for the open source initiatives.
It announced that Java SE, ME and the Glassfish projects (Glassfish is the
open source effort for an JEE 5 compatible application server - incubated and
developed in the [java.net][1] community) is open sourced under the GPL v2
(GNU's General Public License).

This has brought huge applause from the open source communities, more
especially, from the linux circles which, till recently, were upset with the
Sun's distribution of Java through the CDDL (Common Development and
Distribution License). CDDL states that Java could not be bundled with the
Linux distros. Redhat, Suse and a few other distros, however, bundled JRockit
(Bea's proprietory JVM), whose license allowed redistribution.

What does the GPL say? Modify the open code howmuchever you want. Keep it
private in your own system. But if you want to redistribute, share your
modification to everybody else. Meaning, redistribute under GPL again. (Nice.
isn't it). And GPL is also known as the Grand Daddy of the Open Source
licenses with about 70-80% of the open source projects under it.

Why did Sun release Java under GPL? It had its own reasons. And Microsoft was
one big reason when they created a buggy JVM based on JDK 1.1. They called it
the MSJVM (Microsoft Java Virtual machine) with Microsoft extensions which
made applets run faster on windows machines, and eventually forgetting the
"Write Once Run Anywhere" concept of Java. Sun sued and won $ 20 million.
Microsoft is never to use 'Java' or any of its trademarks for its newly cooked
up JVM. What do you think "Microsoft VM" that is installed in our Internet
Explorer is?

Naturally, Sun was afraid that there will surely be forks for Java
implementation and which might be incompatible with each other. GPL promised
prevention of forks to some extent.

Part 2

IBM, which was the leading "pressurizer" that wanted Sun to open source java,
is now upset over the announcement. Last year, there were open letters and
hues and cries by IBM all over the open source community asking Java to be
open sourced. In fact IBM made an open challenge to Sun that IBM would open
source its proprietory JVM if Sun open sourced its version. Then why is IBM
upset over this announcement. Reason.. Lot many reasons -- all with business
intend.

1) Apache Harmony, as you understand, is an Apache project started around May
last year. What are they doing? They are writing open source Java SE. An
equavalent (lets not say competitor) to Sun's Java implementation. Recent
visit says that 1.25 million lines of code is already contributed to it. IBM
is one of the lead players here other than Intel. IBM joined this project soon
after its start just to show itself as a serious open-source player and to
bring down Sun's reputation among the already disgruntled OS community.

2) The GPL v2 licensing for OpenJDK. IBM wants Sun to contribute to Apache
Harmony or at least bring OpenJDK under Apache License. Whats so special in
Apache license? -- it allows use of the distribution of the source code in
both open source and "closed source" (proprietory) software. Meaning IBM can
go ahead and wrap the OpenJDK and market it. The same way it produced
Websphere Community Edition wrapping Apache Geronimo, Websphere commercial
version wrapping Apache Web server and its Rational products wrapping Eclipse.

While IBM was saying that Opensourcing Solaris as OpenSolaris was not a big
deal for Sun (Solaris is well known as the most secure Unix based operating
systems), and that Sun's interest in the community could only be seen when it
outsources Java, questions came up with the OS community that if open-sourcing
Solaris, a home grown product of Sun, was not a big deal, what is stopping IBM
open source its AIX which uses a lot of open source code in it. In fact, IBM
has been advertising that AIX is a superior Unix. Why not share it with the
Linux community?

Sure there exists a cold war situation between the giants. And IBM is on the
losing side.

IBM opens Windows of suspicion.

   [1]: http://java.net/

