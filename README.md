# AWF Priority Landscapes — Conservation Planning Analytics

This repository contains data and code for analysing 42 African Wildlife Foundation (AWF) priority landscapes across sub-Saharan Africa. The analysis produces non-spatial visualisations (and, later, spatial maps) to support AWF's conservation planning and conservation geography teams.

**Isaac Mureithi** · I.N.Mureithi@exeter.ac.uk · IMureithi@awf.org
Research Fellow, Oppenheimer Programme in African Landscape Systems (OPALS)
University of Exeter & African Wildlife Foundation

Use of this code is licensed under GPL v3.

## Project overview

The project combines satellite-derived land cover change (Esri/Impact Observatory 10 m LULC, 2017–2025), gridded SSP2 population projections, Key Biodiversity Area coverage, above-ground biomass (ESA CCI Biomass v6), precipitation climatology (CHIRPS 1991–2020) and protected area coverage (WDPA). Attributes were extracted per landscape in Google Earth Engine. The aim is landscape-level diagnostics (protection gaps, cropland conversion, population–nature interaction, carbon stock × threat) that inform conservation prioritisation across AWF's portfolio.

## Repository contents

| Script | Description |
|---|---|
| `scripts/Mureithi_Isaac-AWF_Landscapes.Rmd` | R Markdown analysis: data preparation, shared theme, the five non-spatial figures, and the spatial maps (being added one at a time). |

| File | Description |
|---|---|
| `data/raw/awf_landscapes_raw.xlsx` | Raw landscape attributes (sheet `AWF_Landscapes`, 42 × 24) plus a `Metadata` data dictionary sheet. |
| `data/raw/awf_landscape_centroids.csv` | Landscape point locations (`lon`, `lat`) used for the maps. **Approximate, hand-geocoded placeholders** (see `Confidence` column) until centroids are exported from the AWF landscape polygons in GEE. |
| `data/processed/awf_landscapes_clean.csv` | Cleaned data with derived variables (population growth, population density, protection gap, annualised cropland rates, cropland direction, AGB class). |
| `outputs/figures/01_protection_gap_dumbbell.png` | KBA share vs protected share per landscape. |
| `outputs/figures/02_cropland_dynamics_bar.png` | Net cropland change 2017–2025. |
| `outputs/figures/03_population_nature_scatter.png` | SSP2 population growth vs natural cover. |
| `outputs/figures/04_carbon_threat_quadrant.png` | AGB density vs relative cropland change. |
| `outputs/figures/05_composite_overview.png` | 2×2 composite of the four figures above. |
| `outputs/figures/06_map_landscape_locations.png` | Map 1: locations of the 42 landscapes (bubble area = landscape area), with an East Africa zoom panel. |
| `outputs/figures/07_map_protection_gap.png` | Map 2: protection gap (protected % minus KBA %, classed colours) with bubble area = KBA area. |

`outputs/tables/` is reserved for summary tables.

## Data sources

| Dataset | Source | Resolution | Period |
|---|---|---|---|
| AWF priority landscapes | AWF internal layer | Vector polygons | — |
| Population projections (SSP2) | Wang, Meng & Long | ~1 km | 2030, 2050 |
| Key Biodiversity Areas | AWF Africa_KBA asset (global KBA standard) | Vector polygons | — |
| Land use / land cover | Esri/Impact Observatory Sentinel-2 LULC | 10 m | 2017–2025 |
| Precipitation | CHIRPS Daily | ~5.6 km | 1991–2020 mean |
| Above-ground biomass | ESA CCI Biomass v6 | 100 m | 2022 |
| Protected areas | World Database on Protected Areas (WDPA) | Vector polygons | Current |
| Country boundaries (map context) | Natural Earth via `rnaturalearth` | 1:50m vector | Current |

## Getting started

```bash
git clone https://github.com/Ismurn/Mureithi_Isaac-AWF_Landscapes.git
```

Open `AWF_Landscapes.Rproj` in RStudio, then open and knit (or run chunk by chunk) `scripts/Mureithi_Isaac-AWF_Landscapes.Rmd`. Packages are installed on demand via `pacman::p_load()`.

## Acknowledgements

This work is supported by the Oppenheimer Programme in African Landscape Systems (OPALS), jointly hosted by the University of Exeter and the African Wildlife Foundation. Landscape attribute data were processed in Google Earth Engine. Repository structure follows the [TESS Lab research repository template](https://github.com/TESS-Laboratory/research-repository-template).
