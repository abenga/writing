
Here we will try to show our visitors a map showing the administrative 
boundaries of the 47 counties of Kenya.

To show this, we obviously need some representation of where the boundaries 
between the counties lie. Geographic data is often stored in the form of 
[shapefiles](https://en.wikipedia.org/wiki/Shapefile), a vector format used for 
geographic information system (GIS) software. Fun(?) fact: A shapefile is not 
really a *file*, but a collection of files in a directory that together define 
the geographic data. The shapefile format describes vector features: points, 
lines, and polygons, representing, for example, water wells, rivers, and lakes 
in a geographical region respectively. Each item usually has attributes that 
describe it, such as name.

The data we will use is a shapefile obtained from 
[this page](http://www.arcgis.com/home/item.html?id=5f83ca29e5b849b8b05bc0b281ae27bc) 
in the ArcGIS website. We download a compressed file called `County.zip` which 
contains the collection of files that define the shapefile.

We need to convert this file to GeoJSON. To do this we will use the `ogr2ogr` 
command, a part of the [GDAL](http://www.gdal.org/), the geospatial data 
abstraction library (on Ubuntu, it is installed by installing the `gdal-bin` 
package).

If we extract all the files in the zip file to a directory (called `Kenya`, 
say), we will have the following directory tree:

    Kenya/
    ├── County.dbf
    ├── County.prj
    ├── County.sbn
    ├── County.sbx
    ├── County.shp
    ├── County.shp.xml
    └── County.shx

We then run the command 

    ogr2ogr -f GeoJSON -t_srs crs:84 kenya.geojson County.shp

in the `Kenya` directory. It will create a `kenya.geojson` file, which contains 
the information contained in the shapefile. This is the file we need.

## Reducing File Size









## References

* Shapefile from ArcGIS Website [Online] Available from:
  [shapefile&nbsp;<i class="fa external-link"></i>](http://www.arcgis.com/home/item.html?id=5f83ca29e5b849b8b05bc0b281ae27bc) 
  [Accessed 27&nbsp;June&nbsp;2015] 
  *(thanks to the user dmuthami for this excellent piece of work)*
