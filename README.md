# RunTime Dive Systems — Lake Washington DPV Planner

A single-page, client-side (no server, no API key) wreck waypoint and DPV route planner for Lake Washington. The app uses Leaflet, OpenStreetMap/CARTO basemaps, NOAA/NCEI bathymetric BAG shaded relief, optional WA Ecology contours, and Archie's publicly shared wreck waypoint catalog.

## Use locally

Download `index.html`, open it in a browser with internet access. Map tiles, Leaflet and the remote wreck catalog need internet access; saved route calculations still work when map tiles are unavailable. Or serve a local folder: `python3 -m http.server 8000`, then open `http://localhost:8000`.

## GitHub Pages deployment

1. Create a **new public GitHub repository** `Jdd227/dpvplanner`. Do not overwrite the existing gas-label application.
2. Upload the `index.html`, `CNAME`, `.nojekyll` and `README.md` files from this directory into the root of `main`, or push them using Git.
3. Open **Settings → Pages**, set **Deploy from a branch → main → /(root)**, and save.
4. In **Settings → Pages → Custom domain**, set `dpvplanner.runtimedivesystems.com` and save. Configure the domain on GitHub before changing DNS, as recommended by GitHub.
5. At the DNS host controlling `runtimedivesystems.com`, create **CNAME** with **Host/Name** `dpvplanner`, **Value/Target** `jdd227.github.io` (some providers require `jdd227.github.io.`). Keep the record DNS-only while validating the GitHub Pages custom-domain certificate if using a DNS proxy. Return to the Pages settings to enable **Enforce HTTPS** when it becomes available.
6. Check https://dpvplanner.runtimedivesystems.com (not guaranteed live until steps above are complete).

GitHub Pages serves HTTPS but it does not itself manage your domain's DNS. The included `CNAME` file configures the site name; it does not publish DNS automatically.

## Map data, behavior, limitations

- **Lake Washington wrecks**: Archisgore dataset, https://github.com/archisgore/dive-site-markers (`markers.json`). Marker depth values in meters are displayed in feet. Default seven wreck markers are included in the HTML as an offline fallback. Full 287 marker inventory is fetched live from GitHub and cached in browser localStorage when possible.
- **NOAA shaded relief**: https://tiles.arcgis.com/tiles/C8EMgrsFcRFL6LrL/arcgis/rest/services/bag_hillshades/MapServer at zooms up to 14; zooms 15+ request imagery from https://gis.ngdc.noaa.gov/arcgis/rest/services/bag_hillshades_subsets/ImageServer. Underlying NOAA survey H11810 is 2008 vintage. Coverage will vary with zoom and available data; source response times vary.
- **Bathymetric contour overlay**: https://gis.ecology.wa.gov/serverext/rest/services/Authoritative/ECY/MapServer (layer 3), which provides depth contours only for selected Washington freshwater lakes. There may be no contour coverage in some areas; the NOAA shaded relief is the primary bathymetric view.
- **Map backend**: Leaflet 1.9.4 loaded from unpkg CDN. Basemap dark CARTO; alternate light OpenStreetMap. No Google Maps API and no provider API keys. An external internet connection is still needed for tiles.
- **Distances**: horizontal WGS84 great-circle approximation, in feet. True bearings, not magnetic. Estimates exclude depth, search time, currents, site obstructions, navigation errors, and no-stop/decompression concerns. Survey depth and GPS do not certify an unobstructed underwater corridor.
- **State**: routes stored in browser localStorage only, not synced across devices. Export route GPX and leg CSV before clearing browser history.

## Smoke test

Check that the initial Diamond Girl → Dawn leg is approximately **1,069 ft at 112° true**, and approximately **6:07** at 175 ft/min. Verify both bathymetric overlays show requests without an API key. Bathymetry itself relies on remotely served imagery: live availability cannot be guaranteed from local static source inspection.

## Licensing

Archisgore marker database: GPL-3.0 per source repository; preserve source attribution and review downstream redistribution obligations. Leaflet, OpenStreetMap and other map providers have their own license/attribution/usage requirements. NOAA data is not for navigation.
