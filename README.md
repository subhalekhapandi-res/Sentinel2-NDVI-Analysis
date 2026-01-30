# Sentinel2-NDVI-Analysis

A reproducible Earth observation workflow for seasonal NDVI analysis using Sentinel-2 data and Python-based geospatial tools.

## Overview

This repository contains an end-to-end, notebook-driven workflow to download, preprocess, compute NDVI, create seasonal composites, and analyze temporal changes using Sentinel-2 imagery. The notebooks use commonly available Python geospatial libraries and are designed to be reproducible, modular, and easy to adapt to other regions or time periods.

## Key features

- Download Sentinel-2 L1C/L2A tiles (instructions for multiple sources)
- Cloud detection and masking
- Compute NDVI from Sentinel-2 bands (B08, B04)
- Generate seasonal composites and time-series summaries
- Visualize NDVI maps, seasonal composites, and temporal trends
- Export final rasters and summary CSVs for downstream use

## Getting started

Prerequisites
- Conda (recommended) or Python 3.9+
- Git
- Sufficient disk space for Sentinel-2 tiles you will download

Create an environment (conda)
```bash
conda env create -f environment.yml
conda activate sentinel2-ndvi
```

If you don't have an environment.yml, a minimal pip install list:
```bash
pip install jupyterlab geopandas rasterio rioxarray xarray numpy pandas matplotlib seaborn scikit-image folium sentinelhub sentinelsat pystac-client fsspec dask
```


Open the notebooks
```bash
jupyter lab
# or
jupyter notebook
```
## Data sources and access

Common options to obtain Sentinel-2:
- Copernicus Open Access Hub (https://scihub.copernicus.eu/)
- ESA Sentinel Hub (commercial tiers + eval) — requires account and credentials
- AWS Public Datasets (Sentinel-2 on AWS S3) — access without credentials
- Google Earth Engine — requires GEE account and different workflow

Be explicit about which source you will use and follow their API usage and rate limits.

## Processing pipeline (high level)

1. Acquire imagery for the AOI and date range.
2. Preprocess:
   - Apply cloud and shadow masks (cloud probability or scene classification)
   - Reproject and resample to a common CRS/resolution
   - Clip to AOI
3. Calculate NDVI = (B08 - B04) / (B08 + B04)
4. Quality filter NDVI using mask and thresholding
5. Aggregate into seasonal composites (mean/median/percentile)
6. Produce time-series and spatial statistics (mean, trend, anomaly)
7. Visualize and export results (GeoTIFF, PNG, CSV)

## Outputs

- GeoTIFFs of NDVI (per-scene and seasonal composites)
- PNG/interactive maps for visualization
- Jupyter notebook HTML exports for reproducibility

## Contributing

Contributions are welcome. Suggested workflow:
1. Fork the repository
2. Create a feature branch (e.g., `feature/cloudmask-improvement`)
3. Add or update notebooks / docs
4. Open a pull request describing your changes

## Issues and support

Open an issue for:
- Problems running notebooks
- Reproducibility bugs
- Suggestions and enhancements


## Contact

Maintainer: subhalekhapandi-res  
