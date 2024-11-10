# Geospatial Intelligence Analysis Project: Optimal Installation Sites Near King of Prussia, PA

This project identifies optimal installation sites within a 5 km radius around King of Prussia, PA. Using ArcGIS Pro, we analyzed terrain, infrastructure, and population data to determine suitable locations. The analysis combines slope suitability, infrastructure accessibility, and proximity to population centers to highlight optimal installation points.

## Table of Contents

- [Project Overview](#project-overview)
- [Project Structure](#project-structure)
- [Data and Setup](#data-and-setup)
- [Analysis Workflow](#analysis-workflow)
  - [Step 1: Project Setup and Data Acquisition](#step-1-project-setup-and-data-acquisition)
  - [Step 2: Define the Area of Interest (AOI)](#step-2-define-the-area-of-interest-aoi)
  - [Step 3: Data Preparation and Terrain Analysis](#step-3-data-preparation-and-terrain-analysis)
  - [Step 4: Infrastructure Mapping](#step-4-infrastructure-mapping)
  - [Step 5: Population Centers Analysis](#step-5-population-centers-analysis)
  - [Step 6: Combined Analysis and Suitability Assessment](#step-6-combined-analysis-and-suitability-assessment)
  - [Step 7: Final Visualization and Map Creation](#step-7-final-visualization-and-map-creation)
- [Results](#results)
- [Images](#images)
- [Additional Notes](#additional-notes)

## Project Overview

This project involves the comprehensive spatial analysis of King of Prussia, PA, with the goal of identifying suitable sites for installations within a defined Area of Interest (AOI). The analysis considers terrain suitability, accessibility to infrastructure, and proximity to population centers.

## Project Structure

The project follows an organized folder structure to manage data, maps, and reports efficiently:

```plaintext
Geospatial_Intelligence_Analysis/
├── data/
│   ├── terrain/                 # DEM and terrain suitability data
│   ├── infrastructure/          # Roads and infrastructure data
│   └── population_centers/      # Population center data
├── maps/                        # Exported maps and images
├── reports/                     # Project reports
└── README.md                    # Project documentation (this file)
```

## Data and Setup

### Prerequisites

- **ArcGIS Pro**: The primary software used for spatial data analysis. Ensure that the Spatial Analyst extension is enabled.

### Data Sources

- **Terrain Data**: Acquired from USGS Earth Explorer (SRTM 1 Arc-Second Global DEM).
- **Infrastructure Data**: Roads data from Esri’s Living Atlas or the US Census Bureau TIGER/Line Shapefiles.
- **Population Centers Data**: Places data from the US Census Bureau TIGER/Line Shapefiles.

## Analysis Workflow

### Step 1: Project Setup and Data Acquisition

1. **Create Project Directory Structure**:
   - Set up the `Geospatial_Intelligence_Analysis` folder with subdirectories for `data`, `maps`, and `reports`.
2. **Install Necessary Software**:
   - Install ArcGIS Pro and activate the Spatial Analyst extension.
3. **Acquire Data**:
   - Download DEM, roads, and population data for King of Prussia, PA.
4. **Organize Data**:
   - Save downloaded files into their respective folders under `data/terrain`, `data/infrastructure`, and `data/population_centers`.

### Step 2: Define the Area of Interest (AOI)

1. **Create Central Point for AOI**:
   - In ArcGIS Pro, create a point feature at the coordinates of King of Prussia, PA.
2. **Generate 5 km Buffer**:
   - Use the Buffer tool to create a 5 km radius around the central point.
3. **Style the AOI Polygon**:
   - Adjust symbology for clarity, using a semi-transparent fill to visually define the AOI.

### Step 3: Data Preparation and Terrain Analysis

1. **Load DEM for Terrain Analysis**:
   - Add the DEM file to ArcGIS Pro for slope and aspect calculations.
2. **Calculate Slope**:
   - Run the Slope tool to calculate terrain slope, saving output as `slope.tif`.
3. **Calculate Aspect**:
   - Run the Aspect tool to determine the direction of slope, saving output as `aspect.tif`.
4. **Reclassify Slope for Suitability**:
   - Reclassify the slope raster to highlight slopes under 15 degrees as suitable for installation.
5. **Visualize Terrain Suitability**:
   - Style `slope_suitability.tif` to clearly distinguish suitable and unsuitable areas.

### Step 4: Infrastructure Mapping

1. **Load and Style Roads Data**:
   - Add `roads.shp` to ArcGIS Pro, adjust symbology for easy visibility.
2. **Buffer Roads for Accessibility**:
   - Use the Buffer tool to create a 1 km buffer around roads, indicating accessible areas.
3. **Visualize Road Buffers**:
   - Style the `roads_buffer_1km.shp` layer with a transparent fill to integrate with other data layers.

### Step 5: Population Centers Analysis

1. **Add Population Data**:
   - Add the population centers shapefile to the map.
2. **Clip Population Centers to AOI**:
   - Use the Clip tool to limit the population data to the AOI, saving the output as `population_centers_clipped.shp`.
3. **Calculate Population Density** (if data available):
   - If population data includes counts, calculate density to prioritize locations near higher population densities.

### Step 6: Combined Analysis and Suitability Assessment

1. **Combine Slope Suitability and Road Buffer**:
   - Use Raster Calculator to create a composite suitability map combining `slope_suitability.tif` and `roads_buffer_1km.shp`.
2. **Identify Suitable Areas Near Population Centers**:
   - Assess proximity of suitable areas to population centers using the Near tool, adding a `NEAR_DIST` field.
3. **Select Optimal Sites**:
   - Use selection tools to find areas that satisfy all criteria (slope suitability, road accessibility, proximity to population centers) and export these as `optimal_sites.shp`.

### Step 7: Final Visualization and Map Creation

1. **Prepare Final Map in ArcGIS Pro**:
   - Add all layers (optimal sites, population centers, roads, AOI, terrain) to a new layout.
2. **Customize Symbology and Layout Elements**:
   - Apply unique colors and transparency levels to each layer.
   - Add essential map elements like a title, legend, north arrow, and scale bar.
3. **Export the Map**:
   - Save the final map as `optimal_installation_sites_map.pdf` in the `maps` folder.

## Results

The analysis successfully identified areas suitable for installations based on terrain, road accessibility, and population proximity. These locations are visually represented in the final map, which highlights optimal areas within the 5 km AOI around King of Prussia, PA.

## Images

- **Project Directory Structure**  
  ![Project Directory](Geospatial_Intelligence_Analysis\maps\Project_Directory.png)

- **Defining AOI**  
  ![AOI Definition](Geospatial_Intelligence_Analysis\maps\AOI_5km.png)

- **Slope and Aspect Analysis**  
  ![Slope Analysis](Geospatial_Intelligence_Analysis\maps\slope.png)  
  ![Aspect Analysis](Geospatial_Intelligence_Analysis\maps\aspect.png)

- **Reclassified Slope for Suitability**  
  ![Slope Suitability](Geospatial_Intelligence_Analysis\maps\slope_suitability.png)

- **Roads Buffer**  
  ![Roads Buffer](Geospatial_Intelligence_Analysis\maps\roads_buffer.png)

- **Population Centers Clip**  
  ![Population Centers](Geospatial_Intelligence_Analysis\maps\population_centers_clipped.png)

- **Combined Suitability**  
  ![Combined Suitability](Geospatial_Intelligence_Analysis\maps\combined_suitability.png)

- **Final Map**  
  ![Final Map](Geospatial_Intelligence_Analysis\maps\final_map.png)

## Additional Notes

- **Data Sources**:

  - Terrain data was sourced from USGS Earth Explorer.
  - Infrastructure and population data were obtained from Esri’s Living Atlas and the US Census Bureau’s TIGER/Line Shapefiles.

- **Challenges and Limitations**:

  - Some data layers required re-projection to align with the AOI.
  - The analysis is limited to available data and assumptions made regarding terrain and proximity.

- **Future Improvements**:
  - Additional data layers could be incorporated to refine site selection.

---
