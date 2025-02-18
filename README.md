[MeteoSwiss - Open Data](https://github.com/MeteoSwiss/opendata/blob/main/README.md) > [Understanding MeteoSwiss' Open Data products](https://github.com/MeteoSwiss/opendata/blob/main/README.md#understanding-meteoswiss-open-data-products) > E. Forecast Data

# E. Forecast Data
[Forecasting systems](https://www.meteoswiss.admin.ch/weather/warning-and-forecasting-systems.html) calculate future atmospheric conditions on the basis of measurement data and observations. MeteoSwiss uses these weather models to create weather forecasts and to enable it to issue weather warnings in the event of imminent hazards.

The following forecast data are available:

1. [Short-term forecast data](#1-short-term-forecast-data) :yellow_circle: *documentation upcoming*
2. [Numerical weather forecasting model](#2-numerical-weather-forecasting-model) :yellow_circle: *documentation upcoming*
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

## 2. Numerical weather forecasting model

MeteoSwiss uses two models, **ICON-CH1-EPS** and **ICON-CH2-EPS**, to forecast atmospheric changes in Switzerland and its surroundings over a longer period than nowcasting, providing predictions for up to five days.
[ensemble data assimilation](https://www.meteoswiss.admin.ch/weather/warning-and-forecasting-systems/icon-forecasting-systems/ensemble-data-assimilation.html).
The user can access the forecast model output data of the last 24 hours. Data that is older than 24 hours is no longer available. To see what data is accessible, the user can search in [Catalog 1](https://sys-data.int.bgdi.ch/browser/#/collections/ch.meteoschweiz.ogd-forecasting-icon-ch1?.language=en) for data on ICON-CH1-EPS and in [Catalog 2](https://sys-data.int.bgdi.ch/browser/#/collections/ch.meteoschweiz.ogd-forecasting-icon-ch2?.language=en) for ICON-CH2-EPS.

The structure of the data is as follows: Each file contains several parameters. What kind of parameters are accesible is stated in the [list of variables](https://meteoswiss.sharepoint.com/:x:/s/tmsAPAPN/Ee1fZIGn92NAtiaAZ3fvhvkBa0G7yuybES5VNaEm7pGqFw?e=Ffm2qX). Here are some examples:

| **Parameter**     | **Standart Unit**    |**Longname**     | **SingleLevel/MultiLevel**       | **Vertical Coordinate**     | **Horizon (Lead Time)**      | **Temporral aggregation**  | **Domain**      |
|------------------|-----------------------------|------------------|-----------------------------|------------------|-----------------------------|------------------|-----------------------------|
| CLCH| %|Cloud area fraction in high troposphere (above ca 400hPa)| Single Level| | | | |
|DURSUN | s | Duration of sunshine| Single Level| | | | |
|TOT_PREC | kg $m^{-2}$| Total precipitation| Single Level| | | | |


### 2.1. Data granularity, update frequency, format, volume and more

Both models have different benchmarks.

| **Attributes**| **ICON-CH1-EPS** | **ICON-CH2-EPS**| 
|-----------|------------------|-----------------|
| Collection Name | `ogd-forecasting-icon-ch1` | `ogd-forecasting-icon-ch2` |
| Horizontal Grid Size | 1 km | 2.1 km |
| Ensemble Members | 11 | 21 |
| Forecast Period | 33 h | 120 h |
| Grid | Native icosahedral | Native icosahedral |
| Temporal Resolution |  1 h | 1 h |
| Model Run Interval | every 3 h | every 6 h |
| Format | GRIB edition 2 | GRIB edition 2 |


### 2.2. Parameter metadata

The parameter metadata is part of each GRIB file.

### 2.3. Coordinate system

The ICON-CH1-EPS and ICON-CH2-EPS model uses a native icosahedral grid inherited by the original ICON model grid. In order to regrid to another grid we provide regridding operators.

### 2.4. Data visualisation

See [jupyter-notebook examples](https://github.com/MeteoSwiss/opendata-nwp-demos).

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
