RGE Alti Version 2.0
===

The RGE ALTI dataset describes the digital elevation model (DEM) of France with the pixel size of 1m. It was created from surveys obtained by airborne lidar or by correlation of aerial images.

Lidar was deployed for flood-prone, coastal, and large forest areas. The vertical accuracy of the DEM in these areas is between 0.2m and 0.5m. Radar was used in mountain areas (Alps, Pyrenees, Cevennes, Corsica). Caution: in areas with steep slopes, the average vertical accuracy is the order of 7m.

The accuracy of these fields has been checked against various sources: the road and hydrographic networks of the BD TOPO, geodetic terminals and points calculated on the ground.

Aerial photo correlation techniques are used in the rest of the territory. On certain zones treated by correlation, ground measurements are absent over large extents due to the presence of vegetation (wooded areas, for example). 1987-2001 altimetry data (BD Alti) are used to fill these gaps. The vertical accuracy of the DEM on these areas is between 0.5m and 0.7m.

Currently the collection includes a single image IGN/RGE_ALTI/1M/2_0/FXX showing metropolitan France.

See also:[user's guide](https://geoservices.ign.fr/sites/default/files/2021-07/DC_RGEALTI_2-0.pdf).

#### Area covered in Earth Engine
Metropolitan area of France

#### Code Editor Snippet
```javascript
// Import the dataset.
var elevation = ee.ImageCollection("IGN/RGE_ALTI/1M/2_0").first().select("MNT");
var slope = ee.Terrain.slope(elevation);

// Define a location of interest.
var lon = 5.04855;
var lat =  45.73616;
var poi = ee.Geometry.Point(lon, lat);

// Create a custom elevation palette from hex strings.
var elevationPalette = ['006600', '002200', 'fff700', 'ab7634', 'c4d0ff', 'ffffff'];
// Use these visualization parameters, customized by location.
var visParams = {min: 1, max: 3000, palette: elevationPalette};
var visParams2 = {min: 0, max: 20};

// Visualize elevation and terrain slope.  
Map.setCenter(lon, lat, 5);
Map.addLayer(elevation.visualize(visParams), {}, "elevation");
Map.addLayer(slope.visualize(visParams2), {}, "slope");
```
![asset_snippet](/assets/eeassets-snippets/rgealti.gif)

[Visit the code editor here](https://code.earthengine.google.com/?scriptPath=users%2Fguiattard_gei%2Fee-france%3Argealti%2Frge_explorer)

#### Data producer
[IGN](https://www.ign.fr/)

#### Citation
```
IGN (2021) RGE ALTI 1m [Data set]. Accessed 2022-07-01 from IGN website
```

#### Licence
Etalab Open License 2.0

#### Implementation in Earth Engine
Currated in Earth Engine with the support of [Guillaume Attard](https://guillaumeattard.com/), [Julien Bardonnet](https://www.linkedin.com/in/julienbardonnet/) and Simon Ilyushchenko.
