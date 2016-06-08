---
author: fritzvd
categories:
- GIS
date: 2012-11-28T12:34:30Z
excerpt: A walkthrough to get ECW library working with GDAL in Linux (ubuntu/debianesque
  distro's). This took me a while to unravel, so before I forget or before other people
  run into the same issues, let's make a note of this.
guid: http://blog.technokrat.nl/?p=398
id: 398
tags:
- gdal ecw libecw
- libecwj gdal-ecw-build gdal-ecw
title: Making sure GDAL works with ECW libecw under linux
url: /2012/11/28/making-sure-gdal-works-with-ecw-libecw-under-linux/
---

This took me a while to unravel, so before I forget or before other people run into the same issues, let&#8217;s make a note of this.

Assuming you are using a debian-like linux distribution (ubuntu, debian, linux mint, etc. anything using: `apt-get` to install packages) there are a few things to note.
  
First of all make sure you have the latest packages for: mapserver, gdal, etc.
  
([ubuntu-gis repository](https://launchpad.net/~ubuntugis "ubuntu-gis") has newer versions than the standard repositories).

The ecw library version 3.3 was free to use with a few exceptions. Read write access is ensured, write access up to files of 500MB. The first requirement is to build this library. Go to: [this place](http://meuk.technokrat.nl/libecwj2-3.3-2006-09-06.zip) to download `libecwj2-3.3.20060906.zip`. Untar and build the library.
  
In the terminal assuming you are using Downloads folder:
  


Last command should output two lines of formats: ECW and JP2ECW