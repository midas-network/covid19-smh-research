## Summary of results given model assumptions? 
In the calibration phase, we fitted the weekly death numbers using Markov Chain Monte Carlo (MCMC) methods, assuming that the transmission rates vary with races/ethnicities and over time (monthly). The true death numbers were captured throughout this phase.

In the projection phase, we recorded the model parameters, as well as the last set of transmission rates and infection-to-fatality rates from the calibration phase. We then considered the humidity cycle (representing the seasonal cycle) and changes in non-pharmaceutical interventions (NPI) to perform the projections.

In California (CA), the true death numbers are captured by the model at similar magnitudes, except for the 'Other' race. For Asian and White races, the model shows slightly higher peaks than the true data, while for Black and Latino races, the peaks are slightly lower. All the peaks occur around one weeks later than in the true data.

In North Carolina (NC), the model captures the true death numbers well for most races except for Asians, which had zero recorded death numbers during the calibration phase. The model exhibits higher and earlier peaks compared to the true data.

## Distribution of susceptibility at the start of the projection period? 
In California (CA), the Latino population has the highest susceptibility, followed by the White and Asian populations. The susceptibility distributions for Black and 'Other' populations are wide, with low median values.


In North Carolina (NC), the White population has a comparably low and narrow distribution of susceptibility. In contrast, the 'Other' population's distribution is wider, with median values slightly higher than those of the White population. The 'Other' group has the lowest median susceptibility. The Asian population has the highest median susceptibility, but with a very wide distribution due to very limited data.


## Which disease datasets (serology, cases, cases with imputed race/ethnicity information provided by coordination team, hospitalizations, deaths) were used for calibration? 
We used serology and death dataset provided in the github for the calibration.

## How were the transmission (P(infection)) and severity (P(death|infection) risks estimated across racial/ethnic groups? 
We estimated the infection values by the times of the serology data and the population data.
In CA, the Infections is shown in the following figure:

The latino has the largest infected number, followed by the white population. The black, asian and the other races are at lower level. Regarding the severity, we used the savgol filter to smooth the monthly rates to daily.

It shows that, except for Asians, whose severity remains around $1\%$, the severity of the other four race/ethnicities is high at the outbreaks and then decreases to low levels. The severity for Whites decreases to $0.5\%$, while for Latinos and Blacks, it decreases even further to $0.25\%$. The severity for the 'Other' category is not stable; after initially decreasing, it experiences a slight increase to $1.1\%$.

Whites have the largest infected population and the second-highest severity. Blacks have the second-largest infected population and the highest severity. The 'Other' race category is in third place, while Asians have the lowest infections and severity. (This may be due to incomplete data collection).

In general, the severities in North Carolina (NC) are lower than those in California (CA).

## How was the suppression of deaths handled in calibration? 
For California (CA), the known suppressed value of 1932 divided by the sum of the minimum suppressed values equals around 6.80. Thus, we adjusted the number of deaths by adding six times the minimum suppressed value to the original value. In North Carolina (NC), the known suppressed value of 223 divided by the sum of the minimum suppressed values is around 1.36. Thus, we adjusted the number of deaths by adding one times the minimum suppressed value to the original value.

## Details about calibration of race/ethnicity showing zero deaths throughout the calibration period (e.g., Others in CA and Asian in NC)? 
Some of the zero points were adjusted by adding the suppressed values as previously described. We did not make additional adjustments for the zero deaths during the calibration period.

## How was contact mixing between racial/ethnic groups characterized? Was a contact matrix (either population-level or setting-specific) used? If so, describe the process used to apply the contact matrix.)
We constructed a 'normalized' contact matrix: we divided the number of contacts made between race $r_{i}$ and all the races by the total contacts made by race $r_{i}$. 

This operation was performed for both California (CA) and North Carolina (NC).

## Was mobility data used throughout the calibration/projection period? 
Yes, the mobility data was not used throught the calibration nor projection period.

## Besides transmission, severity risk and contact matrices, did any other parameters vary by race/ethnicity (e.g., case reporting, NPI compliance)? 
No. No other parameters varied by race/ethnicity.

## How was the introduction of more transmissible variants modeled? 
We fitted the number of deaths of different races/ethnicities with a SEIVR model. The transmissible variants are modeled through the $\beta_{r_{i}}$ of our model. The higher the $\beta_{r_{i}}$ and the more easily the race $r_{i}$ get infected. 

## How were NPIs implemented? 
In the projection period, we created a function to model the decrease in the $\beta$ which was caused by the increase in the NPIs.

## What was assumed about immunity/protection following infection? 
We assumed an immunity period of $600$ days in our SEIRV model.

## How was vaccination implemented? What was assumed about immunity/protection following vaccination? 
In our SEIRV model, we assumed a vaccination projection duration of $730$ days. According to the literature, the protection rate against symptomatic infection was assumed to be $95\%$, reflecting the rates of widely used vaccines BNT162b2 ($95\%$) and mRNA-1273 ($94\%$). Similarly, the protection rate against death was also assumed to be $95\%$.

## Was age modeled in addition to race/ethnicity? Was there consideration for differences in the age structure across racial/ethnic populations? 
No, the age was not modeled in our model.

## Was there importation of cases (e.g. from another external state)? 
No, in our model, we did not consider the importation of cases from another external state.
