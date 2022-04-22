# Pangeo Gallery Template

Authors:
Vivian Trenh, MIT 

This repository stores an example gallery repo for the Pangeo Gallery.
To access, download folder and open in jupyter lab.
Main use of this repo is to query and download data from CMIP6 models to be used to create deep-learning models.

## Content
- Notebooks to preprocess and download CMIP6 data:
  - [basic_search_and_load](basic_search_and_load.ipynb): Queries, stores, and animates CMIP6 data
  - [ECS_Gregory_method](ECS_Gregory_method.ipynb): Approximate the equilibrium climate sensitivity (ECS) of CMIP6 models via the "Gregory method" using the first 150 years after abrupt quadrupling of CO2 concentrations 
  - [global_mean_surface_temp](global_mean_surface_temp.ipynb): Calculates the global mean surface temperature using similar methods to "Gregory method"
  - [intake_ESM_example](intake_ESM_example.ipynb): Queries CMIP6 data; experimental and still unstable
  - [precip_frequency_change](precip_frequency_change.ipynb): Calculate the distribution of precipitation intensity
- Numpy files containing 3D arrays of lat, lon, time, and variable (instructions on extracting this info below)
- A configuration file, `binder-gallery.yaml`, which provides important
  configuration parameters (see [pangeo gallery documentation](http://gallery.pangeo.io)).
- A thumbnail image (`thumbnail.png`), a 200 x 200 px image which represents
  the gallery content.
- Github workflows, which make the magic happen! (Don't touch these.)

## Instructions on Searching and Downloading Data
- Explore Data:
  - Intro to dataset structure at [link](https://docs.google.com/document/d/1yUx6jr9EdedCOLd--CPdTfGDwEwzPpCF6p1jRmqx-0Q/edit#)
  - Variable descriptions at [link](https://docs.google.com/spreadsheets/d/1UUtoz6Ofyjlpx5LdqhKcwHFz2SGoTQV2_yekHyMfL9Y/edit#gid=1221485271)
  - Explore data more throughly at [link](https://esgf-node.llnl.gov/search/cmip6/)
- Go to [basic_search_and_load](basic_search_and_load.ipynb)
- Query data using desired filters:
  - Need only three filters (experiment_id, table_id, variable_id) but can use more if needed
  - Default values should be "activity_id=='CMIP' & table_id == 'Amon' & variable_id == 'tas' & experiment_id == 'historical'"
- Scroll down to for loop where data is saved as numpy then stored into a numpy file
  - Change numpy file name to desired name 
  - Change data variables to new variable_id (replace all the "tas" with new variable_id)

## Installation
```
conda env create -f environment.yml
```
conda create --name cmip6-urop python numpy pandas xarray cartopy zarr
pip install jupyter
pip install --upgrade jupyterhub
pip install --upgrade --user nbconvert
conda install -c conda-forge fsspec
conda install -c conda-forge gcsfs
conda install -c conda-forge cftime
conda install -c conda-forge tqdm
conda install -c conda-forge ffmpeg
conda install -c conda-forge nodejs # Test to make tqdm work

Create the env file: conda env export > environment.yml

