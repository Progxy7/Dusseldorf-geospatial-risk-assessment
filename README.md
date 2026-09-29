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

### Map 04a: Human Settlement Receptors (Green)
![Map 04a: Residential Zones](<Map 04a_Residential.png>)

### Map 04b: Heavy Economic Activity Zones (Red)
![Map 04b: Industrial Zones](<Map 04b_Industrial.png>)

### Map 04c: Combined Functional Zone Interface
![Map 04c: Combined Functional Zones](<Map 04c_Combined Zones.png>)

* **Objective:** Extract specific functional urban zones from the master dataset to evaluate the spatial proximity between vulnerable human populations and heavy industrial operations.
* **Cartographic Symbology:** Residential settlements are rendered in distinctive green, while industrial and commercial operation zones are designated in high visibility red.
* **Advanced QGIS Tools Deployed:**
  * **Vector Geoprocessing:** Verified and standardized all vector layers to the projected coordinate system EPSG:32632 (WGS 84 / UTM zone 32N) to guarantee accurate metric area calculations and spatial alignment.
  * **Attribute Query Builder:** Executed structured SQL queries to filter and isolate distinct polygon features (specifically isolating residential and industrial classifications) directly from the raw OpenStreetMap database.
  * **Categorized Symbology Engine:** Applied custom color rendering and layer prioritization to ensure visual clarity when stacking both functional zones onto a single analytical canvas.
* **Analytical Takeaway:** Segregating the spatial data into isolated layers proves critical for advanced risk modeling. The green residential map establishes the exact geographic footprint of human exposure. The red industrial map pinpoints the exact origin nodes for potential environmental contaminants. When overlaid in the combined view, the immediate interfaces between residential neighborhoods and industrial complexes become starkly visible. This targeted spatial extraction provides the foundational intelligence required for municipal zoning review and targeted environmental health interventions.
## Map 05: Predictive Risk Modeling (500 Meter Industrial Hazard Buffer)

### Map 05a: Human Exposure (Industrial Buffer and Residential Zones)
![Map 05a: Industrial Buffer and Residential Zones](<Map 05a_Industrial and Residential.png>)

### Map 05b: Ecological Vulnerability (Industrial Buffer and Waterways)
![Map 05b: Industrial Buffer and Waterways](<Map 05b_Industrial and Waterways.png>)

### Map 05c: Logistical Intersections (Industrial Buffer and Railways)
![Map 05c: Industrial Buffer and Railways](<Map 05c_Industrial and Railways.png>)

* **Strategic Rationale:** A professional spatial assessment must evolve beyond simply mapping where features are located, to analyzing how they interact. Generating a proximity buffer transitions this project from descriptive cartography into predictive environmental risk modeling. This analytical leap answers the ultimate question of environmental justice and public safety: who and what is actually within the danger zone?
* **Objective:** Establish a 500 meter zone of influence surrounding heavy industrial operations to quantify the immediate exposure risk for human settlements, ecological corridors, and critical transport infrastructure.
* **Advanced QGIS Tools Deployed:**
  * **Vector Geoprocessing Buffer:** Applied a 500 meter spatial boundary radiating from all industrial polygons to simulate standard airborne dispersion, noise pollution limits, and localized chemical runoff perimeters.
  * **Topological Overlay Analysis:** Stacked the generated risk perimeter beneath the primary receptor layers to visually highlight the exact spatial intersection of hazard proximity across multiple environmental domains.
* **Analytical Takeaway:** By testing the industrial buffer against three distinct receptors, this model demonstrates comprehensive risk awareness. Map 05a isolates the specific residential neighborhoods facing maximum exposure to industrial air and noise pollution. Map 05b identifies precise locations where industrial runoff directly threatens aquatic ecosystems and municipal water quality. Map 05c pinpoints critical logistical intersections where hazardous material transport via railways overlaps with localized industrial zones. This holistic buffering approach provides a definitive spatial foundation for targeted municipal emergency response and proactive environmental policymaking.
## Map 06: Hydrological Threat Modeling (200 Meter Flood Inundation Buffer)

### Map 06a: Human Vulnerability to Flooding (Water Threat vs Residential Zones)
![Map 06a: Waterway Buffer and Residential Zones](<Map 06a_Waterway Buffer and Residential.png>)

### Map 06b: Secondary Disaster Risk (Water Threat vs Industrial Zones)
![Map 06b: Waterway Buffer and Industrial Zones](<Map 06b_Waterway Buffer and Industrial.png>)

* **Strategic Rationale:** While previous models focused on anthropogenic hazards where industry acted as the source of contamination, this model reverses the directional risk to evaluate natural hazards where water acts as the active threat. Mapping the inundation zone is essential to predict both primary structural damage and catastrophic secondary environmental spills.
* **Objective:** Establish a 200 meter riparian flood buffer radiating from surface water bodies to simulate severe flood scenarios against human settlements and heavy industrial infrastructure.
* **Advanced QGIS Tools Deployed:**
  * **Hydrological Vector Buffering:** Generated a 200 meter spatial boundary expanding outward from all aquatic features to model municipal floodplains and peak water level expansion.
  * **Directional Risk Overlay:** Contrasted the active flood threat against passive receptor layers (residential and industrial polygons) to separate direct human displacement risks from secondary chemical contamination risks.
* **Analytical Takeaway:** Treating the waterway as the hazard source completely changes the vulnerability landscape of Düsseldorf. Map 06a reveals the exact residential neighborhoods that will be physically submerged during a severe flood event, indicating where municipal evacuation routes must be prioritized. Map 06b highlights a severe secondary vulnerability by identifying industrial facilities located inside the flood zone. If floodwaters breach these industrial complexes, the receding water will drag toxic materials directly back into the primary water supply, transforming a natural hydrological disaster into an uncontrollable chemical spill.
