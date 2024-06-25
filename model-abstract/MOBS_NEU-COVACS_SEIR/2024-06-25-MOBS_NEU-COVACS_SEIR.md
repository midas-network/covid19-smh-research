## Summary of results given model assumptions? 
Our model describes the demographics and contact structures of different ethnic groups explicitly. We assume that variations in transmission rates between these groups are explained by differences in their contact rates and patterns. We use a baseline infection fatality rate (IFR) from the literature and estimate an adjustment for different groups. This is computed by considering the discrepancy between the expected deaths for a group, given its population size, and the actual observed deaths for that group during the calibration period. In California, we find that both "black" and "latino" ethnic groups have higher IFRs compared to the "white" ethnic group. The "black" ethnic group has lower contact rates than the "white" ethnic group, while the "latino" ethnic group has higher contact rates. Similarly, in North Carolina, we observe that "black" ethnic group have higher IFRs compared to the "white" ethnic group.

## Distribution of susceptibility at the start of the projection period? 
To estimate the distribution of the initial population immunity in different groups at the start of the projection period, we used the simulated number of recovered individuals of selected stochastic runs from different racial and ethnic groups.

## Which disease datasets (serology, cases, cases with imputed race/ethnicity information provided by coordination team, hospitalizations, deaths) were used for calibration? 
For the calibration of the model we used only deaths. 

## How were the transmission (P(infection)) and severity (P(death|infection) risks estimated across racial/ethnic groups? 
Our model accounts for different transmission rates across racial and ethnic groups using the contact matrices provided. Severity was adjusted by applying a correction to a baseline infection fatality rate. This correction was based on the ratio of deaths per 1,000 individuals within each group to the proportion of the total population represented by that race/ethnicity.

## How was the suppression of deaths handled in calibration? 
We considered the quantity 'value' + 'min_suppressed' (i.e., the evaluation quantity) of deaths for calibration. 

## Details about calibration of race/ethnicity showing zero deaths throughout the calibration period (e.g., Others in CA and Asian in NC)? 
By considering the quantity 'value' + 'min_suppressed' of deaths for calibration we do not obtain any group with zero deaths.

## How was contact mixing between racial/ethnic groups characterized? Was a contact matrix (either population-level or setting-specific) used? If so, describe the process used to apply the contact matrix.)
We considered the SMH provided contact matrix between racial/ethnic groups at the population level. 

## Was mobility data used throughout the calibration/projection period? 
To model the modulating effect of NPIs on transmission we used mobility data from the COVID-19 community mobility report published by Google. 

## Besides transmission, severity risk and contact matrices, did any other parameters vary by race/ethnicity (e.g., case reporting, NPI compliance)? 
No.

## How was the introduction of more transmissible variants modelled?
We fitted a logistic function to the growth of the Alpha variant in terms of its percentage of detections in both California and North Carolina. We then modulated the transmission rate by incorporating the fitted Alpha prevalence. Starting from \(\beta_0\) (the initial transmission rate at the start of the simulation), we increased it up to \(\psi \times \beta_0\), where \(\psi\) represents the increased transmissibility of the Alpha variant, which we set to 1.5 (i.e., 50% higher transmissibility compared to the wild type).

## How were NPIs implemented? 
We use data from the COVID-19 Community Mobility Report published by Google, which describes the percentage change in visits to specific points of interest. We translated the reduction in visits into a contact reduction factor, which was then used to adjust the transmission rate throughout the simulation.

## What was assumed about immunity/protection following infection? 
We assume that individuals who become infected and subsequently recover gain complete immunity against future infections, and we do not account for any waning of this immunity during the simulation period.

## How was vaccination implemented? What was assumed about immunity/protection following vaccination? 
We implemented vaccination into our model by adding compartments for individuals who received one or two doses of the vaccine. Both doses are considered effective, on average, two weeks after inoculation. The first dose provides an overall effectiveness (VE) against death (our primary endpoint) of 80%, while the second dose increases this effectiveness to 90%. This accounts for both protection against infection and severe outcomes in the event of a breakthrough infection. Individuals vaccinated with one dose have a VE against infection of 70%, and those with two doses of 80%. Vaccinated individuals, whether they received one or two doses, are 60% less infectious if they do get infected. We used real-world rollout data, disaggregated by race and ethnicity, to distribute doses within the simulation. We assume that susceptible, exposed, and recovered individuals are all eligible to receive the vaccine.

## Was age modeled in addition to race/ethnicity? Was there consideration for differences in the age structure across racial/ethnic populations? 
No.

## Was there importation of cases (e.g. from another external state)? 
Initial importation of cases was estimated using a global epidemic and mobility model. 
