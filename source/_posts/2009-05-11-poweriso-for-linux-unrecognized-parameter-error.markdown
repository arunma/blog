---
author: Arun Manivannan
date: '2009-05-11 16:10:43'
layout: post
comments: true
slug: poweriso-for-linux-unrecognized-parameter-error
status: publish
title: PowerISO for Linux (Unrecognized Parameter error)
wordpress_id: '321'
? ''
: - linux
  - linux
  - poweriso
  - Ubuntu
  - Ubuntu
  - unrecognized parameter
---

Just realised today that PowerISO ([http://www.poweriso.com/download.htm][1])
is available for Linux and its free too.  I have a weird feeling of liberation
nowadays though i have been using Linux for more than two years now.

The manual goes like this

`PowerISO   Copyright(C) 2004-2008 PowerISO Computing, Inc Type poweriso -?
for help`

`Usage:    poweriso <command> [parameters] [-switches]`

`<Commands>`

`list <image file> <directory>    List files and directories in image file.
Example:  List all files and directories in root direcory of
/home/sam/test.iso . Command: ** poweriso list /home/sam/test.iso / -r**`

`extract <image file> <dir/file name>   Extract files/directories from image
file. Example:  Extract all files and directories in root direcory of
/home/sam/test.iso to /home/sam/test recursively.` `Command:  **poweriso
extract /home/sam/test.iso / -od /home/sam/test**`

`convert <image file>    Convert image file to other format. Example:  Convert
/home/sam/test.daa to standard iso file Command:  **poweriso convert
/home/sam/test.daa -o /home/sam/test.iso -ot iso**`

Do take note of the "/" before -od and -r. It throws a weird** "Unrecognized
parameter:"**

   [1]: http://www.poweriso.com/download.htm

