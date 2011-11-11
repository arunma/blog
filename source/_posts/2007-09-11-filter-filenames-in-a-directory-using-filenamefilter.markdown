---
author: Arun Manivannan
date: '2007-09-11 10:02:00'
layout: post
slug: filter-filenames-in-a-directory-using-filenamefilter
status: publish
title: Filter filenames in a directory using FilenameFilter
wordpress_id: '278'
? ''
: - filenamefilter
  - filenames
  - filter
  - java
  - Uncategorized
---

Old code but thought this would be useful

`package com.ml;`

`import java.io.File;` `import java.io.FilenameFilter;`

`public class FileFilterTest {`

`public static void main(String[] args) {`

`FilenameFilter filter=new FilenameFilter(){` `public boolean accept(File dir,
String fileName) {` `return fileName.endsWith("java");` `}` `};`

`File f=new File("D:/Programs/Code");` `String [] fileList=f.list(filter);`
`for (int i=0;i<fileList.length;i++){` `System.out.println(fileList[i]);` `}`
`}`

`}`

