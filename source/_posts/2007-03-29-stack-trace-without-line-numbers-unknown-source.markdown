---
author: Arun Manivannan
date: '2007-03-29 09:45:25'
layout: post
comments: true
slug: stack-trace-without-line-numbers-unknown-source
status: publish
title: Stack trace without line numbers — Unknown Source
wordpress_id: '201'
? ''
: - java
  - line numbers
  - stack trace
  - unknown source
---

Sometimes, application servers don't display the line numbers during printing
the trace but instead just print the method name with the "(Unknown Source)"
on it.

eg. something like this.

**Exception in thread "main" java.lang.ArithmeticException at
TraceWithoutLineNumbers.main**_**(Unknown Source)**_

I wrote this small class to just help me learn why the line numbers get missed
and Unknown Source comes up when the trace gets printed.

public class TraceWithoutLineNumbers {

public static void main(String[] args) {

System.out.println("hello world");

if (true){ throw new ArithmeticException(); } System.out.println("very true");

}

}

For the above code, I gave a

**javac TraceWithoutLineNumbers.java**

and got

**java TraceWithoutLineNumbers hello world Exception in thread "main"
java.lang.ArithmeticException at
TraceWithoutLineNumbers.main(TraceWithoutLineNumbers.java:9)**

Cool. Got the line number.

By default, the minimal debugging option is on. (Only line number and source
file information is generated). Here is the list of all the [other java
compiler options.][1]

So, I do a

**javac -g:none TraceWithoutLineNumbers.java **

**java TraceWithoutLineNumbers hello world Exception in thread "main"
java.lang.ArithmeticException at TraceWithoutLineNumbers.main(Unknown
Sourc**e)

There is nothing you could do on this if the class is built and run by the
server ( read if you dont have control over the class' compilation). However,
if it is a standalone class, you can very well do a **javac -g** .

Or use this option.

**-g:**_{keyword list}_

    Generate only some kinds of debugging information, specified by a comma
separated list of keywords. Valid keywords are:

**source**

     Source file debugging information

**lines**

     Line number debugging information

**vars**

     Local variable debugging information

Probably, the app server or the web server you are running your class on would
have disabled the debugging option for performance purposes.

   [1]:
http://java.sun.com/j2se/1.5.0/docs/tooldocs/windows/javac.html#options

