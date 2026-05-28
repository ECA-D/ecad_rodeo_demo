# ECA&D RODEO MyBinder tutorial

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ECA-D/ecad_rodeo_demo/main?urlpath=%2Fdoc%2Ftree%2Fbasic_demo.ipynb)

This repository is a simple setup for a MyBinder tutorial that demonstrates how to use the ECA&D non-blended collection through the RODEO OGC Environmental Data Retrieval (EDR) API.

The notebooks show how to inspect the collection, find stations, request station time series, use bounding-box and polygon queries, and download data in NetCDF format. The environment is intentionally small so it can be launched quickly on MyBinder.

## Project Context

The examples use the ECA&D non-blended collection exposed through the EUMETNET Climate Observations API:

https://api.meteogate.eu/eu-eumetnet-climate-observations

ECA&D contains European meteorological observations. The non-blended collection contains station series as provided by the data participants. More information about ECA&D is available at:

https://www.ecad.eu

Technical API documentation, examples, and settings are available from the API documentation page:

https://api.meteogate.eu/eu-eumetnet-climate-observations

## Contents

- `basic_demo.ipynb`: beginner-friendly walkthrough. It configures the API endpoint, retrieves station metadata with `/locations`, requests one station with `/locations/{id}`, queries observations with `/cube`, summarizes the returned station data, and downloads station data as NetCDF with `f=netCDF4`.
- `advanced_demo.ipynb`: extended demonstration. It inspects collection metadata, plots the ECA&D station network, requests a De Bilt time series, and demonstrates polygon queries using the Rhine basin.
- `requirements.txt`: Python packages installed by Binder.

## Run on MyBinder

Click the MyBinder badge above to launch the tutorial in a browser. MyBinder will build the environment from this repository, install the packages listed in `requirements.txt`, and open `basic_demo.ipynb`.
