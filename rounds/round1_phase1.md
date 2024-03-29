## Disparities Round

We observed disparities in COVID-19 outcomes by sociodemographic factors such as
age, location, race/ethnicity, occupation, and socioeconomic status, yet most
epidemiological models do not account for structural inequities that contribute
to differential transmission and severity risk among these groups. This round
aims to build multi-model capacity within the Scenario Modeling Hub to model
and project how disease is distributed differentially among racial/ethnic
subpopulations. A secondary goal is to retrospectively assess the COVID-19
disease burden that could have been averted if various sources of health
inequities were reduced or mitigated. The round will focus on two US states,
California and North Carolina, where more detailed epidemiological data are
available.

We have specified a set of scenarios and target outcomes to allow alignment of
model projections for collective insights. Scenarios have been designed in
consultation with academic modeling teams and government agencies (e.g., CDC).

### Disparities Round Phase 1: Can we accurately predict COVID-19 death disparities by race/ethnicity?

In Phase 1, teams will calibrate to case and death data by race/ethnicity from
5/1/2020 – 11/14/2020 and project forward 11/15/2020 – 4/3/2021 in a single
Scenario A. Teams are required to incorporate health inequities that contribute
to differential transmission risk and severity by race/ethnicity, where
severity is defined at the probability of death given infection. Teams will be
evaluated on their ability to model race/ethnicity-specific death time series
throughout the projection period in Phase 1. We will assume that we have
prescribed the perfect scenario conditions; thus full information about new
variant circulation, non-pharmaceutical interventions (NPIs) such as masking,
social distancing, and travel restrictions, mobility, and vaccine coverage is
known over the entire projection period. As a result, we will be able to test
the ability of models to project disparities over time, after controlling for
other epidemiological and behavioral uncertainties. Phase 1 features a single
scenario as follows: 

<img src= "https://github.com/midas-network/covid19-smh-research/blob/main/rounds/round1_viz/disparities_phase1.png">


### Assumptions

In this retrospective round, we are interested in assessing the ability of
modeling teams to capture the racial and ethnic distribution of deaths in
California and North Carolina. Therefore, we will provide information on
external circumstances that impacted disease dynamics throughout the projection
period, including new variants, state-specific nonpharmaceutical interventions
(NPIs), mobility, and the ramp up of vaccination during the projection period
November 2020-April 2021. 


#### New Variants
 

- The Alpha variant B.1.1.7 emerged and replaced the Wuhan strain during the
  projection period. Alpha B.1.1.7 became the dominant strain mid-March, and was
  reported to be ~40-60% more transmissible than the Wuhan strain with similar
  severity ([Sah et al. 2021](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8132270/), 
  [Yang et al. 2022](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8947836/), 
  [Ahmad et al. 2022](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9448317/), 
  [Lin et al. 2021](https://www.frontiersin.org/journals/public-health/articles/10.3389/fpubh.2021.775224/full)). 
  By mid-April 2020, B.1.1.7 represented [66%](https://www.cdc.gov/mmwr/volumes/70/wr/mm7023a3.htm?s_cid=mm7023a3_w) 
  of all sequenced cases in the United States.


#### Nonpharmaceutical interventions


- [California](https://calmatters.org/health/coronavirus/2021/03/timeline-california-pandemic-year-key-points/)
	- Nov 16, 2020: Mask wearing required in all settings outside of the 
	household and non-essential businesses closed. 
	- Nov 21, 2020: Curfews from 10pm-5am applied to all non-essential 
	businesses and households. 
	- Dec 3, 2020: Regional stay at home orders instituted. 
	- Jan 25, 2021: Regional stay at home orders and curfew are lifted.

- [North Carolina](https://www.huschblackwell.com/north-carolina-state-by-state-covid-19-guidance)
	- Nov 13, 2020: Indoor gatherings limited to 10 individuals. 
	- Nov 23, 2020: Masking required in non-household settings. 
	- December 11, 2020: Curfew instated from 10pm-5am. 
	- Feb 28, 2021: Curfew lifted, masking and social distancing still 
	required.
	- March 26, 2021: Restrictions on social distancing are lifted, masking 
	remains in place. 

- Schools were largely closed for the 2020-21 school year in both locations. 

- Weekly SageGraph mobility data is provided at the census tract level, in the 
  [disparities/mobility/](https://github.com/midas-network/covid19-smh-research_resources/tree/main/disparities#mobility) 
  folder of 
  [covid19-smh-research_resources](https://github.com/midas-network/covid19-smh-research_resources)
  GitHub Repositories. 
  Mobility data is sourced from 
  [Kang et al. 2021](https://www.nature.com/articles/s41597-020-00734-5). 


#### Vaccination

- Weekly cumulative age- and race/ethnicity-specific vaccination coverage is 
  provided at the state level in the 
  [disparities/vaccination/](https://github.com/midas-network/covid19-smh-research_resources/tree/main/disparities#vaccination) 
  folder of 
  [covid19-smh-research_resources](https://github.com/midas-network/covid19-smh-research_resources). Vaccination data is extracted from the 
  [CA DPH](https://data.ca.gov/dataset/covid-19-vaccine-progress-dashboard-data) and 
  [NCDPH](https://covid19.ncdhhs.gov/dashboard/data-behind-dashboards) vaccine 
  dashboards and report vaccination by age and race/ethnicity in separate time 
  series.  These dashboards report the number of partially (receiving  1 dose) 
  and fully vaccinated  individuals. We describe the details of the vaccination 
  rollout and effectiveness assumptions.  

- We summarize race/ethnicity vaccination data by state into the follow 
  sub-populations: 
      - California: Latino, White, Asian, Black, Other, Unknown
      - North Carolina: White, Asian, Black, Other, Unknown. Note here 
      that non-White Hispanic individuals are included in “Other.” 


- Vaccination rollout timelines
	1. California 
	([COVID-19 Vaccination Plan, CADPH](https://www.cdph.ca.gov/Programs/CID/DCDC/CDPH%20Document%20Library/COVID-19/COVID-19-Vaccination-Plan-California-Interim-Draft_V1.0.pdf), 
	[California: State-by-State COVID-19 Guidance, Husch Blackwell](https://www.huschblackwell.com/california-state-by-state-covid-19-guidance), 
	[Vaccines for People with High-Risk Medical Conditions or Disabilities, CADPH](https://www.cdph.ca.gov/Programs/CID/DCDC/Pages/COVID-19/vaccine-high-risk-factsheet.aspx))
		- December 15, 2020:  Vaccination begins for Phase 1A. Healthcare workers 
		and long-term care residents are eligible. 
		- January 13, 2021: Individuals 65+ years old are eligible for vaccination.
		- February 3, 2021: Phase 1B: Essential workers with high exposure risk 
		(those working in agriculture and food, education and childcare, and 
		emergency services) are eligible for vaccination. Vaccination sites are 
		also set up in Oakland and Los Angeles to prioritize communities that have 
		been heavily impacted by the COVID-19 pandemic. 
		- March 4, 2021: The state announces it will direct 40% of its vaccine supply 
		to vulnerable communities, based on the Healthy Places Index (HPI).
		- March 15, 2021: Individuals <65 and >16 years with high-risk conditions are 
		eligible for vaccination. 

	2. North Carolina 
	([North Carolina: State-by-State COVID-19 Guidance, Husch Blackwell](https://www.huschblackwell.com/north-carolina-state-by-state-covid-19-guidance))
	- January 20, 2021: Group 1: North Carolinians over the age of 65 and all health 
	care workers who have in-person contact with patients are eligible for vaccination.
	- Feb 9, 2020: Group 2: North Carolina mandates a subset of vaccines must go to every 
	geographic region and prioritizes vulnerable communities. 
	- Feb 25, 2021: Teachers and other Group 3 essential workers can get vaccinated. 
	- March 3, 2021: Additional essential workers in Group 3 can get vaccinated. 
	- March 24, 2021: People at higher risk from COVID-19 due to underlying medical 
	conditions will become eligible to receive a vaccine, as will people in certain 
	congregate-living settings (dorms).  
	- March 31, 2021: Group 4 eligible for vaccination. Essential workers now include 
	frontline workers who do not have to be in person for work and those in a range of 
	sectors such as construction, energy, financial services, public works, and others 
	as categorized by the 
	[Cybersecurity and Infrastructure Security Agency](https://www.cisa.gov/sites/default/files/publications/ECIW_4.0_Guidance_on_Essential_Critical_Infrastructure_Workers_Final3_508_0.pdf). 


### Calibration Data


Weekly case and death data by race/ethnicity are available for phase 1 and 2 in the
[target-data](./target-data/) folder. For more information, please consult the
documentation associated with the 
[disparities round target data](https://github.com/midas-network/covid19-smh-research/blob/main/target-data/README.md#disparities-round).


### Targets

In this round, the required target for trajectories will be **weekly incident
infections, cases, and deaths in California and North Carolina for a set of
specified racial/ethnic groups.** Trajectories will need to be paired across
racial/ethnic groups (i.e., for a given model, location, scenario and horizon,
all race/ethnicity data for simulation 1 corresponds to the sum of
race/ethnicity-specific estimates for simulation 1). 

In California, required racial/ethnic groups are `"latino"`, `"black"`, 
`"white"`, `"asian"`, and `"other"`, where `"other"` represents American Indian 
Alaska Native and Native Hawaiian and Pacific Islander. 

In North Carolina, required racial/ethnic groups are `"white"`, `"black"`, `"asian"`,
and `"other"`, where `"other"` represents non-White Hispanic and American Indian 
Alaska Native. 

Given the missingness in demographic disease data and limited data available on 
case reporting rates by race/ethnicity, infections and cases will not be evaluated. 

Teams will be submitting cases and infections for the purpose of model comparison and 
weekly death targets will be evaluated. 

### Additional Information

Auxiliary data and code are available in the 
[covid19-smh-research_resources](https://github.com/midas-network/covid19-smh-research_resources) 
GitHub repository,
[disparities folder](https://github.com/midas-network/covid19-smh-research_resources/tree/main/disparities)

The folder contains multiple sub-folders:

- Case Imputation: imputed case time series by race/ethnicity at the state level to 
  infer missing case demographic information
- Vaccination: vaccination time series by age and race/ethnicity
- Serology: monthly infection-based and combined vaccination/infection seroprevalence 
  time series
- Population Data: state-level population structure data by age and race/ethnicity
- Hospitalization: hospitalization time series by race/ethnicity, in a rate per 100,000 
  people for California and number of hospitalizations for North Carolina
- Contact Matrix: synthetic daily contact matrices by race/ethnicity in the household, 
  school, community, workplace setting in the pre-pandemic and pandemic period

### Submission Information

| Phase | Type | Scenario | Scenario name | Scenario ID for submission file (`scenario_id`) |
|:--------:|:--------:| ---------------------------------------------- |:-----------------:|:--------------------:|
|1| Projection  | Scenario A. Inequity-driven transmission and severity by race/ethnicity                        | phase_one      | A-2020-05-01 |

- End date for fitting data for Phase 1: Saturday November 14, 2020
- Start date for scenarios: Sunday November 15, 2020 (first date of simulated 
 transmission/outcomes)
- Simulation end date: April 3, 2021 (20-week horizon)
- **Phase 1 projections due: March 26, 2024**

##### Submission requirements

- Must consist of a subset of weekly targets from Sunday, November 15, 2020 - 
  Saturday, April 3, 2021 (20 week projection period). Weeks follow epi-weeks 
  (Sun-Sat) dated by the last day of the week. 

- Weekly targets: Weekly incident infections, cases, and deaths by location 
  and major racial/ethnic group. We require the following racial/ethnic groups 
  by state:
  	- California: `"latino"`, `"black"`, `"white"`, `"asian"`, and `"other"`. 
  	- North Carolina: `"black"`, `"white"`, `"asian"`, and `"other"`.

- 100-300 individual trajectories for each target. Trajectories should be sampled 
  in such a way that they will be most likely to produce the uncertainty of the 
  simulated process. 

- Metadata: We will require a brief meta-data from all teams.
