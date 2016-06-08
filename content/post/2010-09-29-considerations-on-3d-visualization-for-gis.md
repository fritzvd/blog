---
author: fritzvd
categories:
- minor-thesis
date: 2010-09-29T14:54:21Z
guid: http://fritzvd.wordpress.com/?p=139
id: 139
jabber_published:
- 1285764869
tags:
- 3dgis
- cryengine
- gameengine
- gis
- minorthesis
- python-gis
title: Usability and 3D in Geovisualization
url: /2010/09/29/considerations-on-3d-visualization-for-gis/
---

For my minor thesis I am thinking of a project for processing Environmental Impact Assessment in a way that is more easily comprehensible. For this project I intend to use Augmented Reality. Hopefully some form of 3d visualization. And I am looking at the possibilities of using gaming engines.

First and foremost, this is a preliminary research. I am not in any way an expert. And only just learning about the amazing possibilities.

Over the last few days I have been looking at different scholarly and not so scholarly papers in search of some good information on the use of game engines in 3d visualizations of GIS. The search has been quite fruitful but not conclusive. Aren&#8217;t these searches always.

Anyway. This is more or less a note to self. To remind myself what I&#8217;ve found and where. But if you&#8217;re interested please follow this blog to see the outcome of this project.

Visualization using Game Engines is something that has over the last decade caught the attention and imagination of more people than just me. Not surprisingly because the gaming industry is leading the field in wonderful visualizations and magnificent displays of Artificial Worlds and the interaction of the user with it.

**1. Fritsch and Kada &#8211; Visualization Using Game Engines**
  
Dieter Fritsch and Martind Kada of the Institute for Photogrammetry in Germany has written an introductory overview on different game engines and their applicability and capabilities for visualization in 3d. His conclusion clearly states the possibilities but also the complications. These mainly consist of data format. Common GIS data patterns are very different to most 3d data types. Polygons and points are usually a bit more complex more on this in number 3. A project called GISMO apparently is quite capable of rendering large data sets and are quite user friendly.

**2. Herwig and Paar &#8211; Game Engines: Tools for Landscape Visualization and Planning?**
  
Interesting conclusions and research on the increased involvement of stakeholders and planners. Not necessarily a very technical paper. But good for reference.

**3. Scianna and Ammoscato &#8211; 3D GIS Data Model Using Open Source Software (2010)**
  
An interesting article on using the Python bindings of Blender to process GIS data. They start of by stating why they chose to use Blender for the research and not other open source 3d software. There is quite a difference in data types as already mentioned between usual 3d rendering and design software and GIS data types. Unlike GIS types points and lines do not form the primitives of 3d software.
  
Blender and the GIS RDBMS PostGIS are then linked through a Python script. And data is sent back and forth. Python scripts are available online: [Link does not seem to work](www.dirap.unipa.it/python_scripts)

**4. Slocum et al. &#8211; Cognitive and Usability Issues in Geovisualization**
  
This is a more academic work on cognitions and user friendliness. Different methods of working with Geovisualization are proposed. Good for reference and Usability things.

**5. MacEachran (editor) &#8211; Exploring Geovisualization**
  
Huge collection of articles on Geovisualization. From Usability and Cognition, to Data Handling and 3D interfaces. Chapter 28 was quite useful on Usability.

Of course much more literature has been leafed through, but these are some of the articles or books that I found worth mentioning in the introduction of my proposal. Next time some more literature overviews and then hopefully some conclusions.