# foss4g-workshop
Workshop for foss4g neebies

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
