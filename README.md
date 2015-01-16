# foss4g-workshop
Workshop for foss4g neebies

Natical maps of scotland

http://maps.nls.uk/geo/explore/#zoom=15&lat=55.85697&lon=-4.26107&layers=74401014

##zyGrib 
Download wind data for scotland

## QGIS
Open Natural Earth data
Filter admin = Austria or region = Scotland

### rename filtered data
at - sl

### label features
name

### save as .. esri shape file

### clip evaluation points
Vector - geoprocessing - clip

name  ||  '('  || elevation  || ')'


## Download SRTM Data
<a href="http://dds.cr.usgs.gov/srtm/version2_1/SRTM3/Eurasia/">HGT data</a>

## GRASS
HGT - r.slope
HGT - r.contour.level (100)
HGT - r.contour.step (100)

##POSTGIS
select ST_Box2D(the_geom) from ne_10m_admin_0_countries where iso_a2 = 'AT';
                                 st_box2d                                 
--------------------------------------------------------------------------
 BOX(9.52115482500017 46.3786430870001,17.1483378500001 49.0097744750001)
(1 row)

Calculate the Range of Austria



Calculate the area of Austia
<code>select ST_AREA(the_geom::geography)/1000000 from ne_10m_admin_0_countries where iso_a2 = 'AT';</code>
 ?column?     
------------------
 83993.1389909428
(1 row)

## Download osm data (i.e. from geofabrik)

## Copy great britian osm data to database
osm2pgsql -U user -W -H localhost -C 1300 -s -d uk great-britain-latest.osm.pbf

## Extract data from scotland
osmosis --read-pbf great-britain-latest.osm.pbf --bounding-box top=60 left=-10 bottom=55 right=0 --write-pbf scotland.osm.pbf

## Create Database SL
create database sl
create extension postgis

## Copy scotland osm data to database
osm2pgsql -U user -W -H localhost -C 1300 -s -d sl scotland.osm.pbf


## Style (OSM-Bright)

<p>OSM Style verwenden
<a href="https://github.com/mapbox/osm-bright">OSM-Bright</a>.</p>

## Carto 
<code>npm install -g carto</code>

<code>carto project.mml > mapnik.xml</code>

## Render OSM tiles on the fly 

### Service
<p>Start a tilelite webservice<br>
<code>
/usr/local/bin/liteserv.py -c --cache-path=/home/gcu/cache mapnik.xml
</code>
</p>

### Display in the Browser (Leaflet) 
<code>var map = L.map('map').setView([55, -5], 5);</code> 

<code>L.tileLayer('http://localhost:8000/{z}/{x}/{y}.png',{}).addTo(map);</code>
