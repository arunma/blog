---
author: Arun Manivannan
date: '2007-03-27 02:43:00'
layout: post
comments: true
slug: compare-two-objects
status: publish
title: Compare two Objects using Comparator
wordpress_id: '196'
? ''
: - comparator
  - compare objects in arraylist
  - compare objects in vector
  - compare two objects
  - java
  - Uncategorized
---

Old story but will be useful for sure.

Say you have an ArrayList of Beans (eg. ArrayList of Employee objects) that
need to be sorted based on an attribute inside the Bean (eg. EmployeeName)
before displaying to your GUI. You have two options before you..

1) If you are among the lucky lot who gets access to the Data Access Object
(EJB or a class that has queries), just alter your query to return the
ResultSet after sorting. i.e. use an “order by” clause in your query.

2) Or…. Use the **Comparator** interface. (you can use Comparable too. I am
not talking about that in this post)

The implementation is pretty simple..

Here goes the code.

I have three classes with me

1) [UserBean.java][1] (which is just a bean Bean with regular getters and
setters). It has three attributes inside it. userId, userName, address

2) [UserNameComparator.java][2] (which implements the Comparator interface and
obviously overrides the compare method). The compare method just accepts two
objects and returns an int. neednt worry about what to return as “int”. Just
call the compareTo(Object) method inbuilt in String and Wrapper classes. It
will return an int. Just use it.

3) [SortUserBean.java][3] (the caller method). Just builds a dummy ArrayList
of UserBeans, displays the ArrayList before sorting and after sorting.

Download the complete [source code][4]

   [1]: http://www.arunma.com/files/code/compare/UserBean.java

   [2]: http://www.arunma.com/files/code/compare/UserNameComparator.java

   [3]: http://www.arunma.com/files/code/compare/SortUserBean.java

   [4]: http://www.arunma.com/files/code/compare/compare.zip

