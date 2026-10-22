# RunTime DPV Planner (v5 rebuild)

Deploy the included `index.html` on GitHub Pages (`main` / root). The `CNAME` matches the existing DNS configuration. Do not change GoDaddy DNS.

### Data and map
- Wreck markers: Archie’s live JSON file at `archisgore/dive-site-markers` (plus a seven-wreck fallback).
- Bathymetry: Archie’s **exact Lake Washington** TMS PNG tiles, repository `archisgore/lake-washington-bathymetry` (CC0). Leaflet `tms: true` is necessary because the tiles are Y-inverted relative to XYZ.
- Street basemap: public OpenStreetMap tiles (attribution present). Archie’s Google streets tiles are not embedded/reused; they require a licensed API key for independent Google Maps use.
- Front end: Leaflet and plain HTML/CSS/JS. No API keys or build.

### Controls
Click a marker or a wreck in the left list to see its details. Add to route. Turn Draw route ON to select a sequence of wrecks or place a custom waypoint by clicking open water. The route line, segment distance, bearing (TRUE) and travel time appear instantly. Routes can be saved locally or exported to GPX and CSV.

### Safety/data
Archie’s markers and reported depths are not verified positions. Route distances are horizontal and times exclude depth changes, currents, hazards, and search time. Does not replace dive or gas planning.
