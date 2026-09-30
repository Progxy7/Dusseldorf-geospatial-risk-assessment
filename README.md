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
## Map 07: Quantitative Spatial Extraction (500 Meter Industrial Hazard Intersections)

### Map 07a: Extracted High Risk Residential Geometries
![Map 07a: Intersected Vulnerable Residential](<Map 07a_Intersected Vulnerable Residential.png>)

### Map 07b: Extracted Compromised Waterway Segments
![Map 07b: Intersected Compromised Waterways](<Map 07b_Intersected Compromised Waterways.png>)

### Map 07c: Extracted Hazardous Railway Corridors
![Map 07c: Intersected Hazardous Railways](<Map 07c_Intersected Hazardous Railways.png>)

* **Strategic Rationale:** Visual overlays identify general threat proximity, but actionable environmental mitigation requires exact spatial isolation. Executing a topological intersection strips away all safe zones and extracts only the precise geometries caught inside the industrial hazard perimeter. This operation prepares the spatial data for exact area calculation and volumetric impact modeling.
* **Objective:** Mathematically intersect the functional receptor layers with the 500 meter industrial buffer to isolate and extract the precise polygons and lines requiring immediate emergency planning.
* **Advanced QGIS Tools Deployed:**
  * **Vector Topological Intersection:** Executed the Intersection geoprocessing algorithm to calculate the overlapping geometries between the three receptor layers and the anthropogenic hazard buffer. This creates brand new vector layers containing exclusively the areas where the inputs physically overlap.
  * **High Contrast Symbology:** Applied stark high visibility styling to the newly extracted features against a neutral basemap to emphasize the absolute critical zones within the urban matrix.
* **Analytical Takeaway:** This mathematical extraction completely isolates the anthropogenic danger zones. Map 07a physically extracts the exact residential structures exposed to severe industrial pollution, providing the geometries needed to calculate the affected population size. Map 07b isolates the specific river segments receiving direct industrial runoff, prioritizing where municipal water quality sensors must be deployed. Map 07c extracts the logistical rail corridors operating inside high threat zones, which is vital for planning hazardous material transport routes and preventing compounding disaster scenarios.
## Map 08: Quantitative Spatial Extraction (200 Meter Flood Hazard Intersections)

### Map 08a: Extracted Flood Prone Residential Geometries
![Map 08a: Intersected Flooded Residential](<Map 08a_Intersected Flooded Residential.png>)

### Map 08b: Extracted Compromised Industrial Facilities (Critical Threat Nodes)
![Map 08b: Intersected Flooded Industry](<Map 08b_Intersected Flooded Industry.png>)

* **Strategic Rationale:** Just as the anthropogenic intersection isolated pollution victims, the hydrological intersection isolates the exact geometries vulnerable to natural inundation. Extracting these specific structural footprints provides the raw data required for municipal evacuation logistics and secondary disaster prevention.
* **Objective:** Mathematically intersect the functional receptor layers with the 200 meter waterway buffer to isolate the precise residential and industrial polygons trapped within the active floodplain.
* **Advanced QGIS Tools Deployed:**
  * **Vector Topological Intersection:** Executed the Intersection geoprocessing algorithm to calculate the overlapping geometries between the receptor layers and the flood inundation buffer.
  * **Enhanced Cartographic Highlighting:** Applied a vibrant purple fill with an expanded stroke weight and an outer glow render effect to Map 08b. This advanced styling ensures that micro geometries remain highly visible and immediately draw the eye even when viewing the entire urban scale.
* **Analytical Takeaway:** This mathematical extraction isolates the natural disaster zones and reveals a crucial insight into urban planning. Map 08a extracts the exact residential structures exposed to severe flooding, providing the exact target areas for rescue deployment. Interestingly, Map 08b reveals a very sparse distribution of compromised industrial facilities. This sparsity is a highly positive indicator of effective historical municipal zoning, showing that most heavy industry was successfully built safely outside the riparian zone. However, these few isolated anomalies now represent the most critical secondary threat nodes in the entire city. Because they are so few, environmental agencies can focus all emergency containment funding on these specific pinpointed facilities to prevent toxic spillover during a flood.
## Map 09: Industrial Distribution and Topographic Context

![Map 09: Topographic Vulnerability](<Map 09_Topographic Vulnerability.png>)

* **Strategic Rationale:** Evaluating industrial hazards requires understanding the physical terrain. Chemical spills and heavy gas emissions are dictated by gravity and elevation. A flat map obscures these physical realities.
* **Objective:** Integrate high resolution elevation data with industrial zoning to visualize potential downhill contamination pathways toward waterways and residential areas.
* **Advanced QGIS Tools Deployed:**
  * **Web Map Services:** Connected directly to OpenTopoMap servers via QuickMapServices to stream contour and hill shading data.
  * **Geometry Dissolve:** Merged administrative boundary subdivisions into a single unified polygon to eliminate internal rendering conflicts.
  * **Inverted Polygon Masking:** Applied an inverted geometry style with a Solid White fill and a Transparent stroke to clip the global web map perfectly to the municipal boundary. Specifying a fully transparent stroke was critical to eliminating rendering artifacts along the boundary edge.
* **Analytical Takeaway:** The topographic basemap reveals the exact elevation of industrial zones relative to the river valley. By masking the outside world with a transparent stroke boundary, the visual focus remains strictly on the internal municipal terrain. This sets the foundation for calculating the specific downhill threat of the largest industrial facilities.
## Map 10: Spatial Hazard Analysis and Infrastructure Vulnerability

### Map 10A: Far View Biggest Facility
![Map 10A Far View](<Map 10a_Far View Biggest Facility.png>)

### Map 10B: Close Up View Biggest Facility
![Map 10B Close Up View](<Map 10b_Close Up View Biggest Facility.png>)

* **Objective:** To simulate a severe industrial accident and identify critical civilian and environmental infrastructure caught within a 500 meter containment radius.
* **Geoprocessing and Analytical Workflow:**
  * **Spatial SQL Extraction:** Bypassed manual selection errors by writing a direct expression query inside the attribute table using `$area = maximum($area)` to automatically isolate the single largest industrial polygon.
  * **Custom Text Labeling:** Activated the QGIS labeling engine on the isolated layer, set the value string to `'Biggest Facility'`, and applied a high contrast white text buffer halo for clear legibility over the basemap.
  * **Proximity Buffering:** Executed a 500 meter dissolve buffer around the facility perimeter to generate a continuous, uniform containment zone representing potential airborne dispersion or surface runoff hazards.
* **Data Limitations and Proxies:** In the absence of facility specific chemical emission inventories we utilized spatial area as a proxy for maximum industrial scale. We acknowledge that spatial footprint does not directly equate to toxicity as a large logistics warehouse could trigger this extraction over a smaller chemical processing plant. We therefore classify the target strictly as the Biggest Facility rather than the highest toxic threat.
* **Impact Assessment:** The simulated hazard zone reveals severe spatial vulnerability. The 500 meter radius directly engulfs a major railway line, multiple high density residential blocks, and intersects the main river. The river intersection is particularly critical as topographic runoff from the facility could introduce a secondary aquatic contamination vector.
## Map 11: Emergency Evacuation and Environmental Remediation Strategy

### Map 11: Emergency Evacuation and Water Remediation
![Map 11 Emergency Strategy](<Map 11_Emergency Evacuation and Remediation Strategy.png>)

* **Objective:** To establish an emergency response protocol and containment strategy for civilian evacuation and aquatic protection following a severe industrial hazard event at the primary facility, specifically focusing on the massive thyssenkrupp Steel Europe AG plant as the largest industrial asset in the study area.
* **Complete Step-by-Step Geoprocessing and QGIS Workflow:**
  * **Vulnerability Intersection:** Executed spatial intersection geoprocessing tools using the buffered facility layer against baseline infrastructure to extract precise vulnerable residences, vulnerable railway, and vulnerable waterway geometries.
  * **Residential Exposure Mapping:** Highlighted the specific shades of pink polygon geometries directly surrounding the major thyssenkrupp Steel Europe AG facility to identify residential populations living within the immediate impact zone.
  * **Emergency Evacuation Routing:** Digitized four distinct green escape routes designed to guide residents safely away from the potential hazard zone while bypassing compromised regional transportation corridors.
  * **Aquatic Containment Strategy:** Deployed three thick purple and black containment boom lines strategically across the waterways intersecting the facility perimeter to intercept toxic runoff and protect all three vulnerable water channels from downstream contamination.
  * **Official Facility Identification:** Extracted and mapped the official name thyssenkrupp Steel Europe AG directly from the underlying vector data attributes, highlighting its designation as the biggest facility within the Düsseldorf industrial zone.
  * **Attribute Table Configuration:** Opened the vector layer attribute tables via the layer panels, enabled editing mode, and created custom text string fields to explicitly store asset nomenclature and descriptions.
  * **Dynamic Labeling Engine Setup:** Configured QGIS label properties from no labels to single labels, linked the value expression directly to the custom attribute fields, activated high contrast white text buffer halos, and disabled scale-dependent rendering to ensure universal visibility.
  * **Collision Management:** Overrode default cartographic suppression by enabling settings to show all colliding labels and adjusted line placement parameters to ensure zero occlusion across dense urban intersections.
* **Metallurgical Hazard Profile and Operational Strategy:**
  * **Heavy Metal and Chemical Runoff Mitigation:** Steel manufacturing operations involving blast furnaces, pickling lines, and industrial cooling baths carry high risks of acid and oil laden water runoff during a containment breach, justifying the triple containment boom deployment across local waterways protecting the surrounding aquatic network.
  * **Thermal and Blast Protection:** High temperature metal processing and combustible industrial gases dictate the strict 500 meter buffer zone surrounding the massive thyssenkrupp facility to safeguard the adjacent residential pink population polygons from blast overpressure and air dispersion.
  * **Logistical Disruption Response:** Industrial heavy freight integration requires four distinct multi-directional vector escape corridors to effectively disperse civilian density away from gridlocked regional transport arteries.
