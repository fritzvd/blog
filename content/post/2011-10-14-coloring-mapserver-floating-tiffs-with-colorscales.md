---
author: fritzvd
categories:
- GIS
date: 2011-10-14T07:25:27Z
guid: http://blog.technokrat.nl/?p=395
id: 395
tags:
- gis
- map
- mapserver
- open source
- sld
- style
- webmapping
title: Coloring Mapserver Floating Tiffs with Colorscales
url: /2011/10/14/coloring-mapserver-floating-tiffs-with-colorscales/
---

This has been a little mystery for me waiting to be uncovered. However I solved it. Depending if you are using a SLD (styled layer descriptor) or the embedded Style commands this is what your Mapfile could look like:

<pre><code class="syntax apache">MAP
NAME "Some Map"
DEBUG ON
FONTSET "/home/fritz/maps/fonts.txt"

WEB
  IMAGEPATH "/tmp/"
  IMAGEURL "/tmp/"
  METADATA
    "wms_title"     "WMS Demo Server"  ##required
    "wms_onlineresource" "http://localhost/cgi-bin/mapserv?map=map.map"   ##required
    "wms_srs"       "EPSG:42304 EPSG:42101 EPSG:4269 EPSG:4326 EPSG:7030 EPSG:32736"  ##recommended
  END
END

PROJECTION
  "init=epsg:32736"   ##required
END

#
# Start of layer definitions
#
LAYER
NAME 'test'
METADATA
    "wms_title"   'test'
END
TYPE RASTER
STATUS ON
DATA  '/home/fritz/maps/colorscale_test.tif'
PROJECTION
  "init=epsg:32736"   ##required
END
CLASS
  NAME "test"
  STYLE
    COLORRANGE 255 255 0 140 160 160
    DATARANGE 0.02 0.6
    RANGEITEM "[pixel]"
  END
END
PROCESSING "SCALE=0.2, 0.6"
END
</code></pre>

The Scale and Datarange command look very similar and I haven&#8217;t figured out quite how to set it properly, or how to have three-color scale. However it&#8217;s a start. And I haven&#8217;t found it documented anywhere else, here you go.