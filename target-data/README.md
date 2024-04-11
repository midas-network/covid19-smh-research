# Target Data

This folder is used to store target data (also called "ground truth" or 
"truth data") relevant to the modeling efforts.

For any questions or issues, please feel free to open an issue. 

## Disparities Round

This folder contains the calibration data for phase 1 and 2 of the COVID-19
Scenario Modeling Hub (SMH) Disparities Round. 

### Demographic data

Data is reported for incident cases and deaths. 

- [target_data_phase1.csv](./target_data_phase1.csv): Calibration 
data to be used for Phase 1. 
This file contains incident cases and deaths for California and 
North Carolina as reported to respective public health departments 
up until 11/14/2020. 

- [target_data_phase2.csv](./target_data_phase2.csv): Calibration data 
to be used for Phase 2. 
This file contains incident cases and deaths for California and 
North Carolina as reported to respective public health departments 
up until 4/3/2021.


Race/ethnicity grouping in North Carolina 
includes `"black"`, `"white"`,  `"asian"`, and `"other"`. 

Race/ethnicity 
grouping in California includes `"latino"`, `"black"`, `"white"`, 
`"asian"`, and `"other"`. 

Case demographic data is sourced from the 
[COVID-19 Race-Ethnicity Timeseries](https://data.chhs.ca.gov/dataset/covid-19-equity-metrics/resource/ef29f30e-320c-46cf-86cd-37a36663616d) from 
California Department of Public Health and 
[NC COVID-19 Dashboard Data](https://covid19.ncdhhs.gov/dashboard/data-behind-dashboards)
from the North Carolina Department of Public Health. 
Death demographic data is sourced from 
[The National Center for Health Statistics](https://wonder.cdc.gov/mcd-icd10-provisional.html) 

#### Source:

- [`source/nc_case_demographics_county.csv`](./source/nc_case_demographics_county.csv): 
raw county-level estimates of cases by race in North Carolina with more 
detailed information on suppression from 
[NC COVID-19 Dashboard Data](https://covid19.ncdhhs.gov/dashboard/data-behind-dashboards)
from the North Carolina Department of Public Health.

- [`source/NCHS_death_source_data.csv`](./source/NCHS_death_source_data/csv): 
data from The National Center for Health Statistics where total number of 
suppressed deaths that occurred before the end of 
the projection period in each state so that teams can distribute suppression 
using the method they prefer. We deduced from public health department data 
that there are 1932 total suppressed deaths in California and 223 total 
suppressed deaths in North Carolina over the study period.

### Overall population data

- [cases_overall_jhu.csv](./cases_overall_jhu.csv): Overall cases reported 
to Johns Hopkins Center for Systems Science and Engineering (JHU-CSSE) 
in California and North Carolina. This gives full cases reported, whereas 
the public health department case data has some missingness by 
race/ethnicity.


### Definition

The definitions of race/ethnicity can differ across various datasets. Racial/ethnic 
groups are reported consistently across death data, serology, and census data, 
where if an individual is Hispanic or Latino, their primary racial/ethnic
group is “latino,” and all other racial subgroups are interpreted as non-Hispanic. 
Note that serology is subject to self-reporting whereas death certificate and 
census data are not, so although classifications are the same, there may still be 
slight differences in groups represented. We provide tables for mapping how data 
is reported to how it is observed in the target data. 

Serology and census data are available in the 
[covid19-smh-research_resources](https://github.com/midas-network/covid19-smh-research_resources) 
GitHub repository,
[disparities folder](https://github.com/midas-network/covid19-smh-research_resources/tree/main/disparities)


#### Serology and census data

|State|Race_ethnicity|Target Data|
|:---|:----|:----|
|California|Hispanic or Latino|latino|
|California|non-Hispanic White|white|
|California|non-Hispanic Black|black|
|California|non-Hispanic Asian|asian|
|California|non-Hispanic Other|other|
|North Carolina|Hispanic or Latino|other|
|North Carolina|non-Hispanic White|white|
|North Carolina|non-Hispanic Black|black|
|North Carolina|non-Hispanic Asian|asian|
|North Carolina|non-Hispanic Other|other|

#### NCHS Death data

In the target death data, there are more detailed breakups of the same population 
groups. This dataset is also subject to a small proportion of known suppression, 
where suppressed values can range from 1-9. We have set all suppressed values to 
the minimum value of 1 and this is noted in the "min_suppressed" column in the 
target data files. 

Teams will be evaluated on the sum of the "value" and "min_suppressed" columns 
in the target death data, since this represents the most complete and accurate 
version of the dataset. 

|State|Race_ethnicity|Target Data|
|:---|:----|:----|
|California|Hispanic or Latino|latino|
|California|non-Hispanic White|white|
|California|non-Hispanic Black|black|
|California|non-Hispanic Asian|asian|
|California|non-Hispanic American Indian or Alaskan Native|other|
|California|non-Hispanic Native Hawaiian or other Pacific Islander|other|
|California|non-Hispanic more than once race |other|
|North Carolina|Hispanic or Latino|other|
|North Carolina|non-Hispanic White|white|
|North Carolina|non-Hispanic Black|black|
|North Carolina|non-Hispanic Asian|asian|
|North Carolina|non-Hispanic Other|other|
|North Carolina|non-Hispanic American Indian or Alaskan Native|other|
|North Carolina|non-Hispanic Native Hawaiian or other Pacific Islander|other|
|North Carolina|non-Hispanic more than once race |other|

#### Case and Vaccination data

Case and vaccination data is derived from state public health department data. 
California reports racial/ethnic grouping consistently with other data sources 
but North Carolina reports race and ethnicity separately. We choose to use race data 
in North Carolina given higher completeness and consistency with other data sources.
Cases and vaccination data are mapped in the following format: 


|State|Race_ethnicity|Target Data|
|:---|:----|:----|
|California|Latino|latino|
|California|White|white|
|California|African American|black|
|California|Asian American|asian|
|California|American Indian Native Hawaiian or other Pacific Islander|other|
|California|Multiracial|other|
|California|non-Hispanic more than once race |other|
|North Carolina|White|white|
|North Carolina|Black or African American|black|
|North Carolina|American Indian or Alaskan Native|other|
|North Carolina|Asian or other Pacific Islander|other|
|North Carolina|Additional Groups|other|

