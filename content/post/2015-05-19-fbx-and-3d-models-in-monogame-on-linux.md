---
author: fritzvd
categories:
- development
- game
date: 2015-05-19T15:35:39Z
guid: http://blog.technokrat.nl/?p=600
id: 600
tags:
- 3dengine
- c#
- fbx
- monogame
- xna
- xnb
title: FBX and 3d models in Monogame &#8211; on Linux
url: /2015/05/19/fbx-and-3d-models-in-monogame-on-linux/
---

> TL;DR the monogame community is pretty great

Lately my manic ambitious mode has turned on again for me. So I have about 100s of ideas again, which sadly of course will all come to nothing. But while I&#8217;m at it, I thought I&#8217;d make the best of it to do some tutorials here and there and learn some stuff I know nothing about.

Starting with Monogame on Linux is kind of a hassle to start with, but if you push through it works. At the time of writing this I got Monogame 3.4 to work: <a href="http://www.monogame.net/downloads/" target="_blank">Monogame Downloads Page</a>. If you&#8217;re not very comfortable with 

The real problem was that a tutorial I tried to follow had an old style FBX file that the Monogame Content Pipeline was not willing to load. Everyone told me to use <a href="http://www.blender.org/download/" target="_blank">Blender</a> to convert it. But.. Blender wasn&#8217;t loading my file, because it was ASCII based. So I had to find a converter. I found the Autodesk one for Linux somewhere in the attic of the internet. I&#8217;ll host it <a href="http://meuk.technokrat.nl/fbx_converter" target="_blank">here</a> so I know for sure it won&#8217;t go missing. So install that thing, and convert it (if necessary import and export in Blender too, just to make sure). Your Content Pipeline will thank you.

P.S. you can find some great free models here: <a href="http://tf3dm.com/" target="_blank">http://tf3dm.com/</a>. <a href="http://tf3dm.com/3d-model/puo-67895.html" target="_blank">The featured image is a model made by 3dgenerator: http://tf3dm.com/3d-model/puo-67895.html</a>