---
author: Arun Manivannan
date: '2007-02-03 13:01:38'
layout: post
slug: classloading-who-carries-my-class
status: publish
title: Classloading — who carries my class???
wordpress_id: '29'
? ''
: - java
  - Uncategorized
---

Class loading is always an interesting discussion for any Java developer. Here
are a few quintessential concepts.

We know that every class that we write and work on runs on the JVM. And we
know that before doing the actual functionality that the class is written for
(ie running on the JVM for the functionality), it gets loaded. As you already
know that class is loaded only once. ie. one per TYPE and not one per object.
So, if you have 20 thousand String objects in your heap, you just have one
java.lang.String TYPE per classloader. And this TYPE is represented as
java.lang.Class.You have a java.lang.Class representation for every single
thing that exists in java. For objects you can get access to this type using
the getClass() method (available in the java.lang.Object). For primitives you
have a special variable called "class" in it. (eg. int.class)

JVM loads these classes using various ClassLoaders. You can just see how many
classes are loaded before your actual class is run by just giving a java
-verbose .

There are basically three class loaders that are needed before even your
actual class gets started.

Bootstrap loader which loads the core Java classes (starts from
java.lang.Object, if you look a the java -verbose)

Extension class loader loads all the jar files that are present in your
jre/lib/ext folder

System class loader which loads all the jars and classes you specify in the
CLASSPATH variable in your machine

and finally, your own custom application class loader.

The best example for a custom class loading that could be quoted is the J2EE
servers. They have their own class loaders for dynamically loading classes
into itself. And thats the reason why changes that we make in the code is
reflected without even restarting the server (for hot deployments).

[![class hierarchy][1]][2]

© [ibm.com][3]

As you could see from the picture, the class loaders are hierarchical. Meaning
that before your custom class loader loads a class, it consults with the
system class loader which in turn calls its parent till it reaches the
Bootstrap loader. For the first time, when a class is loaded, the ClassLoader
would read all the bytes and deploy it into the JVM. Second time, when the
same TYPE comes up, it uses the cached version, so that it need not traverse
through the hierarchy again.

Again, the same class could never be deployed by two classloaders in the same
hierarchy. Classes that are loaded in the topmost hierarchy prevails if there
is a duplication.

But the same class could be loaded in two different hierarchies. WHAT???

[![identity crisis][4]][5] © [ibm.com][6]

The picture clearly shows that two classes and interfaces are loaded in
different hierarchies.

Lets consider a situation where class Class1 loaded by ClassLoader1 tries to
access Class2 loaded by ClassLoader2. And that's the job of the
ClassNotFoundException.

   [1]:
http://beanpicks.wordpress.com/files/2007/02/clhierarchygif.thumbnail.png

   [2]: http://beanpicks.wordpress.com/files/2007/02/clhierarchygif.png (class
hierarchy)

   [3]: http://www-128.ibm.com/developerworks/java/library/j-dclp1/

   [4]: http://beanpicks.wordpress.com/files/2007/02/identity-
crisisgif.thumbnail.png

   [5]: http://beanpicks.wordpress.com/files/2007/02/identity-crisisgif.png
(identity crisis)

   [6]: http://www-128.ibm.com/developerworks/java/library/j-dyn0429/

