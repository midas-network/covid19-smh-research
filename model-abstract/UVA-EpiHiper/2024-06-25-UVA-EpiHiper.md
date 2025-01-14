## Summary of results given model assumptions? 
In EpiHiper we model racial/ethnic heterogeneities explicity at individual level in demographics and activities. We also calibrate R/E specific transmissibility and R/E specific infection fatality rate using serology, cases, and deaths data sets.

For California, we find that both target deaths and target cases are well captured for white, asian, latino, and overall in our projections, but are under-projected for black and other. In our projections deaths and cases decrease slower after peak than in the target.

For North Carolina, we find that target deaths are well captured for white, asian, other, and overall in our projections, but are slightly over-projected for black. Target cases are well captured for white and other in our projections, but are slightly over-projected for overall and significantly over-projected for black and asian. The peak timing is also well captured by our projections.

## Distribution of susceptibility at the start of the projection period? 
Susceptibility of each racial/ethnic group at the start of the projection period depends on race/ethnicity specific prior infections, which are derived from serology data and imputed R/E specific cases data.

## Which disease datasets (serology, cases, cases with imputed race/ethnicity information provided by coordination team, hospitalizations, deaths) were used for calibration?
We use serology, imputed race/ethnicity specific cases, and race/ethnicity specific deaths data sets provided by coordination team for calibration.

## How were the transmission (P(infection)) and severity (P(death|infection) risks estimated across racial/ethnic groups? 
The transmission risks across racial/ethnic groups are partly modeled in our contact networks, as results of R/E specific demographic distributions and activity/mobility patterns, and also estimated in our calibration of R/E specific transmissibility parameters. The severity risks across racial/ethnic groups are estimated through calibration of R/E specific IFR using serology and deaths data sets.

## How was the suppression of deaths handled in calibration? 
We added "value" and "min_suppressed" columns in the target data to get deaths for calibration.

## Details about calibration of race/ethnicity showing zero deaths throughout the calibration period (e.g., Others in CA and Asian in NC)? 
We used "value + min_suppressed" from the target data and did not have any race/ethnicity group with zero deaths.

## How was contact mixing between racial/ethnic groups characterized? Was a contact matrix (either population-level or setting-specific) used? If so, describe the process used to apply the contact matrix.)
We do not use an explicit contact matrix. Instead, the contact mixing between R/E groups comes from our synthetic population and network modeling, where we assign R/E to each individual based on R/E specific distributions and assign activities and activity locations to each individual based on their R/E (and other demographic attributes).

## Was mobility data used throughout the calibration/projection period? 
Mobility data was used to derive a relative adjustment factor for scaling the transmissibility throughout the projection period.

## Besides transmission, severity risk and contact matrices, did any other parameters vary by race/ethnicity (e.g., case reporting, NPI compliance)? 
Case ascertainment rate varied by race/ethnicity.

## How was the introduction of more transmissible variants modeled? 
We assumed that when the new variant emerged, 0.5% of the infections were new variant; and calibrated the emerging time towards 66% prevalence of new variant in mid-April 2021.

## How were NPIs implemented? 
We implemented (1) school closure with 65% compliance which removes in-school contacts of those who comply, (2) mask wearing outside of the household with 85% compliance which reduces transmission risk of compliant people by 60%, and (3) mobility changes in the projection period as a scaling on the transmissibility parameter.

## What was assumed about immunity/protection following infection? 
Natural immunity (from infection) provides 100% protection against infection. Vaccinal immunity (from vaccination) provides no protection against infection but reduces risk of symptomatic infection.

## How was vaccination implemented? What was assumed about immunity/protection following vaccination? 
To implement vaccination, we move a vaccinated node to a vaccinated state V1 after one dose or V2 after two doses, which has the same susceptibility to infection, but if infected has reduced probability (50% reduction with one dose, 95% reduction with two doses) of becoming symtomatic. This subsequently reduces risk of severe outcomes including IFR.

## Was age modeled in addition to race/ethnicity? Was there consideration for differences in the age structure across racial/ethnic populations? 
We model age (and race/ethnicity) explicitly at individual level in our agent-based model. The joint distribution of age and race/ethnicity is reflected in our synthetic population and heterogeneities between these demographic groups are reflected in our contact network. Our disease model has age and race/ethnicity stratifications.

## Was there importation of cases (e.g. from another external state)? 
We do not consider importations.
