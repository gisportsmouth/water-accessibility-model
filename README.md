# water-accessibility-model

Analyse household access to old and new water sources using OpenStreetMap paths, terrain models, walking-time estimation and load-carriage energy metrics.

## Introduction

This project estimates the benefits of installing new rural water sources by calculating changes in:

- Walking distance
- Travel time
- Energy expenditure (LCDA calories)

For each household, accessibility is calculated along the OpenStreetMap walking network while accounting for terrain elevation and slope.

## Requirements

The input is a folder containing one or more CSV files. Each CSV represents a village survey and must contain the following columns:

```python
['Latitude', 'Longitude', 'Description']
```

Requirements:

- Coordinates must be in WGS84 (`EPSG:4326`).
- `Description` must contain one of the following values:
  - `Household Locations`
  - `Old Water Source`
  - `Old Water Source 1`, `Old Water Source 2`, ...
  - `WC Source`
  - `WC Source 1`, `WC Source 2`, ...

Each village must contain:

- At least one household
- At least one old water source
- At least one proposed (`WC Source`) water source

## Python Environment

All required packages are listed in `environment.yml`.

A Conda-based distribution such as Miniforge is recommended.

Create the environment using:

```bash
conda env create -n village_access -f environment.yml
```

Activate it with:

```bash
conda activate village_access
```

## Running the Code

Open the supplied Jupyter Notebook and run all cells.

When prompted, provide:

- The folder containing the survey CSV files

## Outputs

The model creates the following outputs:

```text
Processed GPS Results/
├── cache/
│   ├── dem.tif
│   ├── dem_utm.tif
│   ├── slope.tif
│   ├── geofabrik_index.geojson
│   ├── uganda.osm.pbf
│   └── paths_<village_name>.parquet
├── raw data/
│   ├── accessibility_report.gpkg
│   └── villages_raw_statistics.csv
└── report/
    ├── report_before_after_metrics.png
    ├── report_village_ranking.png
    ├── village_<village_name>_map.png
    ├── village_<village_name>_metrics.png
    └── water_access_report.pdf
```

### GeoPackage Layers

`accessibility_report.gpkg` contains:

- `accessibility`
- `paths`
- `old_sources`
- `new_sources`

## Final Output

The primary deliverable is:

```text
water_access_report.pdf
```

This report summarises accessibility improvements for each village, including changes in distance travelled, travel time, and energy expenditure following installation of the proposed water sources.
