---
author: fritzvd
categories:
- minor-thesis
date: 2010-11-30T17:40:15Z
guid: http://fritzvd.wordpress.com/?p=198
id: 198
jabber_published:
- 1291131616
title: Rendered Useless
url: /2010/11/30/rendered-useless/
---

A little update on what I am doing. Today is a pictureless day, too bad.

Moving away from Mayavi2 I have been moving towards ActionScript and Flash. Why this switch? Well Mayavi2 is a real cool scientific visualization tool, but most of the focus is on on-the-fly visualization of data that is dense, but also a computer that is powerful. This does not really serve useful for the purposes I would want to move towards. Another major drawback is that I haven&#8217;t been able to find a way to export the visualization I have made in Mayavi2 to another format than a static PNG.

Finding out that the FLARToolkit almost does all the things I am moving towards I swallowed my pride and installed the Flex SDK. This is a first time for me to do scripting in ActionScript, but I must say it has been most rewarding and a lot more useful and powerful than I have always judged Flash to be, always shying away from it, because I hate website that use Flash to do things that CSS and HTML can easily perform.
  
Diving into ActionScript and Flash 3D engines has been educational, I&#8217;ve been able to rotate [cows](http://papervision2.com/loading-complex-models-v2/), which was fun, as well as a few other things. The FLARManager allows you to use 3D engines such as PaperVision3D, Sandy, Away3D and some others that don&#8217;t surface for now.

So that was good. But then the other aspect. Trying to get a GIS file to 3D. You&#8217;ve got to be shittin&#8217; me why should this be so hard.

Trying to get a GIS file (even raster images) into a 3D format seems to prove more difficult than anticipated. It is not so much that I do not know how to visualize or how I would like it to be, but I keep running into these stupid data type issues. I am almost frustrated up to the point of trying out a red brick vs. LCD screen collision.

**ArcScene**
  
ArcScene exports 3D to VRML (.wrl) format, which is almost completely useless (unless someone is able to persuade me otherwise, I will stick to this view). ArcScene is however by far the easiest way to go from a flat surface to a nice 3D visualization. This bothers me to some extent, because of my primal urge for open-source software to be better.

**Step-by-Step**
  
So what I am going to try now is to export the raster image I have to a PNG file and to load that in Blender. Blender can export to X3D (the successor of VRML) but not import from it (another point of frustration). Trying out all of these different import/export tools almost made me parse the VRML myself and spit out a COLLADA file. Maybe this is still the best way to go. So if I do I will post the script here.

For the time being I am going to load the greyscale into PNG to create a height map in that using the same technique as the last post featured, and export that to COLLADA or another suitable format for pv3d or something. Let you know how it goes (hopefully with nice pictures).

P.S. check out this awesome portfolio: [mrdoob.com](http://mrdoob.com)