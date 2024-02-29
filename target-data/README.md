# Target Data

This folder is used to store target data (also called "ground truth" or 
"truth data") relevant to the modeling efforts.

It contains the calibration data for phase 1 and 2 of the COVID-19
Scenario Modeling Hub (SMH) Disparities Round. 

For any questions or issues, please contact sbents@alumni.princeton.edu. 

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
Here `"other"`  represents the sum of other and Hispanic/Latino. 

Race/ethnicity 
grouping in California includes `"latino"`, `"black"`, `"white"`, 
`"asian"`, and `"other"`. All non-Latino groups are non-Hispanic and 
`"latino"` represents both Latino and Hispanic. 

Case demographic data is sourced from the 
[COVID-19 Race-Ethnicity Timeseries](https://data.chhs.ca.gov/dataset/covid-19-equity-metrics/resource/ef29f30e-320c-46cf-86cd-37a36663616d) from 
California Department of Public Health and 
[NC COVID-19 Dashboard Data](https://covid19.ncdhhs.gov/dashboard/data-behind-dashboards)
from the North Carolina Department of Public Health. 
Death demographic data is sourced from 
[The National Center for Health Statistics](https://wonder.cdc.gov/mcd-icd10-provisional.html) 

### Overall population data

- [cases_overall_jhu.csv](./cases_overall_jhu.csv): Overall cases reported 
to Johns Hopkins Center for Systems Science and Engineering (JHU-CSSE) 
in California and North Carolina. This gives full cases reported, whereas 
the public health department case data has some missingness by 
race/ethnicity.
