## Summary of results given model assumptions? 
Model dynamics are driven by SEIR dynamics, and differences between race-ethnicity groups are largely due to differences in transmission modifiers due to implemented interventions. These fit intervention modifiers are race-ethnicity-specific. Additionally, we fit race-ethnicity-specific transmissibility parameters. Absent of these parameters, trends/dynamics across groups are not largely different, based on our simplified assumptions. 

## Distribution of susceptibility at the start of the projection period? 
Our simulations begin at the start of the pandemic, and initial infections are seeded from initial death data. 

## Which disease datasets (serology, cases, cases with imputed race/ethnicity information provided by coordination team, hospitalizations, deaths) were used for calibration? 
We calibrated to race/ethnicity specific death data provided.

## How were the transmission (P(infection)) and severity (P(death|infection) risks estimated across racial/ethnic groups? 
We model and fit different transmission rates for each race/ethnic group, but do not explicitly use the contact matrices provided. We also assume that interventions apply differentially to each race/ethnic group, and fit these separately. Additionally, we fit differential IFR adjustments by race/ethnic group. 

## How was the suppression of deaths handled in calibration? 
We compared hub provided data with aggregated data from the equivalent state dashboards, and calculated the discrepancy between these datastreams, and redistributed any difference by week according to the proportion of incidence. We then performed a quality check on these values; if the number of suppressions was greater than the redistributed value, we replaced the redistributed value by the number of suppressions. 

## Details about calibration of race/ethnicity showing zero deaths throughout the calibration period (e.g., Others in CA and Asian in NC)? 
We calibrate to the provided data using a normal likelihood, and do not make any adjustments to these data. 

## How was contact mixing between racial/ethnic groups characterized? Was a contact matrix (either population-level or setting-specific) used? If so, describe the process used to apply the contact matrix.)
We did not directly use a contact matrix, but assumed for each race/ethnic group there was some modified transmissibility which we fit. 

## Was mobility data used throughout the calibration/projection period? 
Commuter data

## Besides transmission, severity risk and contact matrices, did any other parameters vary by race/ethnicity (e.g., case reporting, NPI compliance)? 
We assumed that NPIs modified transmission in each race/ethnic group differently. 

## How was the introduction of more transmissible variants modelled?
We assumed Alpha was 1.5x more transmissible. 

## How were NPIs implemented? 
We fit transmission modifiers to each NPI period as differential across race/ethnic groups. For NPIs in the projection period, we assumed these were similar in magnitude to these fit NPI transmission modifiers, based on the interventions announced/the list provided by the hub. 

## What was assumed about immunity/protection following infection? 
We assume protection wanes, and fit this waning rate with a prior of 10 months.

## How was vaccination implemented? What was assumed about immunity/protection following vaccination? 
We implement vaccination using the provided vaccination rates, and assumed this moved individuals to a protected compartment based on vaccine efficacies against each variant. We assume that vaccination only wanes after the second dose, at the same rate as natural infection. 

## Was age modeled in addition to race/ethnicity? Was there consideration for differences in the age structure across racial/ethnic populations? 
Yes, we model the following age groups: 0-17, 18-64, and 65+. Age structure was determined using the joint population data provided by the hub. 

## Was there importation of cases (e.g. from another external state)? 
No
