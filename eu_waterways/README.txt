# European Navigable Waterways Analysis

This project extracts navigable waterways across Europe using the OpenStreetMap Overpass API and converts them into geospatial datasets for analysis and visualization.

## Project Goals

- Extract navigable waterways from OpenStreetMap
- Convert raw OSM data into GeoJSON
- Build a geospatial dataset of European waterways
- Visualize waterways interactively

## Technologies

Python
Pandas
GeoPandas
Shapely
Overpass API
Streamlit

## Pipeline

1. Fetch waterways from Overpass API
2. Convert nodes to LineString geometries
3. Create GeoDataFrame
4. Export dataset to GeoJSON
5. Visualize waterways on an interactive map

## Output

The pipeline generates:
data/europe_navigable_waterways.geojson


## Example Map


## Run the project

Install dependencies
pip install -r requirements.txt


Run extraction
python src/fetch_waterways.py
