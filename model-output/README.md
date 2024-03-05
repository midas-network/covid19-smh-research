# Data submission instructions

This page is intended to provide teams with all the information they
need to submit scenarios.  

All projections should be submitted directly to the [model-output/](./) 
folder. Data in this directory should be added to the repository
through a pull request. 

Due to file size limitation, the file can be submitted in a in a 
`.parquet` or `.gz.parquet`.


----

## Subdirectory

Each sub-directory within the [model-output/](./) directory has the
format:

    team-model
    
where 

- `team` is the abbreviated team name and 
- `model` is the  abbreviated name of your model. 

Both team and model should be less than 15 characters, and not include
hyphens nor spaces.

----

## Metadadata

Each submission team should have an associated metadata file. The file should
be submitted with the first projection in the 
[model-metadata/](../model-metadata/) folder, in a file named: 
`team-model.yaml`.

For more information on the metadata file format, please consult the associated
[README](../model-metadata/README.md)

----

## Date/Epiweek information

For week-ahead scenarios, we will use the specification of epidemiological
weeks (EWs) [defined by the US CDC](https://ndc.services.cdc.gov/wp-content/uploads/MMWR_Week_overview.pdf)
which run Sunday through Saturday.

There are standard software packages to convert from dates to epidemic weeks
and vice versa. E.g. [MMWRweek](https://cran.r-project.org/web/packages/MMWRweek/) 
for R and [pymmwr](https://pypi.org/project/pymmwr/) and 
[epiweeks](https://pypi.org/project/epiweeks/) for python.

---

## Model Results

Each model results file within the subdirectory should have the following 
name

    YYYY-MM-DD-team-model.parquet
    
where

- `YYYY` is the 4 digit year,
- `MM` is the 2 digit month,
- `DD` is the 2 digit day,
- `team` is the teamname, and
- `model` is the name of your model.

"parquet" files format from Apache is "is an open source, column-oriented data
file format designed for efficient data storage and retrieval". Please find more
information on the [parquet.apache.com](https://parquet.apache.org/) website.

The "arrow" library can be used to read/write the files in 
[Python](https://arrow.apache.org/docs/python/parquet.html) and 
[R](https://arrow.apache.org/docs/r/index.html).
Other tools are also accessible, for example [parquet-tools](https://github.com/hangxie/parquet-tools)

For example, in R:
```
# To write "parquet" file format:
filename <- ”path/YYYY-MM-DD-team_model.parquet”
arrow::write_parquet(df, filename)
# with "gz compression"
filename <- ”path/YYYY-MM-DD-team_model.gz.parquet”
arrow::write_parquet(df, filename, compression = "gzip", compression_level = 9)

# To read "parquet" file format:
arrow::read_parquet(filename)
```

The date YYYY-MM-DD should correspond to the start date for scenarios
projection ("first date of simulated transmission/outcomes" as noted in the
scenario description on the main 
[README, Submission Information](https://github.com/midas-network/rsv-scenario-modeling-hub)).

The `team` and `model` in this file must match the `team` and `model` in the 
directory this file is in. Both `team` and `model` should be less than 15 
characters, alpha-numeric and underscores only, with no spaces or hyphens.

If the size of the file is larger than 100MB, it should be submitted in a 
`.gz.parquet` format. 

---

## Model results file format

The output file must contain eleven columns (in any order):

- `origin_date`
- `scenario_id`
- `target`
- `horizon`
- `location`
- `race_ethnicity`
- `output_type` 
- `output_type_id` 
- `value`
- `run_grouping`
- `stochastic_run`

No additional columns are allowed.

Each row in the file is a specific type for a scenario for a location on
a particular date for a particular target. 

#### Column format

|Column Name|Accepted Format|
|:---:|:---:|
|`origin_date`|character, date (datetime not accepted)|
|`scenario_id`|character|
|`target`|character|
|`horizon`|numeric, integer|
|`location`|character|
|`race_ethnicity`|character|
|`output_type`|character| 
|`output_type_id`|character, logical (if all `NA`)| 
|`value`|numeric|
|`run_grouping`|integer|
|`stochastic_run`|interger|

### `origin_date`

Values in the `origin_date` column must be a date in the format

    YYYY-MM-DD
    
The `origin_date` is the start date for scenarios (first date of 
simulated transmission/outcomes).
The "origin_date" and date in the filename should correspond.


### `scenario_id`

The standard scenario id should be used as given in in the scenario 
description in the [main README](https://github.com/midas-network/rsv-scenario-modeling-hub). 
Scenario id's include a capitalized letter and date as YYYY-MM-DD, e.g., 
`A-2020-05-01`.


### `target`

The submission can contain multiple output type information: 

- 100 to 300 representative trajectories from the model simulations. We 
  will call this format "sample" output type. For more information, please
  consult the [sample](./data-processed#sample) 
  section.
- A set of quantiles value for all the targets (except peak timing).
  We will call this format "quantile" output type. For more information, 
  please consult the [quantile](./data-processed#quantile) 
  section. 

The requested targets are (for "sample" type output):

- weekly incident infections
- weekly incident cases
- weekly incident deaths

Optional target (for "quantile" type output):

- quantile:
    - weekly cumulative hospitalizations
    - weekly incident hospitalizations
    - peak size hospitalizations

Values in the `target` column must be one of the following character strings:

- `"inc inf"`
- `"inc case"`
- `"inc death"`


#### inc inf

This target is the incident (weekly) infections
predicted by the model during the week that is N weeks after
`origin_date`.

A week-ahead scenario should represent the total number of new
infections occuring during a given epiweek (from Sunday through
Saturday, inclusive).

Projections of infections will be used to compare outputs between 
models but will not be evaluated against observations.  
 

#### inc case

This target is the incident (weekly) number of cases 
predicted by the model during the week that is N weeks after 
`origin_date`. 

A week-ahead scenario should represent the total number of new 
cases reported during a given epiweek (from Sunday through Saturday, 
inclusive).

Projections of infections will be used to compare outputs between 
models but will not be evaluated against observations. 


#### inc death

This target is the incident (weekly) number of deaths predicted 
by the model during the week that is N weeks after 
`origin_date`. 

A week-ahead scenario should represent the total number of new 
deaths reported during a given epiweek (from Sunday through 
Saturday, inclusive).

Predictions for this target will be evaluated compared to 
the death demographic data from The National Center for Health Statistics,
available in the 
[target-data](https://github.com/midas-network/covid19-smh-research/tree/main/target-data)
folder.


### `location`

Values in the `location` column must be: `"06"` for California 
and `"37"` for North Carolina.

Please note that when writing FIPS codes, they should be written in as a 
character string to preserve any leading zeroes.


### `output_type`

Values in the `output_type` column are either

- `"sample"` or 
- `"quantile"` (optional)


This value indicates whether that row corresponds to a "sample" scenario or a
quantile scenario, etc. 

**Scenarios must include "sample" scenario for every
  scenario-location-target-horizon-race_ethnicity group.**

### `output_type_id`

#### `sample`

For the simulation samples format only. Value in the `output_type_id` 
column is `NA`

The id sample number is input via two columns:

- `run_grouping`: This column specifies any additional grouping if it controls 
   for some factor driving the variance between trajectories (e.g., underlying 
   parameters, baseline fit) that is shared across trajectories in different 
   scenarios. I.e., if using this grouping will reduce overall variance 
   compared to analyzing all trajectories as independent, this grouping should 
   be recorded by giving all relevant rows the same number. If no such 
   grouping exists, number each model run independently. 
- `stochastic_run` : a unique id to differentiate multiple stochastic runs. If 
   no stochasticity: the column will contain an unique value

Both columns should only contain integer number. 

The submission file is expected to have in between 100 to 300 simulation 
samples (or trajectories) for each "group". 

For round 1 disparities, it is required to have the trajectories grouped at 
least by `"ethnicity"` and `"horizon"`, so it is required that the combination of 
the `run_grouping` and `stochastic_run` columns contains at least an unique
identifier for each group containing all the possible value for `"race_ethnicity"` 
and `"horizon"`.

Fore more information and examples, please consult the 
[Sample Format Wiki page](https://github.com/midas-network/rsv-scenario-modeling-hub/wiki/Sample-File-Format).

For example:

|origin_date|scenario_id|location|target|horizon|race_ethnicity|output_type|output_type_id|run_grouping|stochastic_run|value|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|2020-10-15|A-2020-05-01|06|inc case|1|asian|sample|NA|1|1||
|2020-10-15|A-2020-05-01|06|inc case|2|asian|sample|NA|1|1||
|2020-10-15|A-2020-05-01|06|inc case|3|asian|sample|NA|1|1||
||||||||||||
|2020-10-15|A-2020-05-01|06|inc case|1|asian|sample|NA|2|1||
|2020-10-15|A-2020-05-01|06|inc case|2|asian|sample|NA|2|1||
||||||||||||


#### `quantile` 

Values in the `output_type_id` column are quantiles in the format

    0.###

and `NA` in the `run_grouping` and `stochastic_run` columns.
    
For quantile scenarios, this value indicates the quantile for the `value` in
this row. 

Teams should provide the following 23 quantiles:

``` 
0.010 0.025 0.050 0.100 0.150 0.200 0.250 0.300 0.350 0.400 0.450 0.500
0.550 0.600 0.650 0.700 0.750, 0.800 0.850 0.900 0.950 0.975 0.990 
```

An optional `0`  and `1` value can also be provided.

For example:

|origin_date|scenario_id|location|target|horizon|age_group|output_type|output_type_id|run_grouping|stochastic_run|value|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|2023-11-12|A-2023-10-27|US|inc hosp|1|0-0.99|quantile|0.010|NA|NA||
|2023-11-12|A-2023-10-27|US|inc hosp|1|0-0.99|quantile|0.025|NA|NA||
||||||||||||


### `value`

Values in the `value` column are non-negative numbers indicating the associated
output_type prediction for this row. 


### `race_ethnicity` 

Accepted values in the  `race_ethnicity` column are:

- "asian"
- "black"
- "latino" (accepted only for California ("06"))
- "other"
- "black"

----

## Scenario validation

To ensure proper data formatting, pull requests for new data or updates in
model-output/ will be automatically validated

When a pull request is submitted, the data are validated by running the
scripts in [validation.R](../code/validation/validation.R). The intent for
these tests are to validate the requirements above and all checks are 
specifically enumerated 
[on the Validation wiki page]([https://github.com/midas-network/frsv-scenario-modeling-hub/wiki/Validation](https://github.com/midas-network/rsv-scenario-modeling-hub/wiki/Validation)).

Please [let us know](https://github.com/midas-network/rsv-scenario-modeling-hub/issues) if
the wiki is inaccurate or if any questions.

#### Workflow

When a pull request is submitted, the validation will be 
automatically triggered.

- If the pull request (PR) contains update on metadata 
and/or abstract file(s):
    - These files are manually validated, the automatic validation
    will only returns a message indicating it did not run any
    validation. 

- If the PR contains model output submission file(s). The validation 
automatically runs and output a message and a PDF file containing the 
quantiles projections of the requested targets at national and State
level (only if available in the submission file).

    - The validation has 3 possible output:
        - "Error": the validation has failled and returned a message 
        indicating the error(s). The error(s) should be fixed to have the PR 
        accepted
        - "Warning": the PR can be accepted. However, it might be necessary 
        for the submitting team to validate if the warning(s) is expected or 
        not before merging the PR.
        - "Success": the validation did not found any issue and returns a message 
        indicating that the validation is a success and the PR can be merged.


#### Run checks locally

To run these checks locally rather than waiting for the results from a pull
request, follow [these instructions](https://github.com/midas-network/rsv-scenario-modeling-hub/wiki/Validation#file-checks-running-locally)
(section File Checks Running Locally).



