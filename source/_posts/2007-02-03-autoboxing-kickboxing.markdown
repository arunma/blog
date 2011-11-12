---
author: Arun Manivannan
date: '2007-02-03 18:33:55'
layout: post
comments: true
slug: autoboxing-kickboxing
status: publish
title: Autoboxing Kickboxing ;-)
wordpress_id: '38'
? ''
: - java
  - Uncategorized
---

###  [ ][1]

Sorry for not posting last week. Had a tight work schedule.

Here is an interesting feature of auto-boxing, which you know, was introduced
with Java 5.0 where you could directly assign a primitive to a Wrapper (eg.
int value to a Integer wrapper.)

Meaning....something like

Integer a = 10;

Here goes the interesting part of this feature.

Integer a = 10, b = 10 ; Integer c = 128, d = 128 ;

System.out.println( a == 10 ) ; System.out.println( a == b ) ;
System.out.println( c == 128 ) ; System.out.println( c == d ) ;  This is the
output for the above snippet

true true true false

Strange Isnt it? 'a' and 'b' holds the same value. And they are the same.
Good. But "c" and "d" also holds the same value but they arent equal !!!

Sun has something as an interesting explanation for this...

"If an int or short number between -128 and 127, let r1 and r2 be the results
of any two boxing conversions. It is always the case that r1 == r2."

It seems that -128 through 127 are cached. God knows why they did this.

Solution :

Use intValue() during unboxed comparisons. The following code would return
true.

System.out.println( c.intValue() == d.intValue() ) ;

source: [http://java.sun.com][2]

   [1]: http://beanpicks.blogspot.com/2007/01/autoboxing-kickboxing.html

   [2]:
http://java.sun.com/docs/books/jls/third_edition/html/conversions.html#5.1.7

