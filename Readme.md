# Pangeo Gallery Template


This repository stores an example gallery repo for the Pangeo Gallery.
To access, download folder and open in jupyter lab.
Main use of this repo is to query and download data from cmip6 models to be used to create deep-learning models.


The repo contains the following elements:

- A set of jupyter notebooks
  - basic_search_and_load: query for data from cmip6 -> store data and/or create animation 
  - ECS_Gregory_Method: uses "Gregory method" to approximate ECS of CMIP6 models based on first 150 years after abrupt quadrupling of CO2 concentrations
  - global_mean_surface_temp: calculates global mean surface temp using similar methods to "Gregory method"
  - intake_ESM_example: experimental way to query cmip6 data; still unstable
  - precip_frequency_change: calculate the distribution of precipitation intensity
- numpy files containing 3D arrays of lat, lon, time, and variable (instructions on extracting this info below)
- A configuration file, `binder-gallery.yaml`, which provides important
  configuration parameters (see [pangeo gallery documentation](http://gallery.pangeo.io)).
- A thumbnail image (`thumbnail.png`), a 200 x 200 px image which represents
  the gallery content.
- Github workflows, which make the magic happen! (Don't touch these.)


Search and Download Data
- Explore Data:
  - Read thorough this: https://docs.google.com/document/d/1yUx6jr9EdedCOLd--CPdTfGDwEwzPpCF6p1jRmqx-0Q/edit#
  - Search through this for variable descriptions: https://docs.google.com/spreadsheets/d/1UUtoz6Ofyjlpx5LdqhKcwHFz2SGoTQV2_yekHyMfL9Y/edit#gid=1221485271
  - Explore data more throughly here: https://esgf-node.llnl.gov/search/cmip6/
- Go to basic_search_and_load.ipy
- Query data using desired filters
  - need only three filters (experiment_id, table_id, variable_id) but can use more if needed
  - default values should be "activity_id=='CMIP' & table_id == 'Amon' & variable_id == 'tas' & experiment_id == 'historical'"
- scroll down to for loop where data is saved as numpy then stored into a numppy file
  - change numpy file name to desired name 
  - change data variables to new variable_id (replace all the "tas" with new variable_id)
