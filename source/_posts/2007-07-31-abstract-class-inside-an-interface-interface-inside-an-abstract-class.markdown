---
author: Arun Manivannan
date: '2007-07-31 00:30:36'
layout: post
comments: true
slug: abstract-class-inside-an-interface-interface-inside-an-abstract-class
status: publish
title: Abstract Class inside an Interface??? Interface inside an Abstract class???
wordpress_id: '238'
? ''
: - inner class
  - inner interface
  - interface
  - Uncategorized
---

Interface inside an abstract class is static.

` package com.nu;`

`public abstract class ClassInterface {`

`public interface Intrface{`

`public void m1();`

`}`

`}` And so is an Abstract class inside an interface

`package com.nu;`

`public interface IntrfaceClass {`

`public abstract class AbstrClass{` ` public void m1(){` `
System.out.println("from m1");`

`}`

`}`

`}` Usage :

`package com.nu;`

`public class ImplClass extends IntrfaceClass.AbstrClass implements
ClassInterface.Intrface{`

`public static void main(String[] args) {`

`}`

`}`

