# FlockMap2026 - Phoenix 50-mile camera awareness map

Live page: https://elhefa287-clark2324.github.io/FlockMap2026/

Passenger / voice use only. Do not touch or look at the page while driving.
Covers about 50 miles around Phoenix (lat 32.73 to 34.17, lon -112.67 to -111.47). Features: live location, 150 m voice-only alerts (fire once, re-arm after 300 m), mute toggle, clustering, drive quick links (Google Maps, current location as origin). The work address is stored only in your browser's localStorage.

Files: index.html (page), cameras.csv, cameras.kml (Google My Maps import), unlocated_sites.csv (published sites with no coordinates).

## Final counts: 1902 pins
By type: Flock ALPR 1613, other ALPR 166, speed camera 39, city photo enforcement (speed/red-light) 84. (Mesa data does not separate speed from red-light, so Mesa is all photo enforcement.)

## Per-source: input vs output
| Source | Input | Output pins | Notes |
|---|---|---|---|
| DeFlock public data (OSM-derived), ALPR | 1751 | 1751 | Flock + other ALPR, 50-mile bbox, all kept |
| OSM Overpass speed/red-light/ALPR nodes | 27 | 27 | Overpass retry finished: all tiles loaded, 0 failed (retry added 1 node) |
| Mesa PhotoSafety official layer | 49 | 49 | all active records |
| Peoria GIS Flock layer | 74 | 26 new + 48 deduped | 48 within 25 m of existing DeFlock Flock pins |
| Scottsdale page (11 sites) | 11 | 8 earlier + 2 newly geocoded; 1 duplicate row | FLW at Greenway-Hayden listed twice on site |
| Tempe page (14 sites) | 14 | 10 earlier + 4 newly geocoded | 4 mobile units have no listed spots |
| Chandler page (12 sites) | 12 | 3 earlier + 9 newly geocoded | |
| Phoenix photo-safety page (9 corridors) | 9 | 5 earlier + 4 newly geocoded | corridor pins are low confidence (one end or midpoint); 8 rotating units have no locations |
| Paradise Valley photo radar page (6 sites) | 6 | 6 newly geocoded (some deduped vs OSM) | |
| OSM speed cameras county-wide | 26 | 1 new + 25 deduped | |
| Reddit sweep (r/mesaaz) | 3 specific | 1 new + 1 deduped vs existing Flock + 1 not geocodable | Judd Rd and Gantzel Rd (r/phoenix) has no shared OSM node; X sweep gave no specific locations |
| Total pins in page | | 1902 | page JS loads 1902 (browser-verified) |

Merged from merge_ready.csv / geocoding / social: dedupe rule is same camera group within 25 m of an existing pin. Newly geocoded intersections come from OpenStreetMap Overpass (nodes shared by both named roads); confidence medium for intersections, low for corridors. Pin position is the intersection, not the exact camera pole. Still not geocoded: none of the 26; Judd/Gantzel (social) not placed.

Programs with counts but no posted locations (Phoenix PD ~132, Glendale 58, Gilbert 42, Avondale 15, Queen Creek 47, Buckeye 72, Goodyear 33, MCSO 32 Litchfield Park) are not mapped. Tempe voted Oct 15, 2026 to ban ALPR use and Chandler's Flock cameras were reported removed (X posts), so mapped Flock pins in those cities may be stale. City labels on pins are approximate.

## Sources and attribution
- DeFlock (deflock.org) and OpenStreetMap contributors, ODbL: https://www.openstreetmap.org/copyright
- City of Mesa, City of Peoria public GIS layers; Tempe, Chandler, Scottsdale, Phoenix, Paradise Valley web pages (URL on each pin).
Crowdsourced and city-posted data may be incomplete or stale. Confidence label is on every pin.
