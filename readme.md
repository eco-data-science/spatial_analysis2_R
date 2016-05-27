### R Spatial Analysis Workshop: Vectors (Polygons and Shapefiles)

Spatial R workshop focusing on reading and using shapefiles and polygon layers directly in R.  Examples based on Ocean Health Index - British Columbia.  Requires a range of spatial packages: `sp`, `rgdal`, `rgeos`, `maptools`, `raster`, and the usual suspects: `dplyr`, `tidyr`, `stringr`; optional packages: `cleangeo`, `gdalUtils`,  `ggplot2`, `RColorBrewer`

View the HTML (knitted from the .Rmd): https://rawgit.com/eco-data-science/spatial_analysis2_R/master/spatial_analysis2.html

Download the PDF (knitted from the .Rmd): https://github.com/eco-data-science/spatial_analysis2_R/blob/master/spatial_analysis2.pdf

View the R Markdown document: https://github.com/eco-data-science/spatial_analysis2_R/blob/master/spatial_notes.Rmd

This tutorial/workshop assumes that you have existing vector spatial data that you want to analyze.  You can create polygons and such directly in R, but we will save that for another time...

# Setup for workshop

1. __Get the workshop materials:__ Go to the repository and click on the "fork" button to create an independent copy within your own GitHub account.  Alternately, click on the "clone or download" button. https://github.com/eco-data-science/spatial_analysis2_R.
2. __Install the necessary packages:__
```
### Eco-data-science faves! If you don't already have these, get them, they will make your life easier.
  install.packages('dplyr'); install.packages('tidyr'); install.packages('stringr'); install.packages('readr')

### We will do some visualization of maps toward the end with `ggplot2` and `tmap` packages.
  install.packages('ggplot2')
  install.packages('tmap')
  install.packages('RColorBrewer') ### to go along with ggplot - getting better color selection into your plots

### Spatial packages: If you did Jamie's raster workshop, you probably have most of these already, but can't hurt to update.
  install.packages('sp')       ### spatial classes and basic spatial functionality
  install.packages('rgdal')    ### GDAL functionality in R
  install.packages('rgeos')    ### vector spatial analysis tools
  install.packages('raster')   ### raster stuff, but some handy tools that work great for vector spatial data as well
  install.packages('maptools') ### an alternate package with good spatial analysis tools

### Optional: These are for some of the extensions to the workshop - not necessary, but install them if you want to try them out
  install.packages('gdalUtils')    ### this one adds some good GIS-like geospatial processing functionality
  install.packages('cleangeo')     ### this one has functions for checking and cleaning faulty vector spatial data
```

__Note:__ If you get an error trying to install the `rgdal` or `rgeos` packages, you may need to install some libraries outside of R.  For the rgdal package (and some of the others) to work properly, you need GDAL (Geospatial Data Abstraction Library) and Proj.4 (projection management) libraries already installed on your laptop.  For the rgeos package, you need the GEOS (Geometry Engine Open Source) library installed.

* For Mac, go here, and the top link ("GDAL 1.11 Complete") will download an installer that gets you everything you need (incl. GEOS and Proj.4), easy peasy:
    * http://www.kyngchaos.com/software:frameworks
* For Windows and Linux, there are some links to installers on this page:
    * https://trac.osgeo.org/gdal/wiki/DownloadingGdalBinaries
* For Windows and Linux, I'm not sure whether those installers also include the GEOS and Proj.4 libraries, so you may also need to separately install those.  If so, check these pages:
    * Proj.4: https://github.com/OSGeo/proj.4/wiki
    * GEOS: https://trac.osgeo.org/geos/

If you don't already have these on your laptop, install them, then go back and do the install.packages('rgdal'), install.packages('rgeos'), etc at your R command line afterward, just to make sure the R packages can access the info from these external libraries.

I'll also show a super-fast demo with QGIS, a free GIS application that works on Mac and does most of the stuff that ArcGIS does.  [Here's more info on QGIS](http://www.qgis.org/en/site/)  We will not spend any time on it in the workshop though.
