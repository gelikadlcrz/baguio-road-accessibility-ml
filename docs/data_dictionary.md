# Data dictionary — initial validation inputs

This dictionary describes fields observed in the current source files. It does not define authoritative data provenance or certify individual records.

## 1. Barangay polygons — `Baguio_Barangaysv2.geojson`

| Field | Interpretation in QA |
| --- | --- |
| `adm4_psgc` | Barangay administrative code; used for missing/duplicate checks |
| `adm4_en` | Barangay name for map labeling and descriptive reporting |
| `area_km2` | Supplied area field; may be rounded; **not** used as an area calculation source |
| `geometry` | Barangay polygon geometry and study-area union |

Other supplied administrative metadata is preserved in the original file.

## 2. Road network — `baguio_roads_full.graphml`

Graph structure is a directed multigraph with node IDs and potentially parallel directed edges.

| Field | Interpretation in QA |
| --- | --- |
| Node `x`, `y` | Node coordinates in graph CRS |
| Edge `length` | Edge length in meters, as stored in source GraphML |
| Edge `geometry` | Optional serialized road linestring; if absent, straight node-to-node geometry is used **for diagnostic mapping only** |
| Graph `crs` | Network coordinate reference system |
| Graph edge IDs `(u, v, key)` | Used to check hospital records referencing network edges |

Graph node and edge attributes are initially read as strings by NetworkX and explicitly converted where appropriate.

## 3. Landslide susceptibility — `geoson_query.geojson`

| Field | Interpretation in QA |
| --- | --- |
| `OBJECTID` | Source feature identifier |
| `LndslideSusc` | Categorical susceptibility code; observed values `LL`, `ML`, `HL`, `VHL`, and `DF` |
| `geometry` | Susceptibility polygon or multipolygon |

The category `DF` is retained as an unmapped code pending confirmation of its official meaning. Observed labels are not assumed to represent landslide-event records or road closures. Calculated area by class is the *sum of polygon–city intersections*, which can double-count if features overlap.

## 4. Hospital access points — `hospital_access_points_graphml_compatible.csv`

| Field | Interpretation in QA |
| --- | --- |
| `entrance_id` | Record-level entrance identifier |
| `facility_code`, `hospital_name` | Hospital identifiers and descriptive name |
| `entrance_latitude`, `entrance_longitude` | Preliminary WGS 84 point coordinates |
| `nearest_edge_u`, `nearest_edge_v`, `nearest_edge_key` | Existing graph-edge reference to be verified |
| `nearest_edge_distance_m` | Previously reported nearest-edge distance; audited against geometry |
| `nearest_graph_node_id` | Existing graph-node reference to be verified |
| `inside_graph_bbox`, `network_coverage_status` | Supplied coverage indicators; recomputed where possible |
| `gate_verified` | Preliminary verification status; not proof of legal vehicular access |

Hospital rows may contain missing optional metadata while collection is ongoing. A **200 m** nearest-road threshold is used only as an exploratory QA screening rule, not as an acceptance standard.
