---
author: Arun Manivannan
date: '2007-02-15 01:01:42'
layout: post
comments: true
slug: jruby-on-rails-your-jvm-is-shared
status: publish
title: JRuby on Rails. Your JVM is shared !!!
wordpress_id: '82'
? ''
: - java
  - jruby
  - rails
  - Uncategorized
---

As you already know that from Java 6.0, JVM wont be running Java alone. Its
going to run a lot of scripting languages too. **Rhino, the Mozilla
implementation of Javascript is the one that is officially announced.** There
are already too many tutorials in the web on how to run Javascript in Java
6.0.

Mid last year, there was so much hype about **[Ruby on Rails][1] **and that it
is going to shun Java to oblivion very soon. The ease of development with Ruby
on Rails made that trick. But then experts opined that Ruby will hold its own
niche just like PHP and wouldnt be replacing Java in the enterprise market,
now that Java has become more a standard than a technology.

Following the Ruby hype, **JRuby** came into existence. Ruby interpreter,
which was originally written in C, was written completely in Java and guess
what, Ruby will now run on your JVM. Please visit the **[JRuby homepage][2]
**for more details.

JRuby ... Ruby on Rails... Thats right.** JRuby on Rails.** A new Java web
application framework comes into existence. Just like any upcoming web
frameworks, there is less of configuration and more of tier based stack ups.

So, two years down the line you will be working with a programmer who writes a
completely different language and will ask you to speed up your JDBC code. You
have to buddy. He calls your code and shares your JVM.

   [1]: http://www.rubyonrails.org/

   [2]: http://jruby.codehaus.org/

