---
author: Arun Manivannan
date: '2007-05-18 02:16:48'
layout: post
comments: true
slug: hold-variables-across-page-refreshes-in-javascript-the-infamous-close-all-functionality
status: publish
title: Hold variables across page refreshes in Javascript — The infamous “Close All”
  functionality
wordpress_id: '225'
? ''
: - javascript
  - Uncategorized
---

[![Expandable sample][1]][2]

Say, you have an expandable menu (like the one in picture but the expansion is
not Javascript driven) on the parent window and the parent window refreshes on
every click of the node of the menu (the (+) and (-) kind of menus). You also
have a "Close All" button on the parent window which is supposed to close all
the child windows.

Ideally, you want to hold the names (or handles) of the child windows in order
to close all the child windows when the "Close all" button is pressed. But
since the parent window gets refreshed on menu node expansion, the Javascript
array of child handles that i have disappears.

Bottom line, Javascript variables get reinitialized on page refreshes. But
there is a workaround for this.

You can simply assign the array to a special variable called
**navigator.storedvariable**

Something like, **navigator.storedvariable=windowNames; // **windowNames is
the array of names of the child windows.

This is the exact code i wrote for implementing the Closeall functionality

`function closeChildWindows(){``//retrieve all the names of childwindows var
childWindows = navigator.storedvariable; if ( childWindows != null ){`

//loop through each of the window for (var k=0;k<childWindows.length;k++){ var
openedWindowName = childWindows[k];

//Open all the child windows since we have already lost handles and then close
again. The browser will open the child window in the same previous (stale)
browser child window

winHandle = window.open('',openedWindowName,'toolbar=0,location=0,width=2,heig
ht=2,scrollbars=no,resizable=no,directories=0,status=0,menubar=0');winHandle.b
lur(); //as soon as you open, close them. So that the user doesnt realise that
the same browser was used again

if( winHandle && winHandle.open && !winHandle.closed) { winHandle.close(); }
}//end of for loop

} // end of childwindows!= null //after closing all windows, reinitialize
navigator.storedvariable windowNames=new Array();
navigator.storedvariable=windowNames; }

   [1]: http://www.arunma.com/wp-
content/uploads/2007/05/expandablemenu.thumbnail.JPG

   [2]: http://www.arunma.com/wp-content/uploads/2007/05/expandablemenu.JPG
(Expandable sample)

