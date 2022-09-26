RGA: Withdrawl-swelling risk of clay soils

The [RGA dataset](https://www.georisques.gouv.fr/donnees/bases-de-donnees/retrait-gonflement-des-argiles) describes the exposure to the phenomenon of clay shrinkage-swelling over clay soils.

#### Area covered in Earth Engine
Metropolitan area of France (excluding the city of Paris)

#### Code Sample
```javascript

// Import the dataset.
var rga = ee.FeatureCollection("projects/ee-france/assets/BRGM/GEOR/RGA");

// Define a location of interest.
var lon = 5.04855;
var lat =  45.73616;
var poi = ee.Geometry.Point(lon, lat);

// Paint the dataset with appropriate palette.
var empty = ee.Image().byte();
var coloredRpg = empty.paint({
  featureCollection: rga,
  color: 'NIVEAU',
});

var palette = ["yellow", "orange", "red"]
  
Map.setCenter(lon, lat, 12);
Map.addLayer(coloredRpg, {palette: palette, min:1, max:3}, 'RGA');
```
![asset_snippet](/assets/eeassets-snippets/rga.gif)

[Visit the code editor here](https://code.earthengine.google.com/?scriptPath=users%2Fguiattard_gei%2Fee-france%3Ageorisques%2Frga_explore)

#### Data producer
[BRGM](https://www.brgm.fr/fr)

#### Licence
Etalab Open License 2.0

#### Implementation in Earth Engine
Currated in Earth Engine by [Guillaume Attard](https://guillaumeattard.com/) & [Julien Bardonnet](https://www.linkedin.com/in/julienbardonnet/)
