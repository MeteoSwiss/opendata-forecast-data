[MeteoSwiss - Open Data](https://github.com/MeteoSwiss/opendata/blob/main/README.md) > [Understanding MeteoSwiss' Open Data products](https://github.com/MeteoSwiss/opendata/blob/main/README.md#understanding-meteoswiss-open-data-products) > E. Forecast Data

# E. Forecast Data
... 

1. [Short-term forecast data](#1-short-term-forecast-data)
2. [Forecast data](#2-forecast-data)
3. [Local forecast data](#3-local-forecast-data)

---

## 1. Short-term forecast data
[Nowcasting](https://www.meteoswiss.admin.ch/weather/warning-and-forecasting-systems/nowcasting.html) involves high spatial and temporal resolution forecasts of weather developments for the next few minutes and up to a maximum of six hours ahead. MeteoSwiss uses these short-term forecasts to, among other things, predict thunderstorms, hail and heavy rainfall.

As MeteoSwiss is planning to replace the current 'INCA' nowcasting software, the following datasets are available from the start of our open data provision:
- Precipitation (10min values): quantitative chain (based on CombiPrecip, RR)
- ...
- ...

The following datsets will be provided next:
- Snowfall (10min values): quantitative chain (based on CombiPrecip, RS)
- ...
- ...


<!-- The INCA forecasts come .

For more information see the metadata in each NetCDF-File. -->

...

### 1.1. Data granularity, update frequency, format and volume
Data granularity is `every 10min`. Update frequency for the period 0h- +6h is specified per dataset in the table below.

Data format is [`NetCDF (.nc)`](https://www.unidata.ucar.edu/software/netcdf).

| Dataset | Update frequency | Estimated volume per file (MB) | (Example!) data file | Productive version file name |
| ----- | ----- | ----- | ----- | ----- |
| Precipitation (10min values): quantitative chain (based on CombiPrecip, RR) | 1.7 | [RR_INCA_202106280700.nc](https://github.com/MeteoSwiss/publication-opendata-inca-data-nowcasting/blob/main/RR_INCA_202106280700.nc) | `ogd-nowcasting_RR-INCA_(date and time code).nc` |  |
|       |       |       |       |       |
| Snowfall (10min values): quantitative chain (based on CombiPrecip, RS) | 0.4 | [RS_INCA_202106280700.nc](https://github.com/MeteoSwiss/publication-opendata-inca-data-nowcasting/blob/main/RS_INCA_202106280700.nc) | `ogd-nowcasting_(product name)_(granularity code)_(update frequency code).csv` |  |

### Parameter metadata
*See (example!) parameter metadata files of [data granularity](https://github.com/MeteoSwiss/opendata-download?tab=readme-ov-file#data-granularity): [`...`](...) and [`...`](...).*

<!-- ### Codes -->
<!-- ... -->

### Station metadata
*See (example!) [station metadata file](...).*

### Data visualisation
See e.g. MeteoSwiss' [...](...).

## 2. Forecast data
...

## 3. Local forecast data
... 

...

### Data granularity, update frequency, format and volume
There are files of [data granularity](https://github.com/MeteoSwiss/opendata-download?tab=readme-ov-file#data-granularity) `...`, `...`, `...`, `...` *and [update frequency](https://github.com/MeteoSwiss/opendata-download/blob/main/README.md#update-frequency) hourly (`now`), daily (`recent`) or yearly (`historical`) for each station*.

Data format is [`CSV`](https://github.com/MeteoSwiss/opendata-download?tab=readme-ov-file#column-separators-decimal-dividers-and-missing-values) with an estimated volume of ... MB per file.

See (example!) data files: [`...`](...).

### Parameter metadata
See (example!) parameter metadata files of [data granularity](https://github.com/MeteoSwiss/opendata-download?tab=readme-ov-file#data-granularity): [`...`](...) and [`...`](...).

<!-- ### Codes -->
<!-- ... -->

### Station metadata
See (example!) [station metadata file](...).

### Data visualisation
See e.g. MeteoSwiss' [...](...).
