---
author: Arun Manivannan
date: '2007-08-23 17:35:19'
layout: post
comments: true
slug: javautilregexpatternsyntaxexception-dangling-meta-character-near-index-0
status: publish
title: 'java.util.regex.PatternSyntaxException: Dangling meta character ‘*’ near index
  0'
wordpress_id: '277'
? ''
: - java
  - 'java.util.regex.PatternSyntaxException: Dangling meta c'
  - Uncategorized
---

The same error comes when the regex is "+"

**Here is the solution.**

Enclose your * and + within square brackets.

Here is my code.

**`public static final String [] wildCards={"[*]","%","@","&","[+]"};`**

**`public static void main(String[] args) { String s="!@#$%^&*()";
s=stripWild(s, wildCards); System.out.println(s); }`**

