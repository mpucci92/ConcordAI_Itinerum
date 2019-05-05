# Itinerum Challenge

Before going further fill this out ! (mandatory) : 

http://tiny.cc/concordai-hackathon-form

## Project Description

The purpose of this project is to develop machine learning classifier models that will use
location data on respondent trips from the 2017 MTL Trajet study. MTL Trajet is an Itinerum-
based smartphone travel survey app that has been used for annual smartphone studies in the
fall of 2016, 2017 and 2018.

## Data source

The two main data sources for the project are the open versions of this data from the Ville de
Montréal Open Data portal.

The data are located in ./data folder of this project

The two main data sources for the project are the open versions of this data from the Ville de
Montréal Open Data portal. The data can be accessed here:

http://donnees.ville.montreal.qc.ca/dataset/mtl-trajet/resource/64278608-6bf4-4a30-83c0-2bc6e3a459e1

The two primary datasets are the “trips” (trajets) data and the “points” data.
The trips data can be downloaded here:

http://donnees.ville.montreal.qc.ca/dataset/mtl-trajet/resource/71d43835-1eef-4ae0-a0c4-578d5c8c605d?inner_span=True

![image0](/img/img0.png)

The points data can be downloaded here:

http://donnees.ville.montreal.qc.ca/dataset/mtl-trajet/resource/cb661499-3fa9-4793-a5fd-1ba320342fcd?inner_span=True

![image1](/img/img1.png)


## Proposed methodology

To get started with this project the software and libraries listed below will likely be used and
would be good to have installed. It would be best to work only with single mode trips (e.g.
Bicycle instead of Bicyle and Walk). It would also be best to work only with a subset of these
trips; a few hundred should be fine to facilitate processing and estimation.
Mode identification for the points of a trip (the classification) needs to be obtained from the
trips (trajets) data. Possible factors/variables to be used in the mode classifier models could
include average travel speed, 85 th percentile speed, overall trip distance, acceleration, etc. It
might also be possible to include other information such as the location of metro stations to
help in such models.

## Getting Started

Clone the Gitlab project

In a terminal command :

git clone https://gitlab.com/concordai-spring-hackathon-2019/itinerum-challenge.git

## Requirements

#### GIS and Database Software

QGIS (an open-source cross-platform desktop geographic information system application that
supports viewing, editing, and analysis of geospatial data)
https://www.qgis.org/fr/site/forusers/download.html

PostGIS (an open source software program that adds support for geographic objects to the
PostgreSQL object-relational database)
https://postgis.net/install/

Postgres/PostgreSQL (open-source relational database management system)
https://www.postgresql.org/

ogr2ogr (a general purpose command-line GIS tool for transforming data and loading to
PostGIS)
https://www.gdal.org/ogr2ogr.html

#### Python Libraries

Most of the following libraries are already included in an Anaconda env
- Numpy
```
pip install numpy

```
- scikit-learn
```
pip install scikit-learn

```
- Pandas
```
pip install pandas

```
- Tensorflow, Keras
```
pip install tensorflow keras

```
- Pytorch
```
pip install pytorch

```

## Exemple

1. Have PostgreSQL installed with PostGIS extension enabled
a. Create a new database for MTL Trajet data
2. Download the open MTL Trajet points and trip .geojson files (above) to a local directory
3. Load .geojson files to PostgreSQL using ogr2ogr (working directory from step 2; can take
a while)
In a Terminal command :
$ ogr2ogr -f "PostgreSQL" PG:"dbname=mtltrajet user=postgres" "./points_mtl_trajet_2017-1.geojson" -
nln points
$ ogr2ogr -f "PostgreSQL" PG:"dbname=mtltrajet user=postgres" "./trajets_mtl_trajet_2017-1.geojson" -
nln trips

