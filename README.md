[MeteoSwiss - Open Data](https://github.com/MeteoSwiss/opendata/blob/main/README.md) > [Understanding MeteoSwiss' Open Data products](https://github.com/MeteoSwiss/opendata/blob/main/README.md#understanding-meteoswiss-open-data-products) > E. Forecast Data

# E. Forecast Data
[Forecasting systems](https://www.meteoswiss.admin.ch/weather/warning-and-forecasting-systems.html) calculate future atmospheric conditions on the basis of measurement data and observations. MeteoSwiss uses these weather models to create weather forecasts and to enable it to issue weather warnings in the event of imminent hazards.

The following forecast data are available:

1. [Short-term forecast data](#1-short-term-forecast-data) :yellow_circle: *documentation upcoming*
2. [Numerical weather forecasting model data](#2-numerical-weather-forecasting-model-data) :yellow_circle: *documentation upcoming*
3. [Local forecast data](#3-local-forecast-data) :yellow_circle: *documentation upcoming*

<br>

---

## 1. Short-term forecast data
[Nowcasting](https://www.meteoswiss.admin.ch/weather/warning-and-forecasting-systems/nowcasting.html) involves high spatial and temporal resolution forecasts of weather developments for the next few minutes and up to a maximum of six hours ahead. MeteoSwiss uses these short-term forecasts to, among other things, predict thunderstorms, hail and heavy rainfall.

As MeteoSwiss is planning to replace the current 'INCA' nowcasting software, the following datasets are available from the start of our open data provision:
- **Precipitation (10min values): quantitative chain (based on CombiPrecip, RR)**
- **Wind, wind gust and wind direction (10min values)**
- *Relative sunshine duration* (10min values)
- **Total cloudiness (10min values)**

The following datsets will be provided next:
- **Snowfall (10min values): quantitative chain (based on CombiPrecip, RS)**
- ...
- ...

### 1.1. Data granularity, update frequency, format and volume
Data granularity is every 10min. Update frequency for the period 0h- +6h is specified per dataset in the table below.

Data format is [`NetCDF`](https://www.unidata.ucar.edu/software/netcdf).

| Dataset | Update frequency | Example data file | Productive version file name | Estimated volume per file (MB) |
|:----- | ----- |:----- |:----- | ----- |
| **Precipitation (10min values): quantitative chain (based on CombiPrecip, RR)** | every 10min | [RR_INCA_202106280700.nc](https://github.com/MeteoSwiss/publication-opendata-inca-data-nowcasting/blob/main/RR_INCA_202106280700.nc) | `ogd-nowcasting_RR-INCA_(date and time code).nc` | 1.7 |
| **Wind, wind gust and wind direction (10min values)** | every 10min | [...](...) | `ogd-nowcasting_(product name)_(date and time code).nc` | ... |
| *Relative sunshine duration* (10min values) | 10min | [SU_INCA_202106280700.nc](https://github.com/MeteoSwiss/publication-opendata-inca-data-nowcasting/blob/main/SU_INCA_202106280700.nc) | `ogd-nowcasting_SU-INCA_(date and time code).nc` | 6.4 |
| *Total cloudiness* (10min values) | 10min | [SU_INCA_202106280700.nc](https://github.com/MeteoSwiss/publication-opendata-inca-data-nowcasting/blob/main/SU_INCA_202106280700.nc) | `ogd-nowcasting_SU-INCA_(date and time code).nc` | 6.4 |
|       |       |       |       |       |
| **Snowfall (10min values): quantitative chain (based on CombiPrecip, RS)** | every 10min | [RS_INCA_202106280700.nc](https://github.com/MeteoSwiss/publication-opendata-inca-data-nowcasting/blob/main/RS_INCA_202106280700.nc) | `ogd-nowcasting_RS-INCA_(date and time code).nc` | 0.4 |

### 1.2. Parameter metadata
Parameter metadata is part of each NetCDF-File. See example data files in the table above.

<!-- ### Codes -->
<!-- ... -->

### 1.3. Coordinate system
The coordinate system is Swiss LV95 EPSG:2056.

### 1.4. Data visualisation
See e.g. MeteoSwiss' [...](...).

<br>

## 2. Numerical Weather Forecasting Model Data

MeteoSwiss uses two model setups based on the [ICON](https://www.icon-model.org/) model, **ICON-CH1-EPS** and **ICON-CH2-EPS**, to forecast the atmospheric state in Switzerland and its surroundings over a longer period than nowcasting, providing predictions for up to five days. Both models include
[ensemble data assimilation](https://www.meteoswiss.admin.ch/weather/warning-and-forecasting-systems/icon-forecasting-systems/ensemble-data-assimilation.html).

The documentation covers the following topics:
- [2.1 Model Specifications](#21-model-specifications)
- [2.2 Available Parameters](#22-available-parameters)
- [2.3 Accessing Forecast Data](#23-accessing-forecast-data)
- [2.4 3D Grid Structure and Representation](#24-3d-grid-structure-and-representation)
- [2.5 Example Notebooks: From Retrieval to Visualization](#25-example-notebooks-from-retrieval-to-visualization)
- [2.6 Retrieving Forecasts via REST API](#26-retrieving-forecasts-via-rest-api)
- [2.7 Accessing Static Grid Information: Height, Longitude, and Latitude](#27-accessing-static-grid-information-height-longitude-and-latitude)
- [2.8 Reading Forecast Files Using ecCodes](#28-reading-forecast-files-using-eccodes)

### 2.1 Model Specifications

| **Attributes**| **ICON-CH1-EPS** | **ICON-CH2-EPS**|
|-----------|------------------|-----------------|
| Collection |[ch.meteoschweiz.ogd-forecasting-icon-ch1](https://data.geo.admin.ch/browser/#/collections/ch.meteoschweiz.ogd-forecasting-icon-ch1?.language=en) | [ch.meteoschweiz.ogd-forecasting-icon-ch2](https://data.geo.admin.ch/browser/#/collections/ch.meteoschweiz.ogd-forecasting-icon-ch2?.language=en) |
| Horizontal Grid Size | approx. 1 km | approx. 2.1 km |
| Ensemble Members | 11 | 21 |
| Forecast Period | 33 h | 120 h |
| Grid | Native icosahedral | Native icosahedral |
| Temporal Output Resolution |  1 h | 1 h |
| New Model Run (Initialization) | every 3 h | every 6 h |
| Output Data Format | GRIB edition 2 | GRIB edition 2 |


### 2.2 Available Parameters

### 🚧  **Temporary Notice Work in Progress**

Users can find information about available parameters, including metadata about height, longitude and latitude, in the collection level assets of the above collections.

#### 2.2.1 Parameter Metadata

A complete set of metadata describing the corresponding parameter is encoded in each record of the GRIB files.
Please refer to [section 2.7.2 Decoding GRIB Files with ecCodes](#272-decoding-grib-files-with-eccodes)

### 2.3 Accessing Forecast Data

The data provided in the two collections described in the [Model Specification table](#21-model-specifications) is accessible for **24 hours**.
Data older than this is no longer available.

> ⚠️ **WARNING**: Data located at the boundary of the spatial domain may be random.

#### 2.3.1 Forecast Data Volume

The following tables summarize the volume of the different forecast files for **ICON-CH1-EPS** and **ICON-CH2-EPS**.

**ICON-CH1-EPS Data Volume**
| | Single-Level Files| Multi-Level Files|
|-----------|------------------|-----------------|
| Deterministic| 199.0 Bytes - 2.2 MiB| 19.7 - 177.4 MiB|
| Perturbed | 1.9 KiB - 22.4 MiB | 197.1 MiB - 1.7 GiB |


**ICON-CH2-EPS Data Volume**
| | Single-Level Files| Multi-Level Files|
|-----------|------------------|-----------------|
| Deterministic|  175.0 Bytes - 564.7 KiB| 4.9 MiB - 43.9 MiB|
| Perturbed | 3.4 KiB - 11 MiB | 97.5 MiB - 877.5 MiB |


### 2.4 3D Grid Structure and Representation
The model data is structured on both a horizontal and vertical grid. While some parameters extend across the entire three-dimensional grid, others are only available at specific vertical levels.
Parameters are classified as either **single-level** or **multi-level**:
- **Single-level parameters** contain data at a specific vertical level.
- **Multi-level parameters** extend across multiple vertical layers.

For example, vertical velocity is stored at multiple vertical levels, while the two-meter temperature is available only at a single vertical level.


#### 2.4.1 Vertical Grid

The vertical grid above the surface is a height-based coordinate system that describes terrain-following model levels. The closer the levels are to
the surface, the narrower the layers they define, as shown in the image below. The model levels gradually change into levels of constant height as the distance from the surface increases.
Each grid box is delimmited at the top and bottom by so-called half levels of the grid, while the full levels are aligned with the center of the grid box.
The vertical grid uses a Lorenz-type staggering, meaning that some parameters are defined at full levels and others, e.g. the vertical velocity `W`, at full levels.
There are 81 discrete half levels and 80 full levels in our data. The levels are numbered from top to bottom.

<div align=center>
<img src="Images/VerticalLayers.png" width="550"/>

Illustration of ICON's vertical levels, Working with the ICON Model 2024, Figure 3.2
</div>

In addition to the vertical grid above the surface (half and full levels), there is also a grid below the land surface to describe parameters as the soil temperature for example.
In the provided model data, some variables are also defined on a surface (e.g. total precipitation), or at a specific height above ground (e.g. temperature at 2m).
To determine the vertical positioning of a parameter and the units corresponding to the vertical surface type, inspect the GRIB2 key `typeOfLevel`:

* `generalVertical`: half levels (-)

* `generalVerticalLayer`: full levels (-)

* `depthBelowLandLayer`: depth below surface (m)

* `surface`: ground or water surface (-)

* `heightAboveGround`: specific height above ground (m)


Most parameters are stored on full vertical levels, while some — such as the vertical velocity `W` — are stored on half (staggered) levels.
To determine the vertical positioning of a parameter, inspect the GRIB2 key `typeOfLevel`:

* `generalVertical` indicates half levels

* `generalVerticalLayer` indicates full levels

For details on reading GRIB key values, see the section [Section 2.7.4 Decoding GRIB Files with ecCodes](#274-decoding-grib-files-with-eccodes).

For more detailed information on the vertical grid, read section 3.4 in [Working with the ICON Model](https://www.dwd.de/DE/leistungen/nwv_icon_tutorial/pdf_einzelbaende/icon_tutorial2024.pdf?__blob=publicationFile&v=3).


#### 2.4.2 Horizontal Grid

The horizontal grid of the ICON-CH1-EPS and ICON-CH2-EPS models is based on a native icosahedral grid used by the ICON model (illustration below).

<div align=center>
<img src="Images/IcosahedralGrid.png" width="300"/>

Illustration of the ICON grid structure, Working with the ICON Model, Figure 2.1
</div>

Since the provided data is defined on the native grid, the horizontal grid points correspond to the **center of the circumcircle of each triangle** and **not** to the vertices.
Therefore, the longitude and latitude information corresponds to the middle of each triangle. For more detailed information on
the horizontal grid, read section 2.1 in [Working with the ICON Model](https://www.dwd.de/DE/leistungen/nwv_icon_tutorial/pdf_einzelbaende/icon_tutorial2024.pdf?__blob=publicationFile&v=3).

### 2.5 Retrieving, Handling, and Visualizing Forecasts using Python

We provide a Python library to access the data and perform some processing tasks. You can find some simple examples on how to get
and use the model forecast data in the form of Jupyter notebooks:

<p>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/38/Jupyter_logo.svg" style="height: 52px; vertical-align: middle; padding-right: 20px;">
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://github.com/MeteoSwiss/opendata-nwp-demos">
    <img src="https://img.shields.io/badge/GitHub-Repository-blue?logo=github" style="height: 22px; vertical-align: middle;">
  </a>
</p>

### 2.6 Retrieving Forecasts via REST API

If users prefer not to use the provided Python library to load the data, they can retrieve datasets directly via the [REST API](https://data.geo.admin.ch/api/stac/static/spec/v1/apitransactional.html#tag/Data/operation/getAsset) by following the step-by-step instructions in this section to obtain forecast data for specific models, parameters, and other customizable variables.

#### 2.6.1 Submitting a POST Request

Filtering and querying forecast data must be done using a **POST** request. To retrieve a forecast, use a tool like `curl` and send the request to the API endpoint:
```
curl -X POST "https://data.geo.admin.ch/api/stac/v1/search" \
     -H "Content-Type: application/json" \
     -d '{
            "collections": [
                "ch.meteoschweiz.ogd-forecasting-icon-ch2"
            ],
            "forecast:reference_datetime": "2025-03-12T12:00:00Z",
            "forecast:variable": "TOT_PREC",
            "forecast:perturbed": false,
            "forecast:horizon": "P0DT00H00M00S"
        }'
```

Each parameter in the request body serves the following purpose:
- `collections`: Defines the forecast model to retrieve (`ch.meteoschweiz.ogd-forecasting-icon-ch1` for ICON-CH1-EPS and `ch.meteoschweiz.ogd-forecasting-icon-ch2` for ICON-CH2-EPS).
- `forecast:reference_datetime`: Specifies the desired forecast initialization time (e.g., `2025-03-12T12:00:00Z`).
- `forecast:variable`: Indicates the meteorological parameter of interest (`TOT_PREC` for total precipitation, for example).
- `forecast:perturbed`: Boolean flag determining if the request is for deterministic (`false`) or ensemble (`true`) data.
- `forecast:horizon`: Defines the forecast lead time to retrieve in ISO 8601 duration format (`P0DT00H00M00S` for data at +0h lead time, i.e. initialization).

#### 2.6.2 Downloading the Forecast Data
Upon a successful request, the response will contain a dictionary of metadata, including forecast file links under the `assets` key. Locate the `href` field containing the pre-signed URL.
Download the GRIB file containing the forecast data using the following command:
```
wget -O <desired_filename> “<pre-signed URL>”
```
Once downloaded, proceed with decoding the GRIB file. A brief explanation on decoding GRIB can be found in [Section 2.7.4 Decoding GRIB Files with ecCodes](#274-decoding-grib-files-with-eccodes).

### 2.7 Accessing Static Grid Information: Height, Longitude, and Latitude

Besides the current forecast files, each catalog contains two static files. They store constant information about the height of the half levels (HHL) in the vertical grid and
the center point coordinates of each triangle on the horizontal grid.

> ❗ **NOTE**: The forecast GRIB files contain no information on height, longitude and latitude. They have to be determined via the static vertical and horizontal grid parameter files.

#### 2.7.1 Accessing Vertical Grid Parameters

In the static vertical file, the heights of the half levels of the vertical grid are provided in meters above see level. In order to associate a value from a data file (for a given parameter) to a height in meters above sea level, follow the steps below:

1. Submit a GET request specifying the collection you want to retrieve the static vertical files from (e.g., `ch.meteoschweiz.ogd-forecasting-icon-ch1` for ICON-CH1-EPS):
```
curl -X GET https://data.geo.admin.ch/api/stac/v1/collections/ch.meteoschweiz.ogd-forecasting-icon-ch1/assets
```
2. Locate under `assets` in `id: vertical_constants_icon-ch1-eps.grib2` the `href` field and copy the pre-signed URL.
3. Download the file with:
```
wget -O <desired_filename> “<pre-signed URL>”
```
4. Once the static GRIB file is downloaded, verify that the `uuidOfHGrid` (Universally Unique Identifier) key in the data file matches the one in the HHL file.
5. Retrieve the value for the `level` key and inspect the `typeOfLevel` key by listing the GRIB messages:
    - **generalVertical**: The value of `level` corresponds to a half level in the HHL file. For each level (i.e., each GRIB message), the variable `h` provides the height in meters above sea level for every grid point.
    - **generalVerticalLayer**: The `level` value corresponds to a full level. To obtain the height in meters above sea level, average the heights of the two surrounding half levels (above and below).
    - **Other types of level**: These are usually specified directly in meters and are self-explanatory.

#### 2.7.2 Accessing Horizontal Grid Parameters

> ❗ **NOTE**: We recommend inexperienced GRIB file users to take a look at the provided [Jupyter Notebooks](https://github.com/MeteoSwiss/opendata-nwp-demos). The data retrieval with the Python API includes fetching longitude and latitude.

The static horizontal file stores the longitude and latitude of the center points of each triangle in the horizontal grid. To retrieve this information, follow the steps below:

1. Submit a GET request specifying the collection you want to download the static horizontal files from (eg. `ch.meteoschweiz.ogd-forecasting-icon-ch1` for ICON-CH1-EPS).
```
curl -X GET https://data.geo.admin.ch/api/stac/v1/collections/ch.meteoschweiz.ogd-forecasting-icon-ch1/assets
```
2. Locate under `assets` in `id: horizontal_constants_icon-ch1-eps.grib2` the `href` field and copy the pre-signed URL.
3. Download the file with:
```
wget -O <desired_filename> “<pre-signed URL>”
```
4. Once the static GRIB file is downloaded, ensure that the `uuidOfHGrid` (Universally Unique Identifier) key in the data file matches the one in the static horizontal file.

### 2.8 Reading Forecast Files Using ecCodes

Once you have the desired GRIB files, you need a tool to read them. We recommend installing [ecCodes](https://confluence.ecmwf.int/display/UDOC/How+to+install+ecCodes+with+Python+bindings+in+conda+-+ecCodes+FAQ) from ECMWF.

#### 2.8.1 Installing ecCodes and COSMO definitions

By default, a GRIB file shows the short names defined by ECMWF. However, the ICON model has its own definitions.
In order to install them, apply the steps below.

- Clone the GitHub repository [eccodes-cosmo-resources](https://github.com/COSMO-ORG/eccodes-cosmo-resources) into folder `<name_of_your_folder>`.
- Clone the GitHub repository [ecmwf/eccodes](https://github.com/ecmwf/eccodes/) into the same folder `<name_of_your_folder>`.

> ⚠️ **WARNING**:
> Make sure both repositories are in the same folder and run on the same version.

Finally, execute the following command to set the GRIB definition path:


```
export GRIB_DEFINITION_PATH=<name_of_your_folder>/eccodes-cosmo-recources/definitions:<name_of_your_folder>r/eccodes/definitions
```

> ❗ **NOTE**:
> This command must be executed every time you start a new terminal session.

#### 2.8.2 Decoding GRIB Files with ecCodes

This section provides a brief introduction to decoding GRIB files using **ecCodes**.
For more details, refer to the [ECMWF ecCodes documentation](https://events.ecmwf.int/event/363/contributions/4110/attachments/2346/4098/intro_grib_decoding_2023-10-31.pdf).

Use the following commands to
- Check ecCodes installation details:
```
codes_info
```

- List all the GRIB messages in a file:
```
grib_ls filename.grib
```

- Filter GRIB messages based on key-value conditions:
```
grib_ls -w key1=value1,key2=value2 filename.grib
```

- Specify a list of keys to be printed:
```
grib_ls -p key1,key2 filename.grib
```

- Get a detailed view of the content of all GRIB messages:
```
grib_dump filename.grib
```
- Get a detailed view of GRIB messages with filters:
```
grib_dump -w key1=value1,key2=value2 filename.grib
```

> ⚠️ **WARNING**:
> Some variables in the ICON model are not included in the WMO standard definitions but are instead defined in ICON's local GRIB definitions. If a variable is missing, users should check the [eccodes-cosmo-resources files](https://github.com/COSMO-ORG/eccodes-cosmo-resources/blob/master/definitions/grib2/localConcepts/edzw/shortName.def).

<br>

## 3. Local forecast data
...

...

### Data granularity, update frequency, format and volume
There are files of [data granularity](https://github.com/MeteoSwiss/opendata-download?tab=readme-ov-file#data-granularity) `...`, `...`, `...`, `...` *and [update frequency](https://github.com/MeteoSwiss/opendata-download/blob/main/README.md#update-frequency) hourly (`now`), daily (`recent`) or yearly (`historical`) for each station*.

Data format is [`CSV`](https://github.com/MeteoSwiss/opendata-download?tab=readme-ov-file#column-separators-decimal-dividers-and-missing-values) with an estimated volume of ... MB per file.

See example data files: [`...`](...).

### Parameter metadata
See example parameter metadata files of [data granularity](https://github.com/MeteoSwiss/opendata-download?tab=readme-ov-file#data-granularity): [`...`](...) and [`...`](...).

<!-- ### Codes -->
<!-- ... -->

### Station metadata
See example [station metadata file](...).

### Data visualisation
See e.g. MeteoSwiss' [...](...).

<br>
