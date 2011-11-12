---
author: Arun Manivannan
date: '2007-03-26 01:07:36'
layout: post
comments: true
slug: save-image-as-without-right-click-using-javascript
status: publish
title: “Save Image As” without Right Click using Javascript
wordpress_id: '193'
? ''
: - javascript
  - without mouse
  - without right click
---

**<script> function saveImageAs (imgOrURL) { if (typeof imgOrURL == 'object')
imgOrURL = imgOrURL.src; window.win = open (imgOrURL);
setTimeout('win.document.execCommand("SaveAs")', 500); } </script>**

**<A href="#" ONCLICK="saveImageAs(document.getElementById('embedImage'));
return false" >save image</A>**

**<img id="embedImage" src="impossible.jpg" >** I am not the author of this
code and i am really not sure where i picked up this script. But it works too
good... only on IE

