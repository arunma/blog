---
author: Arun Manivannan
date: '2007-03-28 02:06:56'
layout: post
slug: apache-commons-lang-find-number-of-string-occurences
status: publish
title: Apache Commons Lang - Find number of String occurences
wordpress_id: '198'
? ''
: - commons lang
  - java
  - string count
  - string occurences
  - Uncategorized
---

The [Apache Commons Lang][1] page says " The _Lang_ Component provides a host
of helper utilities for the java.lang API, notably String manipulation
methods, basic numerical methods, object reflection, creation and
serialization, and System properties. Additionally it contains an inheritable
enum type, an exception structure that supports multiple types of nested-
Exceptions, basic enhancements to java.util.Date and a series of utlities
dedicated to help with building methods, such as hashCode, toString and
equals."

I have been using the commons library for quite sometime. But everything are
in bits and pieces. So, just thought i could learn something more.  But before
that download the[ commons lang libraries][2].

Counting the number of occurences of a String in a particular file or String
requires lots of code. Here is one simple solution.

**import org.apache.commons.lang.StringUtils;**

**public class StringMatch {**

**public static void main(String[] args) {**

**String inputString="hello arun, say hello to all coz" + " it's going to save
you from a hell a lot of trouble";**

**int occurences=StringUtils.countMatches(inputString, "hell");
System.out.println(occurences); //gives you 3 }**

**}**

If you are reading from a file, then go for

** import java.io.FileNotFoundException; import java.io.FileReader; import
java.io.IOException; import java.io.LineNumberReader;**

**import org.apache.commons.lang.StringUtils;**

**public class StringFromFile {**

**public static void main(String[] args) { try { FileReader fileReader=new
FileReader("InputFile"); LineNumberReader lineReader=new
LineNumberReader(fileReader); int count=0; while (lineReader.ready()){
count=count+StringUtils.countMatches(lineReader.readLine(), "hell"); }
System.out.println("Number of occurences is : "+count); } catch
(FileNotFoundException e) { e.printStackTrace(); } catch (IOException e) {
e.printStackTrace(); }**

**}**

**} **

Download the [entire source code ][3]

   [1]: http://jakarta.apache.org/commons/lang/

   [2]: http://apache.mirrors.tds.net/jakarta/commons/lang/binaries/commons-
lang-2.3.zip

   [3]: http://www.arunma.com/files/code/commons/commonslangstring.zip

