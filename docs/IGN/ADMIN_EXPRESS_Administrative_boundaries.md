ADMINEXPRESS 08-2022
===

The administrative divisions of the French territory (municipality, departmental district, department, region...).

#### Description
The ADMIN EXPRESS product contains the following data layers or object classes (in french):
- ARRONDISSEMENT (ARRON)
- ARRONDISSEMENT_MUNICIPAL (ARRMU)
- CANTON (CANTO)
- CHFLIEU_ARRONDISSEMENT_MUNICIPAL (CHFAM)
- CHFLIEU_COMMUNE (CHFCO)
- CHFLIEU_COMMUNE_ASSOCIEE_OU_DELEGUEE (CHFLC)
- COLLECTIVITE_TERRITORIALE (COLLE)
- COMMUNE (COMMU)
- COMMUNE_ASSOCIEE_OU_DELEGUEE (COMAS)
- DEPARTEMENT (DEPAR)
- EPCI (EPCI)
- REGION (REGIO)

It covers all French departments, including the overseas departments and regions. 

ADMIN EXPRESS allows cross-referencing with other data sources in order to build thematic representations of the territory according to an administrative scale (municipality, departmental district, department, region). The official dataset description is available [here](https://geoservices.ign.fr/sites/default/files/2021-11/DC_DL_ADMIN_EXPRESS_3-1_0.pdf)

#### Code Editor Snippet
```javascript
// Import the datasets.
var regions = ee.FeatureCollection("projects/ee-france/assets/IGN/ADMIN_EXPRESS/REGIO");
var communes = ee.FeatureCollection("projects/ee-france/assets/IGN/ADMIN_EXPRESS/COMMU");


// Define a location of interest.
var lon = 5.04855;
var lat =  45.73616;
var poi = ee.Geometry.Point(lon, lat);

// Paint the dataset with appropriate palette.
var styleRegions = {
  fillColor: 'b5ffb4',
  color: '00909F',
  width: 2.0,
};

regions = regions.style(styleRegions);

var styleCommunes = {
  fillColor: 'grey',
  color: 'black',
  width: 1,
};

communes = communes.style(styleCommunes);

Map.addLayer(regions, {}, 'Regions');
Map.addLayer(communes, {}, 'Communes');

Map.setCenter(lon, lat, 6);
```
![asset_snippet](/assets/eeassets-snippets/adminexpress.gif)

[Visit the code editor here](https://code.earthengine.google.com/?scriptPath=users%2Fguiattard_gei%2Fee-france%3Aadminexpress%2Fadminexpress_explorer)

#### Data producer
[IGN](https://www.ign.fr/)

#### Citation
```
IGN (2022) ADMIN EXPRESS Version 3.1 - The administrative division of the French territory.
```

#### Implementation in GEE
[Guillaume Attard](https://guillaumeattard.com/) & [Julien Bardonnet](https://www.linkedin.com/in/julienbardonnet/)
