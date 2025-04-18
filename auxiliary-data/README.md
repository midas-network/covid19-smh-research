# Auxiliary Data

This folder is used to store additional data relevant to the modeling efforts. 
It contains one folders for location and population data

## Target Data

The  [target-data](./target-data/) contains:

- COVID-19 case and death time series by race/ethnicity for the 
  heterogeneities round. 

The folder contains also source data and detailed documentation.
  
## Location and Census Data

The folder [location_census/](./location_census/) contains two files:

- [location_census/locations.csv](./location_census/locations.csv) containing
  the state and national full name, 2 letter abbreviation and fips code as used 
  in the hub. The file also contains the population size
- [location_census/state_pop_data](./location_census/state_pop_data.csv) 
  contains the population size per year, state (and national level), age from
  2010 to 2022 (included). The data are coming from the US Census Bureau:
  - Annual Estimates of the Civilian Population by Single Year of Age and Sex 
  for the United States and States: April 1, 2010 to July 1,
  2020: available 
  [here](https://www.census.gov/programs-surveys/popest/technical-documentation/research/evaluation-estimates/2020-evaluation-estimates/2010s-state-detail.html)
  - Annual Estimates of the Civilian Population by Single Year of Age and Sex 
  for the United States and States: April 1, 2020 to July 1, 
  2022: available 
  [here](https://www.census.gov/data/datasets/time-series/demo/popest/2020s-state-detail.html)

## Model examples

The [model_examples](./model_examples/) folder contains model-output and 
model-metadata examples.

## Rounds
The [rounds](./rounds/) folder contains the round information in a markdown 
format with a folder names roundX_viz with X being the round number, containing 
associated visualization (for example, scenario table in a PNG format).
