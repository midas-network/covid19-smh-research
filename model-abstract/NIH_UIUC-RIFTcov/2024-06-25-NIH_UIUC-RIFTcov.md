## Summary of results given model assumptions? 
In California, the confidence interval on projected cases and deaths largely includes target data for this time period, especially for the Latino population; however target data are on the high end of the projection interval. Cases and deaths for the “Other” grouping – while nonzero - are undercounted. In North Carolina, model projections also include most target data but with data on the low end of projections for all groups during the projection period, and projection windows exceed target data in all groups by March.  During calibration, the white population in North Carolina was estimated to have one third of the NPI compliance seen in California. This discrepancy in North Carolina may possibly reflect an unanticipated increase in NPI compliance during the projection period compared to California.

## Distribution of susceptibility at the start of the projection period? 
During the calibration period, a case reporting rate was fit for each racial/ethnic group (REG), indexed off of the white population. At the start of the projection period, we approximated the number of active infections for each REG on November 14, 2020 by dividing the number of reported cases that week by the REG-specific reporting rate, and subtracting the weekly deaths. To approximate the number of recovered individuals, we divided the cumulative reported cases by the reporting rate, and subtracted active infections as well as cumulative deaths. We assumed that this was the first infection for all individuals. To initialize the susceptible class, we subtracted active infections, recovered cases, and deaths from the population size for each REG. 

## Which disease datasets (serology, cases, cases with imputed race/ethnicity information provided by coordination team, hospitalizations, deaths) were used for calibration? 
Cases and deaths were explicitly used for calibration. Serological data was compared post-calibration with estimated cumulative infections, and informed the boundary values for reporting rate parameters during calibration. 

## How were the transmission (P(infection)) and severity (P(death|infection) risks estimated across racial/ethnic groups? 
The transmission parameter mu was assumed constant across racial/ethnic groups and locations, and thus risk of infection was differentiated by disparities in contact rates and NPI compliance. Infection fatality rates were inferred by calculating case fatality rates for each race/ethnicity during the calibration period (including min suppressed) and multiplying by case reporting rates for each race/ethnicity. 

## How was the suppression of deaths handled in calibration? 
The model was calibrated to the sum of the deaths + min suppressed.  Additionally, when calculating CFRs by race/ethnicity, min suppressed were included to avoid 0 CFRs.

## Details about calibration of race/ethnicity showing zero deaths throughout the calibration period (e.g., Others in CA and Asian in NC)? 
We calculated REG-specific CFRs using the deaths and cases reported during the calibration period, which were non-zero for all groups by including min suppressed. Rather than fitting the IFR for each group directly, we inferred the IFR using the CFR and calibrated case reporting rate for each REG - which had a restricted range based on seroprevalence data. Thus, the model can capture non-zero deaths during the projection period even for groups without reported deaths during calibration.

## How was contact mixing between racial/ethnic groups characterized? Was a contact matrix (either population-level or setting-specific) used? If so, describe the process used to apply the contact matrix.)
We included temporal contact matrices stratified by race/ethnicity, which were generated separately for each state using the prepandemic and pandemic contact matrices provided. During the calibration period, we rescaled temporal SafeGraph mobility data for each ego/alter pairing of racial/ethnic groups, with pandemic contact being the minimum and the mean of pre-pandemic/pandemic contact being the maximum. During the projection period, we carried forward the final contact matrix from calibration as baseline contact. We assumed a rise in contact for all groups moving into the projection period, peaking at a 10% increase from baseline on 2020-12-25 and returning to baseline by 2021-01-08. Using this time series of matrices, we generated spline functions for each ego/alter that return contact at time t throughout the calibration and projection periods. 

To calculate the force of infection for a given REG, each ego/alter pairing has a number of contacts at time t multiplied by the proportion of the alter population that is currently infectious and the probability of infection given contact. For each group, the total force of infection is given by the sum of all of these ego/alter interactions. 

## Was mobility data used throughout the calibration/projection period? 
SafeGraph mobility data was used through the calibration period. At the end of mobility data within the calibration period, on 2020-11-10, we stored contact matrices for this date as a baseline. We allowed a 10% rise in contact for each group moving into the projection period, peaking on 2020-12-25 and returning to baseline by 2021-01-08. 

## Besides transmission, severity risk and contact matrices, did any other parameters vary by race/ethnicity (e.g., case reporting, NPI compliance)? 
Case reporting and NPI compliance both varied by race/ethnicity. Values for non-white populations were indexed off of the white population.  

## How was the introduction of more transmissible variants modeled? 
We assumed that the incoming variant is 50% more transmissible and accounts for 1% of cases on November 15, rising to 50% of cases by March 15, and 66% by April 15. Accordingly, we implemented a spline function that returns the weighted average of the relative transmissibility of the old variant (1x) and new variant (1.5x) by the current proportion of new vs. old cases.  This value is used as a multiplier on the probability of transmission given contact throughout simulations.  

## How were NPIs implemented? 
NPIs are captured in two ways. First, changes in mobility scale contact up or down throughout both the calibration and projection periods. Second, in order to capture that some individuals have no or minimal effective contact, we calibrated NPI compliance proportions for each race/ethnicity, which are scaled off of the white population. At the beginning of both the calibration and projection periods, a proportion of each racial/ethnic group moves from a set of non-compliant equations to compliant, where the risk of infection and infecting others is modulated by NPI efficacy. During both the calibration and projection periods, NPIs are parameterized as all-or-nothing, so that compliance is 100% transmission-blocking for both ego and alter.  Individuals leave the NPI-compliant population at a uniform rate calibrated for each state. To reflect uncertainty in compliance behavior moving from the calibration to projection period, a relative change in NPI compliance was sampled from a range of 0.8-1.2x the calibration compliance.

## What was assumed about immunity/protection following infection? 
After the first infection, individuals are recovered in R1 for 6 months, then wane to a second susceptible class S2, where the risk of infection is 50% lower and the infection fatality rate is 75% lower. If reinfected in S2, individuals recover into R2, wane after 6 months into S2, and continue to cycle through this second level of protection. 

## How was vaccination implemented? What was assumed about immunity/protection following vaccination? 
Susceptible and recovered populations are eligible to be vaccinated. We implemented an all-or-nothing vaccine that protects 85% of individuals who receive it by placing them in the R2 class. Immunity wanes after 6 months, moving individuals to S2. REG- and state-specific daily vaccination rates were sourced from the provided data.

## Was age modeled in addition to race/ethnicity? Was there consideration for differences in the age structure across racial/ethnic populations? 
Age was not modeled. However, while reporting rate and NPI compliance were indexed off of the white population and constrained so that these rates were lower for non-white groups, the infection fatality rate was not constrained, in order to allow for the possible influence of age structure on the overall IFR. 

## Was there importation of cases (e.g. from another external state)? 
No importation was considered. 
