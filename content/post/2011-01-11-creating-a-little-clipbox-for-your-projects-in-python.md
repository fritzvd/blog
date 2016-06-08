---
author: fritzvd
categories:
- GIS
date: 2011-01-11T15:48:32Z
guid: http://blog.technokrat.nl/?p=369
id: 369
tags:
- clip
- gdal
- gis
- ogr
- python
title: Creating a little clipbox for your GIS projects in Python
url: /2011/01/11/creating-a-little-clipbox-for-your-projects-in-python/
---

When working on a GIS project, this always bums me out. You need to have a certain area in which you want to cut all your source data. But in ArcGIS I never figure out how to do it properly, except for using Python scripts and arcgisscripting/arcpy. But I figured, this should also be do-able from the terminal, and take less time and energy from your little workbox.

But here&#8217;s a Python script that uses open-source libraries and writes

Be sure to have  [FW_Tools](http://fwtools.maptools.org/) installed (win/linux) or when you&#8217;re on a Mac head over to [KyngChaos](www.kyngchaos.com/). This dude has some binary versions of GDAL and PROJ. On Ubuntu life is even more dreamy:

`sudo apt-get install proj4 python-gdal`

and some other stuff I can&#8217;t think of right now.

This is the version of the script that will run with FWTools in Windows. (all neatly stolen and copied from [Chris Garrard](http://www.gis.usu.edu/~chrisg/python/2009/))

<pre><code class="syntax python">import ogr, os, sys, osr
os.chdir('C:/Directory')

driver = ogr.GetDriverByName('ESRI Shapefile')

fn = 'tmp.shp'
if os.path.exists(fn):
	driver.DeleteDataSource(fn)
ds = driver.CreateDataSource(fn)

if ds is None:
	print 'Could not create file'
	sys.exit(1)
layer = ds.CreateLayer('layer_1', geom_type=ogr.wkbPolygon)

fieldDefn = ogr.FieldDefn('name', ogr.OFTString)
fieldDefn.SetWidth(30)
layer.CreateField(fieldDefn)

featureDefn = layer.GetLayerDefn()

ring = ogr.Geometry(ogr.wkbLinearRing)
ring.AddPoint(54280, 419385)
ring.AddPoint(95285, 419385)
ring.AddPoint(95285, 460390)
ring.AddPoint(54280, 460390)

poly = ogr.Geometry(ogr.wkbPolygon)
poly.AddGeometry(ring)

feature = ogr.Feature(featureDefn)
feature.SetGeometry(poly)

layer.CreateFeature(feature)

ring.Destroy()
poly.Destroy()
feature.Destroy()

ds.Destroy()

inSpatialRef = osr.SpatialReference()
inSpatialRef.ImportFromEPSG(4269)
outSpatialRef = osr.SpatialReference()
# changing from unprojected to 'RijksDriehoeksstelsel' the Dutch National Grid
outSpatialRef.ImportFromEPSG(28992)
coordTrans = osr.CoordinateTransformation(inSpatialRef, outSpatialRef)

inDS = driver.Open('tmp.shp', 0)
if inDS is None:
  print 'Could not open file'
  sys.exit(1)
inLayer = inDS.GetLayer()

# create a new data source and layer
fn = 'clip.shp'
if os.path.exists(fn):
  driver.DeleteDataSource(fn)
outDS = driver.CreateDataSource(fn)
if outDS is None:
  print 'Could not create file'
  sys.exit(1)
outLayer = outDS.CreateLayer('layer_2', geom_type=ogr.wkbPolygon)

featureDefn = outLayer.GetLayerDefn()

# loop through the input features
inFeature = inLayer.GetNextFeature()
while inFeature:

  # get the input geometry
  geom = inFeature.GetGeometryRef()

  # reproject the geometry
  geom.Transform(coordTrans)

  # create a new feature
  outFeature = ogr.Feature(featureDefn)

  # set the geometry and attribute
  outFeature.SetGeometry(geom)
  outFeature.SetField('name', inFeature.GetField('name'))

  # add the feature to the shapefile
  outLayer.CreateFeature(outFeature)

  # destroy the features and get the next input feature
  outFeature.Destroy
  inFeature.Destroy
  inFeature = inLayer.GetNextFeature()

# close the shapefiles
inDS.Destroy()
outDS.Destroy()</code></pre>