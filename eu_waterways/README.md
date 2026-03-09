# Europe Navigable Waterways

Fetches rivers and canals across 24 European countries from OpenStreetMap via the Overpass API, saves them as GeoJSON, and renders an interactive map with Folium.

[View interactive map](https://<your-username>.github.io/<repo-name>/eu_waterways/europe_navigable_waterways_map.html)

## What it does

Queries each country for `waterway=river|canal` ways. It first tries a strict filter requiring `boat=yes|permissive`; if that returns nothing (common where boat access isn't explicitly tagged in OSM), it falls back to all rivers and canals. Results are merged into a single GeoDataFrame and exported.

## Output

- `data/europe_navigable_waterways.geojson` — all ways with `country`, `name`, `waterway`, and `boat` fields
- `europe_navigable_waterways_map.html` — interactive Folium map on a dark basemap; rivers in orange, canals in blue

## Countries covered

Austria, Bulgaria, Switzerland, Czechia, Germany, Estonia, Spain, Finland, France, Croatia, Hungary, Ireland, Italy, Lithuania, Luxembourg, Moldova, Netherlands, Poland, Portugal, Romania, Serbia, Sweden, Slovakia, United Kingdom.

## Install

```bash
pip install geopandas folium requests shapely tqdm
```

## Usage

Run the notebook top to bottom. The API test cell at the top confirms the Overpass endpoint is reachable before kicking off the full loop.

The fetch loop sleeps 10 seconds between countries to stay under the Overpass rate limit. Large countries (Germany, France, UK) can still trigger a 429 — the query function backs off and retries up to 3 times automatically.

## Notes

- OSM tagging is inconsistent. Many navigable waterways don't have `boat=yes`, which is why the fallback query exists.
- The Overpass API is a public service — avoid hammering it. If you need to re-run, consider caching the raw responses first.
