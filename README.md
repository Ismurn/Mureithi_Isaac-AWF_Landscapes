**AWF Priority Landscapes — Conservation Planning Analytics**

This repository contains data and code for analysing African Wildlife Foundation (AWF) priority landscapes across sub-Saharan Africa. The analysis produces non-spatial visualisations and spatial maps to support AWF's conservation planning and conservation geography teams.

**Isaac Mureithi** · (I.N.Mureithi@exeter.ac.uk) (IMureithi@awf.org)
Research Fellow, Oppenheimer Programme in African Landscape Systems (OPALS)
University of Exeter & African Wildlife Foundation

Use of this code is licensed under GPL v3.

**Project overview**

This project analyses 42 AWF priority landscapes using satellite-derived land cover change (Esri/Impact Observatory 10 m LULC, 2017–2025), gridded population projections (Wang, Meng & Long SSP2), Key Biodiversity Area coverage, above-ground biomass stocks (ESA CCI Biomass v6), precipitation climatology (CHIRPS 1991–2020), and protected area coverage (WDPA). The aim is to produce landscape-level diagnostics — protection gap assessments, cropland conversion pressure maps, population–nature interaction profiles, and carbon stock × threat matrices — that inform conservation prioritisation across AWF's continental portfolio.

**Repository contents**
Script	Description
01_data_prep.R	Reads raw landscape attribute data (CSV export from Google Earth Engine), cleans column types, derives analysis variables (population growth rates, protection gaps, cropland expansion rates), and writes a processed dataset.
02_non_spatial_plots.R	Produces non-spatial visualisations: protection gap dumbbell chart, cropland dynamics diverging bar, population–nature scatter, and carbon stock × threat quadrant matrix.
03_spatial_data_prep.R	Sources landscape polygon boundaries and contextual layers (country boundaries, KBAs, protected areas) using rnaturalearth, wdpar, and manual geocoding.
04_spatial_maps.R	Produces choropleth and bivariate spatial maps of landscape indicators using tmap.
05_composite_figures.R	Assembles composite multi-panel figures for reporting and presentation.

**File	Description**
data/raw/awf_landscapes_raw.csv	Landscape-level attributes for 42 AWF priority landscapes, exported from Google Earth Engine. Variables cover area, SSP2 population projections (2030, 2050), KBA overlap, Esri LULC (2017 & 2025), CHIRPS precipitation, ESA CCI above-ground biomass, and WDPA protection coverage.
data/processed/awf_landscapes_clean.csv	Cleaned dataset with derived variables (population growth rates, protection gaps, cropland dynamics).

**Outputs**
Figures and tables are written to outputs/figures/ and outputs/tables/ respectively. Key outputs include:
- Protection gap dumbbell chart (KBA% vs Protected%)
- Cropland dynamics diverging bar (net change 2017–2025)
- Population–nature scatter (SSP2 growth vs natural cover)
- Carbon stock × threat quadrant (AGB density vs cropland expansion)
- Spatial maps of landscape indicators across Africa

**Data sources**
- AWF priority landscapes	AWF internal layer	Vector polygons	—
- Population projections (SSP2)	Wang, Meng & Long	~1 km gridded	2030, 2050
- Key Biodiversity Areas	AWF Africa_KBA asset (global KBA standard)	Vector polygons	—
- Land use / land cover	Esri/Impact Observatory Sentinel-2 LULC	10 m	2017–2025
- Precipitation	CHIRPS Daily	~5.6 km	1991–2020 mean
- Above-ground biomass	ESA CCI Biomass v6	100 m	2022
- Protected areas	World Database on Protected Areas (WDPA)	Vector polygons	Current

**Getting started**
Clone this repository:
```{r}
bash
git clone https://github.com/Ismurn/Mureithi_Isaac-AWF_Landscapes.git
```

Restore the R package environment:
```{r}
r
renv::restore()
```

**Running the analysis**
Run scripts in numerical order:
- scripts/01_data_prep.R
- scripts/02_non_spatial_plots.R
- scripts/03_spatial_data_prep.R
- scripts/04_spatial_maps.R
- scripts/05_composite_figures.R

**Acknowledgements**
This work is supported by the Oppenheimer Programme in African Landscape Systems (OPALS), jointly hosted by the University of Exeter and the African Wildlife Foundation. Landscape attribute data were processed in Google Earth Engine.
