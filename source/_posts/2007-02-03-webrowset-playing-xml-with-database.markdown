---
author: Arun Manivannan
date: '2007-02-03 18:42:13'
layout: post
slug: webrowset-playing-xml-with-database
status: publish
title: WebRowSet — Playing XML with Database
wordpress_id: '46'
? ''
: - java
  - jdbc
  - webrowset
  - xml
---

We already know that ResultSet gets closed once we close our Statement object.
So, prior Java 5.0 we were just "migrating" the ResultSet values to a
Collection of Value objects.. But, bundled with Java 5.0, the "disconnected"
RowSet came up. Although there is a rowset.jar that could be used with Java
1.4, most people still follow the conventional "migration" process.We know
that there are three kinds of RowSet implementations, the CachedRowSet (one
which stores the data in memory. best suitable for less quantity of data), the
JDBC Rowset (I really havent used it yet. They say ResultSet could be used as
a Java bean.) and my personal favourite, the WebRowSet.

WebRowSet typically fetches your ResultSet in an XML format. You could just
use a plain Javascript DOM parser or an XPath language and just show the data
on your HTML page.

I just wrote this small program so you could feel what i felt.

So, I have my getConnection() method to link my app to the database.

public Connection getConnection() throws ClassNotFoundException, SQLException
{ Class.forName("com.mysql.jdbc.Driver");

Connection con = DriverManager.getConnection(
"jdbc:mysql://localhost:3306/ukc", "root", "orange");

if (!con.isClosed()) System.out.println("Connection created"); return con; }

Then i am just using the connection to fetch some data

public WebRowSet getWebRowSet(Connection conn) throws SQLException { Statement
statement = conn.createStatement(); ResultSet rs =
statement.executeQuery("select * from Products"); WebRowSetImpl webRowSet =
new WebRowSetImpl(); webRowSet.populate(rs);

return webRowSet; }

And finally a main program to link these two methods and write the XML to the
Console

public static void main(String[] args) {

WebRowSetSample rowSetSample = new WebRowSetSample();

try { Connection conn = rowSetSample.getConnection(); WebRowSet rowSet =
rowSetSample.getWebRowSet(conn); //I am writing output to Console. Just pass
an OutputStream to the writeXml method rowSet.writeXml(System.out);

} catch (Exception e) { e.printStackTrace(); }

}

[![tabledata][1]][2]

[![output][3]][4]

   [1]: http://www.arunma.com/wp-
content/uploads/2007/02/tabledata.thumbnail.png

   [2]: http://www.arunma.com/wp-content/uploads/2007/02/tabledata.png
(tabledata)

   [3]: http://beanpicks.wordpress.com/files/2007/02/datarowset.thumbnail.png

   [4]: http://beanpicks.wordpress.com/files/2007/02/datarowset.png (output)

