---
author: Arun Manivannan
date: '2007-05-11 01:29:57'
layout: post
comments: true
slug: junk-values-during-excel-exportimage-display
status: publish
title: Junk values during Excel export/Image display
wordpress_id: '223'
? ''
: - database
  - export
  - image display
  - jsp
  - junk values
  - POI excel
  - Uncategorized
---

I happen to face this problem a year back.  I was expected to show an image on
a JSP which is stored as a BLOB in the database.  (I also wrote another post a
few days back with uploading and showing image from a MySQL database (with
Hibernate)).  The problem I faced a year back was that i was displaying junk
values on the page instead of the image though the MIME type was set as
**"image/jpeg"** and  the **output stream flushed**.

The same kind of problem my friend faced last week when he was trying to
extract information from the database and export it as excel sheet.  He used
Apache POI for constructing the workbook, set the MIME type as
**"application/vnd.ms-excel"** and flushed the output stream. But what got
exported was just junk values.

The reason was that only the ServletOutputStream was flushed out. Not the
response. As you already know that in Servlets, the response does not get
flushed automatically (unlike JSPs). So, here comes the need for
**response.flushBuffer();**

Here is the core code.

******

response.reset();


response.setContentType("application/vnd.ms-excel");response.addHeader
("Content-Disposition","filename=TableList.xls");


ServletOutputStream stream=response.getOutputStream();

wb.write(stream);


//flush output stream


stream.flush();


//please dont forget to flush the response


response.flushBuffer();


//need to close the stream now. .



stream.close();

I developed a small sample application. Please dont mind the architecture or
performance of the code. [**Download the entire source code.**][1]

Please note that I have not defined any welcome-files. Point your browser to
export.jsp. (PS :Application works only against Oracle databases)

**

   [1]: http://www.arunma.com/files/ExcelWeb.zip (Excel Web application)

