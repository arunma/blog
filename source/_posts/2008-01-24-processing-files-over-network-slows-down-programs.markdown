---
author: Arun Manivannan
date: '2008-01-24 18:24:17'
layout: post
comments: true
slug: processing-files-over-network-slows-down-programs
status: publish
title: Processing files over network slows down programs
wordpress_id: '283'
? ''
: - file
  - network
  - programs
  - Uncategorized
---

I had this strange problem for the past two weeks. A program which takes 14
minutes on my local machine consumes 98 minutes on my production server. The
only reason is this -- the location of my input files. I am comparing 10,000
XML files against another set of 10,000.

When i make this run from my local box, all the 20k files are in my desktop.
But the 20k files are located on a shared drive on a different system for the
production run.

The diff reports (10k individual reports and a Consolidated report) also needs
to be moved to the shared drive. One of my seniors suggested me to copy the
10k files to a temporary folder in the production box, process it, generate
the diff report (10k files) in the temp directory and then copy everything
back to the shared drive. Initially, i thought it was absurd. What difference
would it take between copying over a network and processing directly over the
network. But it really worked great. My current run time in production box is
brought down to 48 minutes (that is half the time).

Another thing i wanted to share is the deletion process of the temporary
files.  As you know, i cant dump my prod box with temporary files.  Looping
through the temp folder and then deleting was my option. But then i had this
method in the **java.io.File -- deleteOnExit();**

** Javadoc **says** **that deleteOnExit requests that the file or directory
denoted by this abstract pathname be deleted when the virtual machine
terminates. So, after creation of the file, i just mark them for deletion on
JVM exit. Works great.

