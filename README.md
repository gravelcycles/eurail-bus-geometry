# European bus display geometry

Immutable display derivatives for the optional [Euro Rail atlas bus layer](https://gravelcycles.github.io/eurail-atlas/).

Native timetable map/search data lives in [eurail-bus-data](https://github.com/gravelcycles/eurail-bus-data); detailed calls live in [eurail-bus-details](https://github.com/gravelcycles/eurail-bus-details).

Each display product binds an exact native manifest, dated source archives, source licences and credits. Use its manifest/catalogue for attribution and limitations. Repository metadata does not replace the individual source terms.

Generalized segments represent a display network, not boarding stops, through journeys, physical bus counts or confirmed operating roads. Provider paths, publisher stop chains, schematic links and reviewed road-routing estimates keep their separate evidence classifications. Fine selected-route geometry is loaded only on demand.

Raw archives, private databases, access parameters and private build witnesses are excluded. Coverage is partial; publication does not establish complete-country or 95% European coverage.

## Network tiles (`network/<bus manifest sha256>/`)

Location-keyed display tiles for the bus explorer, built by `scripts/build_bus_network_tiles.py` in the atlas source from the exact native map packets of one bus manifest. Each published path is snapped to a per-level grid and stored once per tile with the scheduled trips that use it, so a city view loads a few small files instead of hundreds of identity-ordered packets.

- `catalogue.json.gz` binds the bus manifest hash, dates, sources (with each publisher's licence and credit), levels and index descriptors.
- `index/<tile zoom>/<x>-<y>.json.gz` lists tile sizes and SHA-256 hashes.
- `tiles/<tile zoom>/<x>/<y>.json.gz`: broad levels (2, 4, 6, 8) carry a legend band per date and per mean day for each source/mode/country profile; level 10 carries exact pattern membership, line labels and end-stop names so a click can list every recorded line through a point.

Trip sums are scheduled source trips per source and are never added across sources. Segments are publisher paths or straight stop chains; they do not establish roads, boarding points or physical bus counts. Each source's own licence and attribution applies to its lines, names and paths.
