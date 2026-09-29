# Dusseldorf-geospatial-risk-assessment
Spatial analysis and environmental risk assessment of industrial zones in Düsseldorf using QGIS.
## Map 01: Raw Master Metric Landuse
![Map 01: Raw Master Metric Landuse](<Map 01_Raw Master Metric Landuse.png>)

* **Objective:** Establish a clean, uncorrupted spatial database in metric units.
* **QGIS Tool Used:** Layer Export / Save Features As (GeoPackage format).
* **Input Layer:** Raw OpenStreetMap shapefile (`gis_osm_landuse_a_free_1`).
* **Output Layer:** `00-landuse-master-metric` (Forced to `EPSG:32632` WGS 84 / UTM zone 32N).
* **Analytical Takeaway:** The raw OpenStreetMap landuse dataset contains every type of urban zone mixed together—residential areas, industrial complexes, commercial districts, parks, and forests. By locking the coordinate system to metric units right from the start, we set a stable foundation and completely avoid the projection errors that can break spatial calculations later.
## Map 02: Hydrographic Receptors & Base Context (Waterways & Landuse)
![Map 02a: Waterways with Landuse Context](<Map 02_Waterways and Landuse.png>)
![Map 02b: Detailed Waterway Extent](<Map 02_Waterways.png>)

* **Objective:** Isolate and document surface water bodies while maintaining spatial continuity with the master landuse boundary.
* **QGIS Tool Used:** Multi-layer symbol stacking and layer extent verification.
* **Input Layers:** Master landuse polygon dataset paired with OpenStreetMap water receptors (`EPSG:32632`).
* **Analytical Takeaway:** Initial exploration revealed that raw landuse polygons leave minor boundary gaps where major water channels extend past the landuse edge. By presenting a paired multi-layer view (landuse + water alongside isolated waterways), this workflow preserves complete topological integrity, ensuring all hydrographic receptors are accounted for without visual clipping at the study area fringes.
## Map 03: Linear Transport & Hydrographic Receptors (Railways and Waterways)
![Map 03: Railways and Water](<Map 03_Railways and Water..png>)

* **Objective:** Map linear transport infrastructure alongside surface water bodies to visualize multi-receptor proximity within the urban matrix.
* **QGIS Tool Used:** Layer Styling and Symbology Stack (Multi-layer canvas rendering).
* **Input Layers:** Water receptor layer and raw OpenStreetMap railway lines (reprojected to `EPSG:32632`).
* **Analytical Takeaway:** In this multi-receptor view, solid blue polygons represent surface water bodies, while dark charcoal lines represent the railway network. Overlaying these layers demonstrates how transportation corridors intersect with sensitive ecological zones, establishing a visual baseline for multi-hazard spatial risk assessment.
## Map 04: Functional Urban Zones (Residential and Industrial Spatial Extraction)
![Map 04a: Residential Zones](<Map 04a_Residential.png>)
![Map 04b: Industrial Zones](<Map 04b_Industrial.png>)
![Map 04c: Combined Functional Zones](<Map 04c_Combined Zones.png>)

* **Objective:** Extract specific functional urban zones from the master dataset to evaluate the spatial proximity between vulnerable human populations and heavy industrial operations.
* **Cartographic Symbology:** Residential settlements are rendered in distinctive green, while industrial and commercial operation zones are designated in high visibility red.
* **Advanced QGIS Tools Deployed:**
  * **Vector Geoprocessing:** Verified and standardized all vector layers to the projected coordinate system EPSG:32632 (WGS 84 / UTM zone 32N) to guarantee accurate metric area calculations and spatial alignment.
  * **Attribute Query Builder:** Executed structured SQL queries to filter and isolate distinct polygon features (specifically isolating residential and industrial classifications) directly from the raw OpenStreetMap database.
  * **Categorized Symbology Engine:** Applied custom color rendering and layer prioritization to ensure visual clarity when stacking both functional zones onto a single analytical canvas.
* **Analytical Takeaway:** Segregating the spatial data into isolated layers proves critical for advanced risk modeling. The green residential map establishes the exact geographic footprint of human exposure. The red industrial map pinpoints the exact origin nodes for potential environmental contaminants. When overlaid in the combined view, the immediate interfaces between residential neighborhoods and industrial complexes become starkly visible. This targeted spatial extraction provides the foundational intelligence required for municipal zoning review and targeted environmental health interventions.
