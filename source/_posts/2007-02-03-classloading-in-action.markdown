---
author: Arun Manivannan
date: '2007-02-03 13:05:26'
layout: post
comments: true
slug: classloading-in-action
status: publish
title: Classloading in action
wordpress_id: '30'
? ''
: - java
  - Uncategorized
---

Here is a sample code for custom classloaders and the hierarchical
relationship that i wrote for my personal learning. Thought it would be useful
to you.In the example, I have two classes (Class1 and Class2) whose
implementation is this

package com.beanpicks.classes;

public class Class1 {

}

:-) Class2 is also the same.

I am trying to load these two classes with the help of two different
ClassLoaders (FirstClassLoader and SecondClassLoader). Both have the same
implementation. I just created two ClassLoaders just to see how the
hierarchical classloading works.

And finally, i have a Client class which does the actual plumbing job. Here
are its usecases

1) Instantiates the two classloaders 2) Loads Class1 using FirstClassLoader 3)
Loads Class2 using SecondClassLoader 4) Lists all the classes loaded under
both ClassLoaders (using the method listAllClasses(ClassLoader
whatClassLoaderYouNeedToList)) So, the main method looks like this.

//Instantiate the FirstClassLoader FirstClassLoader firstClassLoader = new
FirstClassLoader(classesFolder); //Load Class1 using FirstClassLoader
firstClassLoader.loadClass("com.beanpicks.classes.Class1"); //List all the
list of classes that are loaded in FirstClassLoader
listLoadedClasses(firstClassLoader);

The only complicated thing in the client class is the implementation of the
listAllClasses (i use a lot of reflection in there). Here is the gist of what
i am doing

1) Get the Class TYPE of the ClassLoader using the ClassLoader.getClass(); 2)
Get the special Field called "classes" from the java.lang.ClassLoader class
using the class.getDeclaredField(). ie. i am getting it from the parent of all
custom class loaders. This MASTER Field has all the classes loaded by all its
sub-classloaders.

3) In order to get the classes loaded by FirstClassLoader, we need to pass the
FirstClassLoader into the get method of the Field. 4) the get method returns a
List. Iterate it.

Now, we can just check out the implementation of the FirstClassLoader

I have overridden loadClass and the findClass methods of the classloader. What
i am doing in the loadClass is that i am simply called the findClass method. I
know its the dumbest of the implementation. But then, i need to load the
System classes too. (otherwise the compiler will complain for the missing
java.lang.Object).

So my implementation of the loadClass method is

public Class loadClass(String className) throws ClassNotFoundException{

if (className.startsWith("java.")) { return findSystemClass(className); }
return findClass(className); }

then the findClass method

public Class findClass(String name)throws ClassNotFoundException{

byte[] classBytes = findClassBytes(name); if (classBytes==null){ throw new
ClassNotFoundException(); } else{ return defineClass(name, classBytes, 0,
classBytes.length); } }

As you can see, i am just getting the bytes of the class file the
findClassBytes method. Then calling the defineClass magic method.

finally, the findClassBytes

public byte[] findClassBytes(String className){

try{ String pathName = classesFolder + File.separatorChar +
className.replace('.', File.separatorChar)+ ".class"; FileInputStream inFile =
new FileInputStream(pathName); byte[] classBytes = new
byte[inFile.available()]; inFile.read(classBytes); return classBytes; } catch
(java.io.IOException ioEx){ return null; } }

I am getting the fully qualified name of the class, replace the "." with a "/"
(File.separatorChar) and load the bytes. Done.

Here is the output of the program

********************************************************** ClassLoader :
com.beanpicks.classloaders.FirstClassLoader@130c19b
********************************************************** class
com.beanpicks.classes.Class1 class com.beanpicks.client.Client class
com.beanpicks.classloaders.FirstClassLoader class
com.beanpicks.classloaders.SecondClassLoader

********************************************************** ClassLoader :
com.beanpicks.classloaders.SecondClassLoader@35ce36
********************************************************** class
com.beanpicks.classes.Class2 class com.beanpicks.client.Client class
com.beanpicks.classloaders.FirstClassLoader class
com.beanpicks.classloaders.SecondClassLoader

As you can see, the firstclassloader loads Class1. Its parent, the
ApplicationClassLoader loads the Client, FirstClassLoader and the
SecondClassLoader. The Classes loaded by the ApplicationClassLoader is also
listed because i am looping for the entire classloading hierarchy in the main
method.

while (currentClassLoader != null) {

listAllClasses(currentClassLoader); //switching to a parent classloader
currentClassLoader = currentClassLoader.getParent(); }

As you understand, currentClassLoader will be null when it meets the bootstrap
loader.

