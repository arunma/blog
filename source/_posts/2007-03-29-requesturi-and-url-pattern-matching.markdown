---
author: Arun Manivannan
date: '2007-03-29 00:13:14'
layout: post
comments: true
slug: requesturi-and-url-pattern-matching
status: publish
title: RequestURI URL Pattern Matching
wordpress_id: '199'
? ''
: - java
  - requesturi
  - url pattern matching
---

Back when i was preparing for the Web Component Developer exam, i had an idea
of the requestURI and pattern mapping against the exact servlet. In simple
words, the logic behind how the server maps the "<url-pattern>" tag and the
<servlet-class> tag. I know that it is really a monstrous job, but then i
wanted to try it using a simple array. Of course the code i wrote is buggy ( I
myself found one big bug in there.) But for most cases, it works fine.

Here is my code. [Download from here][1]. public class Navigation {

static String[] config= { "/test2", "TestServlet2", "/test", "TestServlet" };
static String requestUri= "/test2/";

public static void main(String[] args) {

System.out.println("output" +new Navigation().getHandler(config, requestUri));
}

public String getHandler(String[] config, String requestUri) {
System.out.println("Request uri : "+requestUri); int maxMatch=0; //store the
length of the match that is the longest. String currentMatch=null; //the most
accurate match string

for (int i=0;i<config.length;i=i+2){ //looping through the array. // Coz, you
know that every odd String in the array is the Handler String, //you can just
skip them

System.out.println("config[i] :"+config[i]);

if ((requestUri.startsWith(config[i]))){ if (config[i].length()>maxMatch){
//compare the length of the //previously matched String, if any
maxMatch=config[i].length(); //if so, store it System.out.println("max
match... "+config[i+1]); currentMatch=config[i+1]; //Dont forget the String
too }

}

}

if (currentMatch!=null){ return currentMatch; //return it. }

return "/"; }

}

   [1]: http://www.arunma.com/files/code/burnthykeyboard/Navigation.java

