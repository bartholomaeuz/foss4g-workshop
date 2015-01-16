# foss4g-workshop
Workshop for foss4g neebies

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
