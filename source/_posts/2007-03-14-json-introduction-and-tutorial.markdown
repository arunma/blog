---
author: Arun Manivannan
date: '2007-03-14 01:10:25'
layout: post
comments: true
slug: json-introduction-and-tutorial
status: publish
title: JSON Introduction and Tutorial
wordpress_id: '161'
? ''
: - json
  - json tutorial
  - Uncategorized
---

Now that AJAX is more of JSON than XML, there arises an imminent need to learn
JSON. Interchange of XML between serverside and clientside is heavy. XML is
still a String but it needs to be parsed to give some meaning to the client.
Javascript Object Notation (JSON), on the other hand is lightweight than the
XML and we speak the language of Javascript. Which means no parsing.

This is JSON


    {"addressbook": {"name": "Mary Lebow",

        "address": {

            "street": "5 Main Street"

            "city": "San Diego, CA",

            "zip": 91912,

        },

        "phoneNumbers": [

            "619 332-3452",

            "664 223-4667"

        ]

     }

    }

and this is its XML equavalent


    <addressbook>

     <name>Mary Lebow</name>

     <address>

        <street>5 Main Street</street>

        <city zip="91912"> San Diego, CA </city>

        <phoneNumbers>

          <phone>619 332-3452</phone>

          <phone>664 223-4667</phone>

        </phoneNumbers>

     </address>


    </addressbook>

And


     jsonContent.addressbook[i].name

will return "Mary Lebow". How does that look?

However, the structure of JSON looks a bit odd. And you are just suspicious
about creating JSON in your servlets. Construction of JSON is already made
simple with the Java classes available at http://json.org. Google "simple
json" and you have another damn simple JSON implementation.

[>> Learn more about JSON and XML ][1]

   [1]:
http://weblogs.java.net/blog/arungupta/archive/2007/03/languageneutral.html

