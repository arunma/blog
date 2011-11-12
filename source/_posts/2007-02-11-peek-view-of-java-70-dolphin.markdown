---
author: Arun Manivannan
date: '2007-02-11 01:03:33'
layout: post
comments: true
slug: peek-view-of-java-70-dolphin
status: publish
title: Peek view of Java 7.0 (Dolphin)
wordpress_id: '75'
? ''
: - java
  - Uncategorized
---

Here are some interesting features of Java 7.0

**Using array syntax for collections access.**

For example, instead of writing this:


    List content = new ArrayList(10);

    content.add(0, "Bean");

    content.add(1, "Picks");

    String name = content.get(0);

you will be writing..


    List content = new ArrayList(10);

    content[0] = "Bean";

    content[1] = "Picks";

    String name = content[0];

You can also initialize your List as


    ArrayList content = {"Bean", "Picks", "Techno", "Blog"}

Most of the time we write so much code for accessing the getters and setters
of beans. Consider you have a bean called Point, we generally write..


    Point p = new Point();

    p.setX(56);

    p.setY(87);

    int z = p.getX();

Now, with Dolphin, you could write


    Point p = new Point();

    p->X = 56;

    p->Y = 87;

    int z = p->X;

and your Point class will now look like this :


    public class Point {

      public int property x;

      public int property y;

    }

Cool. Isn't it?

Visit : [www.ibm.com][1] for more info

   [1]: http://www-128.ibm.com/developerworks/java/library/j-java2007.html?ca
=dgr-btw01JavaFuture (Java 7.0)

