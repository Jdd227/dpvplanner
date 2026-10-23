# RunTime DPV Planner V7

Based on the working V6 map and Archie’s wreck markers and bathymetry. Adds a custom shore-entry or boat-drop starting point.

## Set a starting point
1. Open the Route tab.
2. Choose **+ Shore entry** or **+ Boat drop**.
3. Enter a name (optional).
4. Click/tap the map to place the start, OR enter latitude and longitude and select **Use GPS coordinates**.
5. The marker becomes waypoint 1 and existing wrecks move after it. To relocate it, select **Move** beside waypoint 1. Rename it with the inline name field.
6. Save route or export GPX/CSV as usual.

The map toolbar **+ Start point** is a shortcut to shore-entry placement. Shore and boat starts render as distinct S/B markers. A new start replaces an existing shore/boat start rather than adding duplicates.

## Deploy
Replace only `index.html` in `Jdd227/dpvplanner` on the main branch and commit. Do not alter CNAME or GitHub Pages settings. The included CNAME is provided for clean new deployments, but is not needed for this update.

Map/dataset sources and attributions: Archie’s `archisgore/ScubaDiveMap`, `archisgore/lake-washington-bathymetry` (CC0) and `archisgore/dive-site-markers` (GPLv3). Historical wreck coordinates and bathymetry are not verified underwater navigation fixes.
