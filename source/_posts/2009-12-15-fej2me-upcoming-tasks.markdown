---
author: Arun Manivannan
date: '2009-12-15 17:19:19'
layout: post
comments: true
slug: fej2me-upcoming-tasks
status: publish
title: Fej2Me - Upcoming tasks
wordpress_id: '362'
? ''
: - fetch2me
  - java
  - lunarcodes
  - Uncategorized
---

This weekend, i managed to migrate a few core portions of Fetch2Me from Python
to Java. It was an amazing experience and a wonderful feeling to be bilingual.
Though the Java version looks more elegant (to me), i personally loved my
Python. The "the first project in Python" feeling...

So, here are the upcoming tasks in the Java version :

**1) SMS Service : **SMS service is not a part of the the system right now.
Implement SMS service into fej2me through Google Voice account

**2) Encryption : ** The config.xml used in the project has plaintext "mail id
and password".  I was thinking on the lines of AES having an external private
key stored in a non-project folder without which the password hash would not
make any sense.

**3) Use JavaMail instead of Commons Email :** I happen to use Apache Commons
email instead of for sending mails (SMTP) because it looked simple. But later
i realised that we cant attach streams. What i am currently doing is that i am
attaching an URL directly to the email like

`emailAttachment.setURL(new URL(http://www.google.com));`

which is good for our current needs but will limit our options. Plain JavaMail
on the other hand will use a DataSource which will give us a lot of options.

**4) Apache HttpClient : **As of now, the URL is directly attached to the
email. What if the target URL is down or isnt even an URL. We would want to
use HttpClient to ping the URL and check whether the status code returned is
200.

**5) Search functionality using Google AJAX search and JSON :** Google search
or Wiki search (idea by Rajesh) is not a part of the system right now. Need to
use Google Ajax API and JSON to pull data from Google. Please refer to
http://code.google.com/apis/ajaxsearch/documentation/

You might get some additional ideas on Book search, Movie search from the
following URL (Idea by Dinesh)

http://code.google.com/apis/ajax/playground/#hello_world

**6) Interactive browsing using Apache HttpUtils (functionality similar to
Mechanize/Beautiful soup) :** Use HttpUtils/HttpClient to simulate user
browsing with Java. This will open a whole world of accessing authenticated
systems.

**7) Recurring updates using Quartz scheduler : ** Everybody would like to
have recurring updates from sites, say like cricinfo or nseindia. users should
be able to set a recurring job with us and get updates. something like..
"between 1 pm and 8 pm, get updates from
http://www.cricinfo.com/nzvpak2009/engine/current/match/423780.html" every 1
minute". we should enable persisted scheduling using a backend database (which
is also available with quartz)

**8) Multithreaded processing :** Currently, the processing and handling of
requests is sequential. We have to think about exploiting ThreadPool API to
process multiple requests.

**9) Quartz scheduler with BigTable/HBase :** This is totally optional, but
somebody is yet to come up with a Quartz scheduler extension using the backend
as HBase. May be... may be... we could think of that. Though, HBase is good
for large data, it is still an idea worth considering. Optionally, if we have
a need to store large data into our systems, we could consider HBase.. Just
for the fun of it.

