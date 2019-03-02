# RWHOptimiser


[![Hit-Counter](http://hits.dwyl.io/aviral36/RWHOptimiser.svg)](http://hits.dwyl.io/aviral36/RWHOptimiser) 
![made-with-python](https://img.shields.io/badge/Contributors-6-blue.svg)
[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)



RWHOpt is a underground water tank location optimizer that finds the optimal location(s) and capacity of water tank(s) to be placed in the city, provided housing data, catchments, stability and (x,y) coordinates of houses. [See more about input](#inputs-structure-of-data).

RWHOpt implements a transshipment model to produce optimal number and location of tanks. This data is fed into the web application which displays a map of shared tanks and a cost analysis graph. [See more about output](#output-of-the-model).

## Data Collection and Preprocessing

The transshipment model takes in numeric data as input. The input data can either be fetched from a database retrieved from the city municipal corporation data. In case such data is not available, we use Vision API by Google to map catchment area on different coordinates of the city. 
The software is flexible and can take in data in different forms. Both our methods have been discussed below.

### Fetching Data from Municipal Corporation Data

A city municipal corporation has an accurate and comprehensive data of all land use in that city. The data includes important parameters like rooftop_area, coordinates_of_building, type_of_development (industrial/residential, etc.) amongst others. Land_use data is important as it helps differentiate industrial rooftops from residential rooftops.

### Mapping Data using Vision API

The below image shows how a society in Dwarka, New Delhi is being analysed to estimate the catchment area on/near the buildings.

![Rooftop mapping using Vision API](https://github.com/aviral36/RWHOptimiser/blob/master/metadata/Webp.net-gifmaker.gif)

The green cover in above image shows the catchment area as figured out by Vision. This has been made by implementing the watershed problem, which contains a segmentation code which segments a map, built entirely from scratch. 

## Inputs: Structure of Data

<strong>Coordinates (x,y): </strong>represent the geographical location of the centre of the catchment area, which may be a house, an apartment complex, an official building, a factory, etc, hereafter referred to as a node.

<strong> Demand (volumetric): </strong> This parameter denotes the demand of a catchment area arising from a particular node. The unit for measurement is cubic metre per month.

<strong> Stability (decimal): </strong> This measure gives the relative stability of a place (x,y) with a decimal numeral ranging from -1 to 10. Instability arises due to various factors like groundwater level, loose ground, existing pipelines, etc. Further, if a tank is impossible to be placed in a certain location, the value is set to -1. 

<strong> Cost of implementation: </strong> The overall cost of the system is actually a combination of two costs: fixed costs and variable costs. Fixed costs include one-time construction and installation costs. This includes all types of costs incurred during the set-up, like excavation, cost of concrete (per cubic meter) and others. 

## Output of the Model 

###### NOTE: This section deals with the output of our optimization model. This output is fed into a script which displays this information in a more appealing manner, along with various other functionalities. To see the visual output, click here.


