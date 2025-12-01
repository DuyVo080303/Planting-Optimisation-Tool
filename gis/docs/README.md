# Overview
This module provides a lightweight interface for extracting geospatial attributes from coordinates.
It is designed to support the Planting Optimisation Tool by converting longitude/latitude inputs into meaningful environmental data such as elevation, rainfall, temperature, soil pH, and landcover.
```
gis/
│
├── assets/
│   └── gadm41_TLS_3.json        # Administrative boundary data for Timor-Leste
│
├── config/
│   └── settings.py              # Environment variable loading (service account, key paths)
│
├── core/
│   ├── extract_data.py          # Functions to fetch rainfall, temp, pH, elevation, landcover
│   ├── farm_profile.py          # Builds a farm profile from coordinates
│   ├── gee_client.py            # Earth Engine initialization + client handling
│   └── geometry_parser.py       # Parsers for point, multipoint, polygon inputs
|___docs/
|   └── README.md                # folder structure, update works
│
├── keys/
│   └── <service-account>.json   # Local service account key (ignored by Git)
│
├── .env                         # GEE_SERVICE_ACCOUNT and GEE_KEY_PATH variables
└── tests/
    └──test_gis.py               # unit tests for all gis functions

```

# Function Documentation 
**get_rainfall()**
Returns the 5-year (2020 - 2024) average annual rainfall (mm) at a given point in Timor-Leste from PO's Dataset.

**get_temperature()**
Returns the 5-year (2020 - 2024) average land surface temperature (°C) at a given point in Timor-Leste from PO's Dataset.

**get_ph()**
Returns the soil pH value at a given point, based on a soil pH polygon layer from PO's Datasetư

**get_elevation()**
Returns the elevation (m) at a given point, from a DEM provided by the PO.

**get_landcover()**
Returns the landcover class for the farm containing the point, including "forest" or "non_forest".

**get_NVDI()**
turns the mean NDVI (Normalised Difference Vegetation Index, -1 to 1) at a point for the year 2025 from Modis Dataset.