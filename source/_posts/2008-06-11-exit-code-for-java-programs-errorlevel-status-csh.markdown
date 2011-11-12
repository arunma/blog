---
author: Arun Manivannan
date: '2008-06-11 08:04:52'
layout: post
comments: true
slug: exit-code-for-java-programs-errorlevel-status-csh
status: publish
title: Exit code for Java programs -- ERRORLEVEL, $?, $status
wordpress_id: '292'
? ''
: - exit code
  - java
  - java
  - Unix
  - Unix
---

Running a java program from your shell script is commonplace for Batch
operations.  And the wrapper shell script doesnt know about the
success/failure of the wrapped Java program unless we return an exit code.

In most cases, we have the Java source on hand. For others who use a different
mechanism to achieve the functionality of the batch operation, I am not sure
how far this will be useful to you.

**The only possible mechanism (at least that's what i know) is to give out
your exit code using the System.exit (int) method call.  **I would suggest you
to keep off status codes 0-255 because that is already reserved in Unix
platforms (Solaris inclusive).

For the **DOS**, you use the **ERRORLEVEL** to catch your exit status.

echo %ERRORLEVEL% should give you a number indicating the exit code of your
last executed program.

**For bash and ksh, it is $?  as in "echo $?"**

**For cshell, it is $status as in "echo $status" which returns.  I dont see $?
working on cshell (at least on my Solaris box).**

When you are calling a Java program from inside a Java program (using
Runtime.exec()), the code will look something like this (more elegant, of
course) :

Assume the following program is the one which is called

`public class WaitAndTerminate { public static void main(String[] args) {
System.out.println("Program begin"); System.exit(1000);
System.out.println("Program exit"); } } `

and this is your caller program

 ` public class Caller { public static void main(String[] args) {
BufferedReader inStream=null; try { System.out.println("Caller start");
Process process=Runtime.getRuntime().exec("java WaitAndTerminate"); inStream =
new BufferedReader(new InputStreamReader( process.getInputStream() )); //the
waitFor waits for the called program to exit process.waitFor();
System.out.println(process.exitValue()); } catch (IOException e) {
e.printStackTrace(); } catch (InterruptedException ie){ ie.printStackTrace();
} } } `

The getInputStream() method of the Process, as you can see, grabs the output
of the called program so that it could be logged.

**One other main utility of this mechanism is that we can get to know whether
the Java program succeeds completely or not.  In which case, make the last
line of your main program return a System.exit(1000) (which indicates that the
program is terminated successfully). Any termination in the middle (assuming a
system restart or assuming that the called program is a webservice client
making a call to a service hosted on a application server which is restarting
- My God) will not return a status code of 1000. Ideally, it would return 2 or
something like that.**

Lets code that into Java now with a bit of modification into our previously
written code.

` public class WaitAndTerminate { public static void main(String[] args) {
System.out.println("Program begin"); Object object=new Object(); synchronized
(object){ try { object.wait(); } catch (InterruptedException e) {
e.printStackTrace(); } } System.exit(1000); System.out.println("Program
exit"); } } `

The Caller Program is this :  The destroy() method forcefully terminates the
application, giving out a status code of 1. ` public class Caller { public
static void main(String[] args) { BufferedReader inStream=null; try {
System.out.println("Caller start"); Process
process=Runtime.getRuntime().exec("java WaitAndTerminate"); inStream = new
BufferedReader(new InputStreamReader( process.getInputStream() ));
System.out.println(inStream.readLine()); //forceful termination of the called
program process.destroy(); process.waitFor();
System.out.println(process.exitValue()); } catch (IOException e) {
e.printStackTrace(); } catch (InterruptedException ie){ ie.printStackTrace();
} } } ` **Output :** Caller start Program begin 1

