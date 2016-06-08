---
author: fritzvd
categories:
- minor-thesis
date: 2010-11-22T12:51:17Z
guid: http://fritzvd.wordpress.com/?p=190
id: 190
jabber_published:
- 1290423079
tags:
- 3dgis
- blender
- dem
- enthought
- gdal
- gis
- mayavi
- mayavi2
- python
title: Processing images with GDAL and Mayavi2
url: /2010/11/22/processing-images-with-gdal-and-mayavi2/
---

Ok, this took a while but the results are not bad. So I guess it&#8217;s worth it.

First of all, a big thank you at [Ok, this took a while but the results are not bad. So I guess it&#8217;s worth it.

First of all, a big thank you at](http://www.gis.usu.edu/~chrisg/) who is very possibly unaware of the fact that I have been using his classes on Python and Open Source GIS. They give a good introduction into using GDAL with NumPy.

So after struggling a few consecutive days (frustration peaked!), I managed to load a Digital Elevation Model into the Mayavi 3D visualization tool. It&#8217;s still a bit rough and the peaks are a bit pointy, thus buildings look a bit weird, but still it&#8217;s another little step.

I first tried a [Blender Tutorial](http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/Making_Landscapes_with_heightmaps) that helped me out making this image:

<div id="attachment_199" style="width: 456px" class="wp-caption alignnone">
  <a href="http://fritzvd.files.wordpress.com/2010/11/blenderdem.png"><img src="http://fritzvd.files.wordpress.com/2010/11/blenderdem.png" alt="Blender and Digital Elevation Model" title="blenderdem" width="446" height="269" class="size-full wp-image-199" /></a>
  
  <p class="wp-caption-text">
    Blender output
  </p>
</div>

Then after that I figured that is a bit much work for something that in my opinion can be done more efficiently. The steps are still a bit stupid, because I exported a PNG of the DEM visualized with grayscale and then imported that into gdal and displayed that. So it&#8217;s still a bit dumb. And it isn&#8217;t really representative of the data types that a DEM contain. But the DEM itself only gave very weird visualizations, possibly because of the detail of the file as well as large negative values for NoData values.

Anyway it is a start:

<div id="attachment_202" style="width: 510px" class="wp-caption alignnone">
  <a href="http://fritzvd.files.wordpress.com/2010/11/mayavi-dem1.png"><img src="http://fritzvd.files.wordpress.com/2010/11/mayavi-dem1.png" alt="Import with PNG and Mayavi2" title="mayavi-dem" width="500" height="247" class="size-full wp-image-202" srcset="http://blog.technokrat.nl/wp-content/uploads/2010/11/mayavi-dem1-300x148.png 300w, http://blog.technokrat.nl/wp-content/uploads/2010/11/mayavi-dem1.png 1002w" sizes="(max-width: 500px) 100vw, 500px" /></a>
  
  <p class="wp-caption-text">
    Mayavi2 Output
  </p>
</div>