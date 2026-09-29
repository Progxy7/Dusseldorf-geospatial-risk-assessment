# Dusseldorf-geospatial-risk-assessment
Spatial analysis and environmental risk assessment of industrial zones in Düsseldorf using QGIS.
## Map 01: Raw Master Metric Landuse
![Map 01: Raw Master Metric Landuse](<Map 01_Raw Master Metric Landuse.png>)

* **Objective:** Establish a clean, uncorrupted spatial database in metric units.
* **QGIS Tool Used:** Layer Export / Save Features As (GeoPackage format).
* **Input Layer:** Raw OpenStreetMap shapefile (`gis_osm_landuse_a_free_1`).
* **Output Layer:** `00-landuse-master-metric` (Forced to `EPSG:32632` WGS 84 / UTM zone 32N).
* **Analytical Takeaway:** The raw OpenStreetMap landuse dataset contains every type of urban zone mixed together—residential areas, industrial complexes, commercial districts, parks, and forests. By locking the coordinate system to metric units right from the start, we set a stable foundation and completely avoid the projection errors that can break spatial calculations later.
## Map 02: Hydrographic Receptors (Waterways)
![Map 02: Hydrographic Receptors](<Map 02_Waterways.png>)

* **Objective:** Extract and isolate all surface water bodies within the Düsseldorf study area as primary environmental receptors.
* **QGIS Tool Used:** Layer Extraction & Reprojection / Save Features As (GeoPackage format).
* **Input Layer:** Raw OpenStreetMap water polygon dataset (`gis_osm_water_a_free_1`).
* **Output Layer:** `01_Water_Metric` (Forced to `EPSG:32632` WGS 84 / UTM zone 32N).
* **Analytical Takeaway:** Rendered in solid hydrographic blue, this layer represents all natural and artificial surface water bodies across Düsseldorf. Establishing this receptor layer independently is critical because industrial pollutant runoff directly threatens aquatic ecosystems and municipal water security.
