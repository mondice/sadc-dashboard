ESRI SATELLITE GEOJSON DEMO
============================

Files
-----
1. satellite_current_positions.geojson
   - Geometry: Point
   - 5 dummy satellites
   - Includes heading, speed, altitude, direction and timestamp.

2. satellite_prediction_paths.geojson
   - Geometry: LineString
   - One prediction path per satellite.
   - Includes heading, direction and prediction time range.

Why two files?
--------------
ArcGIS GeoJSONLayer supports one geometry type per layer. Keep satellite points
and prediction lines in separate GeoJSON layers.

Suggested public HTTPS URL format
---------------------------------
Upload the two files to a public GitHub repository, for example:
https://github.com/YOUR_USERNAME/satellite-demo

Then use the RAW URLs in Esri:
https://raw.githubusercontent.com/YOUR_USERNAME/satellite-demo/main/satellite_current_positions.geojson
https://raw.githubusercontent.com/YOUR_USERNAME/satellite-demo/main/satellite_prediction_paths.geojson

ArcGIS JavaScript example
-------------------------
const positions = new GeoJSONLayer({
  url: "https://raw.githubusercontent.com/YOUR_USERNAME/satellite-demo/main/satellite_current_positions.geojson",
  title: "Live Satellites"
});

const paths = new GeoJSONLayer({
  url: "https://raw.githubusercontent.com/YOUR_USERNAME/satellite-demo/main/satellite_prediction_paths.geojson",
  title: "Satellite Prediction Paths"
});

map.addMany([paths, positions]);

Notes
-----
- Coordinates are [longitude, latitude] in WGS84.
- The data is DEMO/DUMMY data, not real orbital data.
- A static GeoJSON file will not move by itself. For live movement, update the
  HTTPS GeoJSON endpoint periodically and refresh/reload the layer in your app.
- Use heading_deg to rotate an arrow/satellite symbol.
