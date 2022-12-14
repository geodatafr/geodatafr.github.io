RPG Version 2.0
===

The graphical parcel register is a geographical database used as a reference for the instruction of the Common Agricultural Policy (CAP) aids.

The anonymized version distributed here as part of the public service of reference data availability contains the graphic data of the parcels (basic land unit of the farmers' declaration) with their main crop. These data are produced by the Agence de Services et de Paiement (ASP) since 2007.

The anonymous data of the RPG are vintage and contain parcels corresponding to those declared for the campaign N in their known situation and stopped by the administration, in general on January 1st of the year N+1. These data cover the entire French territory.

- [Link to the original dataset](https://geoservices.ign.fr/rpg)
- [Link to dataset description](https://geoservices.ign.fr/sites/default/files/2021-12/DC_DL_RPG_2-0.pdf)
- [Other infos](https://odr.inrae.fr/intranet/carto/cartowiki/index.php/RPG_:_Groupes_de_Cultures)

#### Available years and assets in Earth Engine

| Year | Asset ID                                  |
|------|-------------------------------------------|
| 2020 | projects/ee-france/assets/IGN/RPG/rpg2020 |
| 2019 | projects/ee-france/assets/IGN/RPG/rpg2019 |
| 2018 | projects/ee-france/assets/IGN/RPG/rpg2018 |

#### Area covered in Earth Engine
Metropolitan area of France

#### Code Editor Snippet
```javascript
// Import the dataset.
var rpg = ee.FeatureCollection("pprojects/ee-france/assets/IGN/RPG/rpg2020");

// Define a location of interest.
var lon = 5.04855;
var lat =  45.73616;
var poi = ee.Geometry.Point(lon, lat);

// Paint the dataset with appropriate palette.
var empty = ee.Image().byte();
var coloredRpg = empty.paint({
  featureCollection: rpg,
  color: 'CODE_GROUP',
});

var palette = [
  "#fdff8f","#00fc03","#f0ff62","#daeb00","#ffecb2","#ffff00",
  "#fdc101","#f0b300","#bc9200","#624700","#f0f0f0","#b0b0b0",
  "#d0d0d0","#8fb5fe","#ffa07d","#a0c75d","#b5e56d","#bfff60",
  "#e0ffb3","#fe0000","#de01e4","#008001","#9fa600","#008081", 
  "#fea1ce", "#0000ff", "#00b558", "#81007f"]
  
Map.setCenter(lon, lat, 12);
Map.addLayer(coloredRpg, {palette: palette, min:1, max:28}, 'RPG');
```
![asset_snippet](/assets/eeassets-snippets/rpg.gif)

[Visit the code editor here](https://code.earthengine.google.com/?scriptPath=users%2Fguiattard_gei%2Fee-france%3Arpg%2Frpg_explore)

#### Data producer
[IGN](https://www.ign.fr/)

#### Citation
```
IGN (XXXX) RPG Version 2.0 - XXX. Registre Parcellaire Graphique.
```
*replace XXXX by the appropriate year*

#### Licence
Etalab Open License 2.0

#### Implementation in Earth Engine
Currated in Earth Engine by [Guillaume Attard](https://guillaumeattard.com/) & [Julien Bardonnet](https://www.linkedin.com/in/julienbardonnet/)
