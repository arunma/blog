---
author: Arun Manivannan
date: '2007-07-13 12:26:44'
layout: post
comments: true
slug: merrill-lynch-interview-questions
status: publish
title: Merrill Lynch interview questions
wordpress_id: '236'
? ''
: - interview questions
  - java interview questions
  - JMS
  - merrill
  - merrill lynch
  - MQ
  - Uncategorized
---

I am not sure how my previous post got deleted.  Let me tell you something
before you go through the questions.  I had three tests and three tech rounds
(actually speaking).  Most of the questions were just questions from my
answers.  So, basically you drive the interview. Trust me, the interviewers
are damn good in what they are doing.  Frankly, I never have faced anything
like this before.  They asked a lot many questions but these are all i could
recollect.  If not for Merrill Lynch, these questions will surely be helpful
for you for some other company.

1) Table level and row level lock

2) How to force a row level lock in a select query (for update clause)

3) Explicit locking in oracle (NO)

4) Deadlock

5) Shared and Exclusive Lock

6) Difference between wait and sleep (the timout seconds as arguments)

7) static synchronized methods possible? YES

8) What do they mean? What does static synchronized methods lock? (locks
java.lang.Class)

9) Is it possible for two threads to get into a same class if one of the
methods is static synchronized and the other just synchronized?

10) Configure webservices (Axis) in weblogic

11) What is a multipool

12) Difference between Topic and Queue. How to identify packet loss in a Topic
publishing?

13) XSLT, XSR? ( I have never heard of XSR)

14) DTD and XSD difference.

15) Why is there just one datatype called CDATA in DTD?

16) Difference between Complex and Simple datatype in XSD

17) How to validate an XML?

18) How to disable XML Validation in runtime when the XSD specified in the
processing instruction (residing in a different machine) is not available

19) DOM and SAX difference.

20) Apache POI API (just because I had this on my resume)

21) >>> An Abstract class is an interface?

>>> An interface is an abstract class?

22) What is Rowid? Can we update the column?

23) What is TRANSACTION_SERIALIZABLE?

24) How to make an IO operation thread safe (use wait/notify model or use Java
NIO)

25) Rules of Serialization

26) How to set security manager in a remote machine

27) What is a sandbox?

28) How to copy serialized contents from one object to another? (Use
reflection??)

29) What is a JMS Exception?

30) How to create transaction ? (User Transaction or use EJBs)

31) Methods in javax.jta.UserTransaction

32) How to rollback a transaction in an EJB ? context.setRollbackOnly()

33) When does EJB automatically rollback transactions (When a SystemException
is thrown)

34) What is twophase commit?

35) In a distributed transaction what is the requirement from the JDBC Driver
Class (should be XA)

36) Is XA possible in all databases?

**37) Are you contributing to Apache?

**38) What projects in Apache have you used?

39) Business Delegate resides on the server-side? (One machine holding the
web-tier and the another machine holding EJB-tier. Where will you place the
BD?)

40) Role of a Service locator apart from lookups ? (Cache Home objects)

41) In a stateless session bean, there is no difference among Remote Objects.
Why cant we cache the Remote Objects too? (????!!!)

42) Pattern of Home Objects in EJB (Proxy)

43) Difference between TIBCO and MQ based messaging model ? (Who knows)

44) What is stack overflow ? (Too many methods in a stack. Often comes in a
uncontrolled recursive function)

45) How to increase the stack memory (I don’t know)

46) Increase the heap memory (Xmx and Xms)

47) Can we have a nested transaction? (Not in J2ee)

48) How to have a count of EJB users for a stateless session bean at any time
(Remember ejbCreate gets called only once. After creation of the bean, the
bean goes to the pool. EjbCreate doesn’t get called the second time)

49) How to link MDBs with Queue?

50) What is the need to have a QueueManager?

51) What gets returned ? (20)

public int m1(){

try{

return 10;

}

catch (Exception e){

}

finally{

return 20;

}

}

52) Why use Ajax?

