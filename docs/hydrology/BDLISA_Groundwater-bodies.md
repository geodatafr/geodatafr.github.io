BDLISA version 2: the hydrogeological french referential
===

[BDLISA](https://bdlisa.eaufrance.fr/) is a referential of the French Water Information System. This dataset classifies the subsoil into hydrogeological entities which are described according to different properties: aquifer or impermeable, free or captive flows, porous, fractured, karstic environment.

BDLISA version 2 has been released in february 2018.

#### Available BDLISA assets in Earth Engine

|Zone         |Code  |EN3-EXT |EN2-EXT |EN1-EXT |EN3-ORD |EN2-ORD |EN1-ORD |EN-COMP |POLY    |ALT     |KARST   |
|-------------|------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|France metro.|FXX   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |
|Guadeloupe   |GUA   |    X   |    X   |    X   |    X   |    X   |    X   |        |    X   |        |        |
|La Réunion   |REU   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |        |        |
|Martinique   |MAR   |    X   |    X   |    X   |    X   |    X   |    X   |        |    X   |        |    X   |
|Guyane       |GUY   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |        |        |
|Mayotte      |MAY   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |    X   |        |        |

For layer codes correspondences (EN3-EXT, EN2-ORD, etc.) see the [offical dataset description](https://reseau.eaufrance.fr/geotraitements/sites/default/files/avertissement_utilisation_BDLISA_version_2.pdf) or visit the [official dataset website](https://bdlisa.eaufrance.fr/decouvrir-la-bdlisa).

#### Area covered in Earth Engine
All France

#### Code Sample
```javascript

// Import local groundwater bodies (level3) covering France Metro.
var table = ee.FeatureCollection("projects/ee-france/assets/bdlisa/FXX/EN3-ORD")

// Select shallow mediums (level 1).
var bdlisa_n1 = table.filter(ee.Filter.eq('OrdreRelEH', 1));

// Paint FeatureCollection to an image using feature-specific style arguments.
// A dictionary of style properties per soil medium type.
var mediumStyles = ee.Dictionary({
  "0": {color: '#ffffff'}, //unknown
  "5": {color: '#79c5f2'}, //aquifer
  "6": {color: '#f2b879'}, //semi-permable
  "7": {color: '#f2e279'}, //impervious
});

// Add feature-specific style properties to each feature based on medium type.
bdlisa_n1 = bdlisa_n1.map(function(feature) {
  return feature.set('style', mediumStyles.get(feature.get('NatureEH')));
});

// Style the FeatureCollection according to each feature's "style" property.
var mediumVisCustom = bdlisa_n1.style({
  styleProperty: 'style'
});

//Define the location of interest.
var lon = 4.857504
var lat = 45.771938337373435
var poi = ee.Geometry.Point(lon, lat)

Map.setCenter(lon, lat, 10)
Map.addLayer(mediumVisCustom, null, 'Aquifer properties');
```
![asset_snippet](/assets/eeassets-snippets/bdlisa.gif)

[Visit the code editor here](https://code.earthengine.google.com/81c7b9c3022cfdf902ed526fc531d90a)

#### Data producer
[BRGM](https://www.brgm.fr/fr)

#### Licence
Etalab Open License 2.0

#### Impelmentation in Earth Engine
Currated in Earth Engine by [Guillaume Attard](https://guillaumeattard.com/) & [Julien Bardonnet](https://www.linkedin.com/in/julienbardonnet/)
