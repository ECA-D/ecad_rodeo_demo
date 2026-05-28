# ECA&D RODEO MyBinder tutorial

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/ECA-D/ecad_rodeo_demo/main?urlpath=%2Fdoc%2Ftree%2Fbasic_demo.ipynb)

This repository is a simple setup for a MyBinder tutorial that demonstrates how to use the ECA&D non-blended collection through the RODEO OGC Environmental Data Retrieval (EDR) API.

The notebooks show how to inspect the collection, find stations, request station time series, use bounding-box and polygon queries, and download data in NetCDF format. The environment is intentionally small so it can be launched quickly on MyBinder.

Each API query in the notebooks prints the full request URL before showing the result. This is useful for non-Python users too: you can see exactly what the API call looks like, copy the URL, and try it in a browser or another tool.

## What Is MyBinder?

MyBinder is a free service that turns a GitHub repository into a temporary interactive computing environment in the browser. You do not need to install Python, Jupyter, or any packages on your own computer.

When you click the MyBinder badge, MyBinder will:

1. Read this repository.
2. Install the Python packages listed in `requirements.txt`.
3. Start a Jupyter notebook session in your browser.
4. Open the tutorial notebook so you can run the examples cell by cell.

A notebook is an interactive document that mixes explanation text, Python code, and output such as tables or plots. To run a code cell, select it and press `Shift + Enter`, or use the run button in the notebook toolbar.

You do not need to understand all the Python code to follow the API examples. For each request, look first at the printed URL in the cell output. That URL shows the endpoint, query parameters, time range, requested variable, and response format used by the API.

The MyBinder session is temporary. Any files created during the session, such as downloaded NetCDF files, may disappear when the session stops. If you want to keep results, download them from the notebook session before closing it.

## Project Context

The examples use the ECA&D non-blended collection exposed through the EUMETNET Climate Observations API:

https://api.meteogate.eu/eu-eumetnet-climate-observations

ECA&D contains European meteorological observations. The non-blended collection contains station series as provided by the data participants. More information about ECA&D is available at:

https://www.ecad.eu

Technical API documentation, examples, and settings are available from the API documentation page:

https://api.meteogate.eu/eu-eumetnet-climate-observations

## Contents

- `basic_demo.ipynb`: beginner-friendly walkthrough. It configures the API endpoint, retrieves station metadata with `/locations`, requests one station with `/locations/{id}`, queries observations with `/cube`, summarizes the returned station data, and downloads station data as NetCDF with `f=netCDF4`. Each request prints the API URL before processing the response.  
  [Open `basic_demo.ipynb` on MyBinder](https://mybinder.org/v2/gh/ECA-D/ecad_rodeo_demo/main?urlpath=%2Fdoc%2Ftree%2Fbasic_demo.ipynb)
- `advanced_demo.ipynb`: extended demonstration. It inspects collection metadata, plots the ECA&D station network, requests a De Bilt time series, and demonstrates polygon queries using the Rhine basin. The request helper also prints the URL for every API call.  
  [Open `advanced_demo.ipynb` on MyBinder](https://mybinder.org/v2/gh/ECA-D/ecad_rodeo_demo/main?urlpath=%2Fdoc%2Ftree%2Fadvanced_demo.ipynb)
- `requirements.txt`: Python packages installed by Binder.
- `runtime.txt`: Python version used by MyBinder.
- `.github/workflows/notebooks.yml`: GitHub Actions workflow that executes the notebooks automatically.

## Keeping the Tutorial Working

The Python package versions in `requirements.txt` are pinned. This helps MyBinder and GitHub Actions build the same environment each time, instead of silently picking newer package versions that may behave differently.

The repository also includes a GitHub Actions workflow that runs the notebooks:

- on pull requests
- on pushes to `main`
- every Monday at 06:00 UTC
- manually, through the GitHub Actions tab

The workflow installs the packages from `requirements.txt` and executes both notebooks with `jupyter nbconvert`. This is similar to how users experience the notebooks on MyBinder: if a dependency changes, an API response changes, or a notebook cell fails, the workflow should fail and make the problem visible.

Because these notebooks call a live API, a failing scheduled run can mean either the notebook broke or the remote service was temporarily unavailable. If a scheduled run fails, first re-run the workflow once from GitHub Actions before changing the notebooks.

## Run on MyBinder

Click the MyBinder badge above to launch the basic tutorial in a browser, or use one of the notebook-specific links in the contents section. MyBinder will build the environment from this repository, install the packages listed in `requirements.txt`, and open the selected notebook.
