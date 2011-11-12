---
author: Arun Manivannan
date: '2007-02-15 00:12:34'
layout: post
comments: true
slug: cc-isnt-faster-than-java
status: publish
title: C/C++ isnt faster than Java
wordpress_id: '80'
? ''
: - java
  - Uncategorized
---

Most Java programmers, just like me are always under the misconception that
Java is slower than C/C++ or any of its Object Oriented counterparts. An
interesting article that i read recently really made me proud to work in Java.

After looking at those Swing applications and Applets, anybody would easily
come to a conclusion that Java is sluggish. Taking hours to load. Eclipse is
slower when compared to C driven Desktop applications. Right. Its very very
true that C applications are faster than Java applications in the **desktop
front.** Meaning. C/C++ can **just run small programs a bit faster than
Java.** But research reveals that C/C++ cannot even come closer to Java in the
server-side front. **C/C++ performs very badly in the web-applications and
server based programs, where Java rules.**

Java developers often feel shy when C/C++ developers come and say that we have
another "layer" called JVM above the machine code which converts the bytecode
to machine code and hence our code can NEVER be faster. This WAS true. But it
isnt now. At least after the** Just In Time compiler** came into existence
since Java 1.2. **The Just In Time compiler just "compiles" the code into
machine language. **So, your java code doesnt get interpreted every time it is
run. And not only compilation, it just optimises your code too.

Does the **Hotspot JIT **ring you bells? Thats right. Its the Sun's own JIT
which looks into your code, **finds places which is frequently run, optmizes
the code, compiles it into machine language. **So, the next time you hit the
same area, you get a blistering response. Same is the case with JSP. When you
try hitting the JSP thrice or more times (first hit will always be tedious.
you know why), your JSP class is fully compiled, optimized and "hotspotted".

Refer [http://www.idiom.com/~zilla/Computer/javaCbenchmark.html][1] for
benchmark results

The above results are for Java 1.4. You know that there are so much of
optimizations done in the JVM for JDK 1.5.

So, the next time somebody comes to you and says "C/C++ is faster", just tell
them back, "You are living in a smaller world, buddy".

   [1]: http://www.idiom.com/~zilla/Computer/javaCbenchmark.html

