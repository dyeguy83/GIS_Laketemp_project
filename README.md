# GIS_Laketemp_project
Lake Turnover Analysis of Strawberry Reservoir

Author: Kyler Dye
Course: GEOG 3200 Final Project

Project Overview

This project analyzes lake turnover at Strawberry Reservoir using satellite imagery and GIS methods. The goal was to determine which month lake turnover occurs and whether the lake turnover pattern is consistent from year to year.

The workflow can also be used as a guide for analyzing lake turnover in other bodies of water.

Data Sources

The project used lake boundary data and satellite imagery from multiple sources:

Utah Lakes NHD: Lake shapefile data from the Utah Geospatial Resource Center (UGRC)
Sentinel-2: Satellite imagery downloaded from the Copernicus Data Space Ecosystem
Landsat 8-9: Satellite imagery downloaded through USGS EarthExplorer
Methods
1. Strawberry Reservoir Shapefile

The Utah Lakes NHD shapefile was added to ArcGIS Pro. Strawberry Reservoir was selected from the attribute table and exported as its own shapefile.

2. NDVI Analysis

Sentinel-2 imagery was added to ArcGIS Pro. NDVI was calculated using:

Near Infrared: Band 8
Red: Band 4

NDVI maps were created for August through November 2024, as well as October 2022 and October 2023.

3. Clip Raster

The NDVI rasters were clipped to the Strawberry Reservoir boundary using the Clip Raster tool. The option to use the input features for clipping geometry was enabled.

4. Land Surface Temperature (LST)

Land Surface Temperature was calculated using the Raster Calculator. The workflow included six steps:

Top of Atmosphere Spectral Radiance
TOA (L) = ML × Qcal + AL
Brightness Temperature
BT = (K2 / (ln(K1 / L) + 1)) − 273.15
Normalized Difference Vegetation Index
NDVI = (Band 5 − Band 4) / (Band 5 + Band 4)
Proportional Vegetation
Pv = ((NDVI − NDVImin) / (NDVImax − NDVImin))²
Land Surface Emissivity
ε = 0.004 × Pv + 0.986
Land Surface Temperature
LST = BT / (1 + (0.00115 × BT / 1.4388) × Ln(ε))

The LST workflow was repeated for August and October 2024.

5. Creating Data Points

A point shapefile was created in ArcGIS Pro. Three points were placed on Strawberry Reservoir:

North end
South end
East side

These points were used to collect NDVI and LST values.

6. Creating the Data Table

Fields were added to the point attribute table for the different months and LST measurements. Values were collected from each map and entered into the table for each point.

Results

The analysis indicated that lake turnover occurred in October.

The October imagery showed higher NDVI values at the three sampling points, while the other months did not show the same pattern.

The analysis also showed that the lake turnover pattern varied somewhat between years. Some similarities were visible, including a similar swirl pattern in the upper-right portion of the reservoir. However, the other years did not show lake turnover as strongly as 2024.

Challenges

Several challenges were encountered during the project:

Some Landsat bands did not work properly for the NDVI analysis.
A personal computer had difficulty running the GIS software smoothly.
Solutions

Sentinel-2 imagery was used instead of Landsat data because it was more reliable for the analysis. The GIS workflow was also condensed into fewer maps to improve computer performance.

Future Improvements

Future analysis could focus more closely on October by collecting imagery on a weekly basis to determine which week lake turnover occurs.

Weekly LST measurements could also be included to examine changes in water temperature during the turnover period.

Conclusion

The results suggest that October is the primary month when lake turnover occurs at Strawberry Reservoir. The timing and spatial pattern of turnover can vary between years, so additional weekly observations during October could provide a better understanding of when and how turnover occurs.

Project Files
data/ – Contains project datasets and satellite imagery used in the analysis.
code/ – Contains code, scripts, or workflow files used for the project.
README.md – Provides an overview of the project, data, methods, results, and future improvements.
