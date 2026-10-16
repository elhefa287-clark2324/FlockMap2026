# FlockMap2026 - Phoenix 50-mile camera awareness map

Live page: https://elhefa287-clark2324.github.io/FlockMap2026/

Passenger / voice use only. Do not touch or look at the page while driving.
Covers about 50 miles around Phoenix (lat 32.73 to 34.17, lon -112.67 to -111.47). Features: live location, 150 m voice-only alerts (fire once, re-arm after 300 m), mute toggle, clustering, drive quick links (Google Maps, current location as origin). The work address is stored only in your browser's localStorage.

Files: index.html (page), cameras.csv, cameras.kml (Google My Maps import), unlocated_sites.csv (published sites with no coordinates).

## Final counts: 1879 pins
By type: {'flock_alpr': 1612, 'other_alpr': 166, 'speed_camera': 31, 'photo_enforcement': 70}

## Per-source: input vs output
| Source | Input | Output pins | Notes |
|---|---|---|---|
| DeFlock public data (OSM-derived), ALPR | 1751 | 1751 | Flock + other ALPR, 50-mile bbox |
| OSM Overpass (speed/red-light nodes) | 26 | 26 | 2 Overpass tiles failed; coverage there is incomplete (33.33,-112.37,33.63,-112.07 and 33.93,-112.07,34.17,-111.77) for non-DeFlock OSM nodes |
| Mesa PhotoSafety official layer | 49 | 49 | merged copy of the same 49 deduped (<=25 m) |
| Peoria GIS Flock layer | 74 | 26 new + 48 already present | 48 were within 25 m of existing DeFlock Flock pins (dedupe) |
| Scottsdale city page (geocoded intersections) | 8 of 11 | 8 | 3 not geocoded; low confidence |
| Tempe city page (geocoded intersections) | 10 of 14 | 10 | 4 not geocoded; mobile units have no listed spots |
| Chandler city page (geocoded intersections) | 3 of 12 | 3 | 9 not geocoded |
| Phoenix photo-safety page (corridor start points) | 5 of 9 | 5 | 4 not geocoded; 8 rotating units have no locations |
| OpenStreetMap speed cameras (county-wide) | 26 | 1 new + 25 already present | 25 deduped within 25 m |
| Paradise Valley photo radar page | 6 | 0 | geocoding failed; listed in unlocated_sites.csv |
| merge_ready.csv total | 175 | 53 new + 122 deduped | 0 dropped for bbox, 0 missing |

Dedupe rule: same camera group within about 25 m of an existing pin. Ungeocoded sites (26 rows) are in unlocated_sites.csv. Programs with counts but no posted locations (Phoenix PD ~132, Glendale 58, Gilbert 42, Avondale 15, Queen Creek 47, Buckeye 72, Goodyear 33, MCSO 32 Litchfield Park) are not mapped. City labels on pins are approximate.

## Sources and attribution
- DeFlock (deflock.org) and OpenStreetMap contributors, ODbL: https://www.openstreetmap.org/copyright
- City of Mesa, City of Peoria public GIS layers; Tempe, Chandler, Scottsdale, Phoenix, Paradise Valley web pages (URL on each pin).
Crowdsourced and city-posted data may be incomplete or stale. Confidence label is on every pin.
