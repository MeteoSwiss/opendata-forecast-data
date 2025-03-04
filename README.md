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

## 2. Numerical weather forecasting model data

MeteoSwiss uses two models, **ICON-CH1-EPS** and **ICON-CH2-EPS**, to forecast atmospheric changes in Switzerland and its surroundings over a longer period than nowcasting, providing predictions for up to five days. Both models include
[ensemble data assimilation](https://www.meteoswiss.admin.ch/weather/warning-and-forecasting-systems/icon-forecasting-systems/ensemble-data-assimilation.html).

### 2.1 Model specification

| **Attributes**| **ICON-CH1-EPS** | **ICON-CH2-EPS**|
|-----------|------------------|-----------------|
| Collection |[ch.meteoschweiz.ogd-forecasting-icon-ch1](https://sys-data.int.bgdi.ch/browser/#/collections/ch.meteoschweiz.ogd-forecasting-icon-ch1?.language=en) | [ch.meteoschweiz.ogd-forecasting-icon-ch2](https://sys-data.int.bgdi.ch/browser/#/collections/ch.meteoschweiz.ogd-forecasting-icon-ch2?.language=en) |
| Horizontal Grid Size | 1 km | 2.1 km |
| Ensemble Members | 11 | 21 |
| Forecast Period | 33 h | 120 h |
| Grid | Native icosahedral | Native icosahedral |
| Temporal Resolution |  1 h | 1 h |
| Model Run Interval | every 3 h | every 6 h |
| Format | GRIB edition 2 | GRIB edition 2 |


### 2.2 Available parameters

Users can find information about available parameters, including metadata, in the collection level assets of the above collections.

#### 2.2.1 Parameter metadata

The parameter metadata is part of each GRIB file.


### 2.3 Accessing forecast data

The user can access the forecast model data from the last 24 hours. Data older than 24 hours is no longer available. The data in each collection is described in the table above.


### 2.4 3D grid structure and representation

The ICON model is an unstructured native grid. It distingiushes between a horizontal and vertical grid structure.
Combining the two structures results in a 3 dimensional grid over Switzerland and
its surroundings. We differentiate between single and multi level parameters where the
former describes a parameter on a single vertical level and the latter a parameter on
the entire 3-dimensional grid. For example the vertical velocity is stored in multiple vertical
levels, whereas the two-meter-temperature has only information in one vertical level.

#### 2.4.1 Vertical grid

The vertical grid is a height based coordinate system that follows the terrain. It is divided into multiple layers. The closer the layer is to
the surface, the narrower the layers are, as one can see in the picture below.
Note that the so-called *half levels* correspond to the horizontal grid points, while the *full levels* describe an avarages value
over the whole vertical layer. In total there exists 81 discrete half levels.

<div align=center>
<img src="Images/VerticalLayers.png" width="550"/>

Illustration of ICON's vertical levels, Working with the ICON Model 2024, Figure 3.2
</div>

All parameters have their information on full levels, except for the vertical velocity W. W is stored on half levels and therefore called staggered.
This means that the value is exact in this point
and not an avarage value over a layer stored in one point like the full levels. For more detailed information on the vertical grid, read section 3.4 in [Working with the ICON Model](https://www.dwd.de/DE/leistungen/nwv_icon_tutorial/pdf_einzelbaende/icon_tutorial2024.pdf?__blob=publicationFile&v=3).

#### 2.4.2 Horizontal grid

The horizontal grid of ICON-CH1-EPS and ICON-CH2-EPS model is based on a native icosahedral grid inherited by the original ICON model grid (illustrated below).

<div align=center>
<img src="Images/IcosahedralGrid.png" width="300"/>

Illustration of the grid construction, Working with the ICON Model, Figure 2.1
</div>

Since the provided data is given in the native grid, note that the grid points correspond to the **center of the circumcircle of each triangle** and **not** to the vertices. Therefore, the longitude and latitude are based in the middle of each triangle on the grid mentioned before. For more detailed information on
the horizontal grid, read section 2.1 in [Working with the ICON Model](https://www.dwd.de/DE/leistungen/nwv_icon_tutorial/pdf_einzelbaende/icon_tutorial2024.pdf?__blob=publicationFile&v=3).

### 2.5 Static files

Besides the current forecasting files, each catalog contains two static files. They store permanent information about the halve levels (HHL) of the vertical grid and
the center points of each triangle (CLON/CLAT) on the horizontal grid. Note that the forecasting GRIB files contain no information on height, longitude and latitude. They have to be determined via the statc files HHL and CLON/CLAT.

#### 2.5.1 How to access the height of a grid point

In the static HHL file one can obtain the height of the half levels of the vertical grid in meters above see level. In order to point a value from the data file of a wanted parameter to a specific height, follow the steps below.
- Check if the `UUID` of the data file and the HHL file match.
- Then, use the `scaledValueOfFirstFixedSurface` value to retrieve the height in meter above see level of the HHL file.

#### 2.5.2 How to access the longitude and latitude of a grid point

The CLON/CLAT file stores the longitude and latitude of the center points of each triangle on the horizontal grid. When opening a data set in a jupyter nootbook the load function includes fetching the CLON/CLAT values. To retrieve CLON/CLAT without a python environment, see section 2.7.


### 2.6 Data visualisation

See [jupyter-notebook examples](https://github.com/MeteoSwiss/opendata-nwp-demos).

### 2.7 Access REST API (without python)

It is possible to dowload a GRIB file using the [REST API](https://sys-data.int.bgdi.ch/api/stac/static/spec/v1/apitransactional.html#tag/Data/operation/getAsset).
Start by runing the following command in a terminal.

```
GET {{baseUrl}}/v1/collections/{{collectionName}}/items/{{itemName}}
```
where:
- `baseURL` is `https://sys-data.int.bgdi.ch/api/stac`.
- `collectionName` is defined in [section 2.1](###2.1-Model-Specification) in the row "Collection".
- `itemName` is the name of the forecast the user wants to download. The name can be retrieved via
the two collections in [section 2.1](###2.1-Model-Specification).

The output shows a dictonary containing multiple keys. Whithin the key
`assets` locate `href`and copy the URL. Paste the URL to your browser and press enter to trigger the dowload.

#### 2.7.1 Install COSMO definitions

There are different abbriviations for the same parameter. By default the GRIB file shows the short names defined by ECMWF.
In order to install the COSMO definition, execute the steps below.

- Clone the github repositroy [eccodes-cosmo-resources](https://github.com/COSMO-ORG/eccodes-cosmo-resources) into folder *nameOfFolder*.
- Use: `cd eccodes-cosmo-resources` and `git checkout *version*`.
- Clone the github repository [ecmwf/eccodes](https://github.com/ecmwf/eccodes/) into the same folder *nameOfFolder*.
- Use: `cd eccodes` and `git checkout *sameVersion*`.

Finally run the following command every time before working with GRIB files:

```
export GRIB_DEFINITION_PATH=pathToFolder/eccodes-cosmo-recources/definitions:pathToFolder/eccodes/definitions
```



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
