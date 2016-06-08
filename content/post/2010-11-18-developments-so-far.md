---
author: fritzvd
categories:
- minor-thesis
date: 2010-11-18T15:53:56Z
guid: http://fritzvd.wordpress.com/?p=187
id: 187
jabber_published:
- 1290088442
tags:
- 3dengine
- 3dgis
- ar
- aster
- augmentedreality
- gdal
- mayavi2
- python
- remotesensing
- unity3d
- vtk
title: Developments so far
url: /2010/11/18/developments-so-far/
---

Ok. 3 weeks down the road of my minor thesis and what do I have to show for? Well, a lot of paradigms and concepts for starters. Furthermore I have never been able to finish a document like research proposal so quickly and of such quality.

But enough of that. I have more or less abandoned the idea of a mobile application for now. Because having a mobile application like Junaio scores high on the cool list, it doesn&#8217;t really in the sphere of performance and handling large data sets. The preference might go to having a standalone or online application that uses a webcam to model the information on screen.

Most interesting technologies so far:

  1. The awesome [Unity 3D](http://unity3d.com) game engine. Apparently possible to combine with [SSTT](http://technotecture.com/content/sstt-visualizer-augmented-reality-demo) &#8211; AR tool
  2. The extensive Python libraries of [VTK](http://www.vtk.org/) and [Mayavi2](http://code.enthought.com/projects/mayavi/) (installing in Ubuntu costs only 10 min.) in combination with [GDAL](http://www.gdal.org/)
  3. [(Open)](http://sourceforge.net/projects/opengamaray/files/)[Gamaray](http://www.gamaray.com/) &#8211; An AR toolkit similar to UnifeyeSDK (Junaio) by Metaio. Possibility to add location and 3d objects. Very cool.

Another harsh realization is that I have grown too fond of Ubuntu Linux and only now have to deal with an issue that other programmers have been dealing with for ages. Building from source. My goodness. In Mac this feels too dangerous as a mismanaged system can have a lot of missing dependencies and building takes quite a while. In Windows this absolute hell. Searching around for pre-compiled binaries is the way to go, as are packages like Pythonxy. But still, this sucks.

What I have been able to do so far (except for spending days writing and compiling) is importing an Aster Satellite image into the Mayavi2 viewer. Which was remarkably painless and cool. The only thing is that I do not really understand yet what it is showing me. I guess the pixel values of one band have become the Z-axis. Still, cool as Sir Dangles.

<div id="attachment_192" style="width: 410px" class="wp-caption alignnone">
  <a href="http://fritzvd.files.wordpress.com/2010/11/aster1.png"><img src="http://fritzvd.files.wordpress.com/2010/11/aster1.png" alt="Aster Image" title="aster1" width="400" height="290" class="size-full wp-image-192" srcset="http://blog.technokrat.nl/wp-content/uploads/2010/11/aster1-300x217.png 300w, http://blog.technokrat.nl/wp-content/uploads/2010/11/aster1.png 400w" sizes="(max-width: 400px) 100vw, 400px" /></a>
  
  <p class="wp-caption-text">
    View from the middle
  </p>
</div>


  


<div id="attachment_193" style="width: 410px" class="wp-caption alignnone">
  <a href="http://fritzvd.files.wordpress.com/2010/11/aster2.png"><img src="http://fritzvd.files.wordpress.com/2010/11/aster2.png" alt="Aster Image" title="aster2" width="400" height="290" class="size-full wp-image-193" srcset="http://blog.technokrat.nl/wp-content/uploads/2010/11/aster2-300x217.png 300w, http://blog.technokrat.nl/wp-content/uploads/2010/11/aster2.png 400w" sizes="(max-width: 400px) 100vw, 400px" /></a>
  
  <p class="wp-caption-text">
    View from above
  </p>
</div>

Also importing height maps in Unity3D should be not be too painfull, but this proved a bit harder than anticipated.