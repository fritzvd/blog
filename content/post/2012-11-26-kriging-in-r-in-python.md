---
author: fritzvd
categories:
- GIS
- python
date: 2012-11-26T13:48:56Z
excerpt: Kriging is a geostatistical method to be able translate point data to a grid,
  to find out where you can predict stuff really well and where the variance is really
  high. As always GIGO (garbage in garbage out). But it is at least a large improvement
  from interpolation techniques such as Inversed Distance Weighting (IDW) which is
  often implemented in GIS software.
guid: http://blog.technokrat.nl/?p=409
id: 409
tags:
- rpy2 rpy r python kriging gstat
title: Kriging in R in Python
url: /2012/11/26/kriging-in-r-in-python/
---

This might be a repost of some sort. However I found that it was kind of hard to find anything about this specific topic. So here it goes.

Kriging is a geostatistical method to be able translate point data to a grid, to find out where you can predict stuff really well and where the variance is really high. As always GIGO (garbage in garbage out). But it is at least a large improvement from interpolation techniques such as Inversed Distance Weighting (IDW) which is often implemented in GIS software.

However for Kriging you need a bit more information. You need to input a variogram. This is however often estimated with &#8216;expert&#8217; knowledge and looking at graphs produced by the input data. In my mind this sounds like automatable. But I haven&#8217;t got around to it. 

The best implementations exist for R, but for those who don&#8217;t like R for any reason (slow, not really productionable etc.) there is a Python implementation by Ambhas [right here](http://www.ambhas.com/tools/html/krige_8py_source.html "kriging in python").

For those who don&#8217;t care. You can use r in python with rpy2 (or rpy). This is a bit ugly. But it is at least a lot nicer (imho) to work with (data i/o) using gdal etc) in production. Also anything beyond Ordinary Kriging becomes complex. And I did not find anyone yet publishing their code for non-ordinary kriging (cokriging, colocated cokriging and other more complicated algorithms). If anyone comes around to writing it, please open source that shiznit.

Anyways. If you want to do colocated cokriging you have to have 2 forms of data for every point. The code will look like this:

<pre><code class="syntax python">def cokriging_in_r(self, x, y, z):
        '''
        Cokriging (and ordinary kriging) is quite fast in R.
        This would anyway be more pragmatic than rewriting/porting it to Python.
        For the moment this will be the 'best' way as R makes it very easy to
        use kriging without fitting a variogram model, but using a standard 
        variogram.
        '''
        import rpy2
        import rpy2.robjects as robj
        import time
        time0 = time.time()
        robj.r.library('gstat')
        self.create_interpolation_grid()
        xi, yi = robj.FloatVector(self.xi.tolist()), robj.FloatVector(self.yi.tolist())
        dataset = self.dataloader.dataset.ReadAsArray().flatten()
        mask = numpy.equal(dataset, -9999)
        rxi = robj.FloatVector(dataset.tolist())
        secondary = self.get_secondary_for_locations()
        secondary = robj.FloatVector(secondary)
        x,y,z = robj.FloatVector(x), robj.FloatVector(y), robj.FloatVector(z)
        primary_frame = robj.DataFrame({'x': x, 'y': y, 'z':z})
        secondary_frame = robj.DataFrame({'x': xi, 'y': yi, 'secondary': rxi})
        target_frame = robj.DataFrame({'x':xi, 'y':yi})
        vgm_args = {'model_type': 'Sph', 'range1': 20000, 'range2':1040000}
        # following command gives a python output to r functions
        vgm_args['nugget'] = 0.035
        vgm_args['sill1'] = 0.473
        vgm_args['sill2'] = 8.994
        secondary_variance = dataset[~mask].var()
        primary_variance = robj.r.var(z)[0]
        correlation_secondary_primary = numpy.abs(robj.r.cor(z, secondary))
        variance_correction = numpy.sqrt(primary_variance * secondary_variance)
        # The cross coefficient is used in the cross variogram (crossgram)
        # 
        cross_coef = (correlation_secondary_primary * variance_correction)[0]
        # change it back to rpy strict

        # The variogram is combined. This is a bit awkward in Rpy.
        # So one way is change the args manually (see below)
        # or load variables in R before hand.
        variogram_secondary = robj.r.vgm(vgm_args['sill1'] * secondary_variance, 
            vgm_args['model_type'], vgm_args['range1'], vgm_args['nugget'], 
            robj.r("add.to=vgm("+ str(vgm_args['sill2'] * secondary_variance)
                + ", 'Sph', 1040000, " + str(vgm_args['nugget'] * 
                    secondary_variance)+")"))
        variogram_primary = robj.r.vgm(vgm_args['sill1'] * primary_variance,
            vgm_args['model_type'], vgm_args['range1'], vgm_args['nugget'], 
            robj.r("add.to=vgm("+ str(vgm_args['sill2'] * primary_variance)
                + ", 'Sph', 1040000, " + str(vgm_args['nugget'] * 
                    primary_variance)+")"))
        crossgram = robj.r.vgm(vgm_args['sill1'] * cross_coef, 
            vgm_args['model_type'], vgm_args['range1'], vgm_args['nugget'], 
            robj.r("add.to=vgm("+ str(vgm_args['sill2'] * cross_coef)
                + ", 'Sph', 1040000, " + str(vgm_args['nugget'] * cross_coef) + ")"))

        cck = robj.r('NULL')
        cck = robj.r.gstat(cck, "primary", robj.r('z ~ 1'), robj.r('~ x + y'), 
            data=primary_frame, model=variogram_primary, nmax=40)
        cck = robj.r.gstat(cck, "secondary", robj.r('secondary~ 1'), robj.r('~ x + y'),
            data=secondary_frame, model=variogram_secondary, 
            merge=robj.r("c('primary','secondary')"), nmax=1)
        cck = robj.r.gstat(cck, robj.r('c("primary", "secondary")'), model=crossgram, nmax=40) 
        result = robj.r.predict(cck, target_frame)
        # crossval = robj.r('gstat.cv')(cck)
        time1 = time.time()
        deltatime = time1-time0
        print('Kriging took '+ str(deltatime) + ' seconds')
        secondary_est = numpy.array(result[4])
        secondary_est = secondary_est.reshape((self.ny, self.nx))
        primary_est = numpy.array(result[2])
        primary_est = primary_est.reshape((self.ny, self.nx))
        return secondary_est, primary_est
</code></pre>

The `create_interpolation_grid` refers to a function which sets up an empty grid based on the extent of the grid and the size of the pixels:

<pre><code class="syntax python">def create_interpolation_grid(self):
        '''
        Run this to get some basic stuff, like an empty grid to interpolated
        the data to, the extent and size of the tifs.
        '''
        extent = dataset.extent
        self.nx, self.ny = basegrid.size
        xi = numpy.linspace(extent[0], extent[1], self.nx)
        yi = numpy.linspace(extent[2], extent[3], self.ny)
        xi, yi = numpy.meshgrid(xi, yi)
        self.xi, self.yi = xi.flatten(), yi.flatten()
</code></pre>