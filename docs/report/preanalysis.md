# Pre-Registration of Rpr-Reproduction of Social Inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S.

Joseph Holler, Department of Geography, Middlebury College, Middlebury VT 05753 <br>
Peter Kedron, School of Geographical Sciences and Urban Planning, Arizona State University, Tempe AZ 85281 <br>
Drew An-Pham, Department of Geography, Middlebury College, Middlebury VT 05753 <br>
Derrick Burt, Department of Geography, Middlebury College, Middlebury VT 05753 <br>

Version 1.0 | Created Jul 7, 2021 | Last Updated Jul 22, 2021

## Abstract

Chakraborty (2020) investigates the relationships between COVID-19 rates and demographic characteristics of people with disabilities by county in the lower 48 states.
The study aims to examine public concern that persons with disabilities (PwDs) face disproportionate challenges due to COVID-19.
To investigate this, Chakraborty examines the statistical relationship between confirmed county-level COVID-19 case rates and county-level socio-demographic and disability variables.
Specifically, Chakraborty tests county-level bivariate correlations between COVID-19 incidence against the percentage of disability and socio-demographic category, with a separate hypothesis and model for each subcategory within disability, race, ethnicity, age, and biological sex.
To control for differences between states and geographic clusters of COVID-19 outbreaks, Chakraborty uses five generalized estimating equation (GEE) models to predict the relationship and significance between COVID-19 incidence and disability subgroups within each socio-demographic category while considering inter-county spatial clusters.
Chakraborty (2020) finds significant positive relationships between COVID-19 rates and socially vulnerable demographic categories of race, ethnicity, poverty, age, and biological sex.

This reproduction study is motivated by expanding the potential impact of Chakraborty's study for policy, research, and teaching purposes.
Measuring the relationship between COVID-19 incidence and socio-demographic and disability characteristics can provide important information for public health policy-making and resource allocation.
A fully reproducible study will increase the accessibility, transparency, and potential impact of Chakraborty's (2020) study by publishing a compendium complete with metadata, data, and code.
This will allow other researchers to review, extend, and modify the study and will allow students of geography and spatial epidemiology to learn from the study design and methods.

In this reproduction, we will attempt to identically reproduce all of the results from the original study.
This will include the map of county level distribution of COVID-19 incidence rates (Fig. 1), the summary statistics for disability and sociodemographic variables and bivariate correlations with county-level COVID-19 incidence rate (Table 1), and the GEE models for predicting COVID-19 county-level incidence rate (Table 2).
A successful reproduction should be able to generate identical results as published by Chakraborty (2020).

The replication study data and code will be made available in a GitHub repository to the greatest extent that licensing and file sizes permit.
The repository will be made public at [github.com/HEGSRR/RPr-Chakraborty2020](https://github.com/HEGSRR/RPr-Chakraborty2020).
To the greatest extent possible, the reproduction will be implemented with (3.7.6) Jupyter Notebooks for implementation on the [CyberGISX platform](https://cybergisxhub.cigi.illinois.edu/) with Python (3.7.6) Jupyter Notebooks.

Chakraborty, J. 2021. Social inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S. *Disability and Health Journal* **14**:1-5. DOI:[10.1016/j.dhjo.2020.101007](https://doi.org/10.1016/j.dhjo.2020.101007)

### Keywords

COVID-19; Disability; Intersectionality; Race/ethnicity; Poverty; Reproducibility

## Study design

The reproduction study will try to implement the original study as closely as possible to reproduce the map of county level distribution of COVID-19 incidence rate, the summary statistics and bivariate correlation for disability characteristics and COVID-19 incidence, and the generalized estimating equations.
Our two confirmatory hypotheses are that we will be able to reproduce for all three portions of the analysis.
It should be noted that there are multiple hypotheses and models being tested within these hypotheses.

> H1: There is a less than perfect match between Chakraborty's bivariate correlation coefficient for each disability/sociodemographic variable and COVID-19 incidence rate and our bivariate correlation coefficient for each disability/sociodemographic variable and COVID-19 incidence rate.

> H2: There is a less than perfect match between Chakraborty's beta coefficient for the GEE of each disability/sociodemographic variable an statistics and our beta coefficient for the GEE of each disability/sociodemographic variable.


### Original study design

The original study is **observational**, with the **exploratory** objective of determining "whether COVID-19 incidence is significantly greater in counties containing higher percentages of socio-demographically disadvantaged [people with disabilities], based on their race, ethnicity, poverty status, age, and biological sex."
This exploratory objective is broken down into five implicit hypotheses that each of the demographic characteristics of people with disabilities is associated with higher COVID-19 incidence rates.

The **spatial extent** of the study are the 49 contiguous states in the U.S.
The **spatial scale** of the analysis is at the county level. Both COVID-19 incidence rates and demographic variables are all measured at the county level.
The **temporal extent** of the COVID-19 data ranges from 1/22/2020 (when John Hopkins began collecting the data) to 8/1/2020 (when the data was retrieved for the original study). The data on disability and sociodemographic characteristics come from the U.S. Census American Community Survey (ACS) five-year estimates for 2018 (2014-2018).

There is no **randomization** in the original study.

The study was originally conducted using SaTScan software (unspecified version) to implement the spatial scan statistic.
Other software are not specified in the publication; however data files and communication with the author show that spatial analysis and mapping was conducted in ArcGIS and statistics were calculated in SPSS.


## Sampling plan

### Existing data and data exploration

This registration is based upon a thorough reading of the original research article and an understanding of the Census data.

As of the 7/21/21 the data exist and we have accessed it, though no analysis has been conducted related to the research plan (including calculation of summary statistics). We have designed the reproduction design that is outlined below only making reference to the methodology outlined in the original paper.

Although the raw data from the original study is not available in an online repository, we received COVID-19 incidence rate data from the author and accessed the disability and sociodemographic website from the Census Bureau website.
We have not analyzed the data, but viewing the variable names and data dictionaries has aided our understanding of the original study design.

### Data collection and spatial sampling

The study exclusively uses secondary data sources.
The study does not sample from the secondary data sources.

The published results are based of COVID-19 cases reported at the county-level and this is not a sampled dataset.
The disability data from the ACS are collected at the county level.
Details on the data collection can be found at [https://www.census.gov/topics/health/disability/guidance/data-collection-acs.html](https://www.census.gov/topics/health/disability/guidance/data-collection-acs.html) and details on sampling methods can be found at [https://www.census.gov/programs-surveys/acs/technical-documentation/code-lists.html](https://www.census.gov/programs-surveys/acs/technical-documentation/code-lists.html).

## Data description

Although the data specifications are described in detail in the original study, none of the data from the original study is provided in an online repository.

We received the COVID-19 case data from 8/1/2020 from the author, as there is no readily apparent way to access archived data from the Johns Hopkins University Center for Systems Science Engineering database.
The COVID-19 case data expresses cumulative count of reported COVID-19 from 1/22/2020 to 8/1/2020. The data can be found at the John Hopkins CCSE COVID-19 Data Repository ([https://github.com/CSSEGISandData/COVID-19](https://github.com/CSSEGISandData/COVID-19)).
However, archived data only provides summaries at the national scale.

The 2018 ACS 5 year estimates for disabilities can be accessed from the U.S. Census website. **Need to add more detail here**

## Variables

All variables in this study were derived from secondary data.
There are no experimentally manipulated variables in this experiment.
Eighteen independent variables, a percentage of total disabled persons per county and seventeen 'disaggregated' categories that break down socio-demographic characteristics of the disabled population.
COVID-19 incidence rate can be seen as the dependent variables.

The socio-demographic variables are broken down into the following categories.
Their table code from the ACS data has been included in this documentation

##### COVID-19 incidence rate

- cases per 100,00

##### Persons with disabilities

- percent of total population with a disability
  - col ID: S1810_C03_001E

##### Race

- percent w disability: White alone
  - col IDs: S1810_C03_004E
- percent w disability: Black alone
  - col IDs: S1810_C03_005E
- percent w disability: Native American
  - colIDs: S1810_C03_006E
- percent w disability: Asian alone
  - colIDs: S1810_C03_007E
- percent w disability: Other race
  - colIDs: S1810_C03_009E

##### Ethnicity

- percent w disability: Non-Hispanic White
  - colID: S1810_C03_0011E
- percent w disability: Hispanic
  - col ID: **???**
- percent w disability: Hispanic Non-White taking the total and subtracting the other two
  - colID: S1810_C03_006E

##### Age

- percent w disability: 5-17
  - col IDs: S1810_C03_014E
- percent w disability: 18-34
  - col IDs: S1810_C03_015E
- percent w disability: 35-64
  - colIDs: S1810_C03_016E
- percent w disability: 65-74
  - colIDs: S1810_C03_017E
- percent w disability: 75+
  - colIDs: S1810_C03_018E

##### Biological sex

- percent w disability: male
  - col IDs: S1810_C03_001E
- percent w disability: female
  - col IDs: S1810_C03_003E

#### Attribute variable transformations

The attribute variable transformations are well documented in the paper.
The COVID-19 incidence rate is normalized at the county-level per 100,000 people.
All of the disability and sociodemographic variables are provided in the format that they are used, as a percentage of total people at the county-level.

Before conducting the GEE, all independent variables are normalized into z-scores.

For the GEE, two different clustering scores are assigned to each county.
The first clustering score is just a categorical variable determined by the counties state.
The second clustering score is a relative risk score calculated by identifying spatial clusters from a spatial scan statistic based on the Poisson Model.

#### Geographic transformations

Although there are no explicit geographic transformations in this experiment, the variable transformations that occur during the GEE are geographic in nature: they assign values based on spatial clustering or state.

Having looked at the SATSCAN outputs from the original study, our best guess is that the author might have calculated centroids for each county before running the GEE.

## Analyses


### Geographical characteristics

The **coordinate reference system** is not specified in the methodology. Without having performed the GEE clustering analysis before, we cannot say for sure whether this.
It seems, however, because the outputs are in lat/lon format, that the author used a geographic coordinate system to perform a geodesic calculation.

The **spatial extent** of the study were the contiguous 49 United States (including the District of Columbia).

The **spatial scale** and **unit of analysis** of the study is are U.S. counties.

**Edge effects** will not be accounted for in the analysis.

This analysis does create **spatial subgroups** based on **spatial clustering**.
The purpose of this grouping is to control for **spatial heterogeneity** between regions (defined as states) and different case rate intensity during the pandemic.
There are criteria for two different types of spatial clustering; we address these in the attribute variable transformation section.

This analysis does not measure or account for any **first order spatial effects**, **second order spatial effects**, or **spatial anisotropies**.


### Temporal characteristics

The **temporal extent** of the study is based on the COVID-19 incidence rate, which covers cases from 1/22/2020-8/1/2020.
The study also uses 5 year estimates for county disability and sociodemographic characteristics collected from 2014-2018.
This range is not explicitly stated in the original study.

The **temporal support** for the COVID-19 incidence rate was case data collected from 1/22/2020-8/1/2020. The **temporal support** for the disability sociodemographic data was data collected from 2014-2018.  **Temporal effects** are not measured or accounted for.

### Data exclusion

There is no documentation of any **data exclusion** based on attribute criteria in the original study.

The study does not analyze the presence of **outliers**. The study does not **weight samples**.

### Analytical specification

The county-level bivariate correlations are used to test association between intra-categorical rates of disability and COVID-19 incidence rates. Pearson's rho is the bivariate correlation coefficient.
As this is a parametric test, normality should be tested.
A separate hypothesis is formulated for each sociodemographic disability characteristic.

The generalized estimating equation models are used to test association between intra-categorical rates of disability and COVID-19 incidence rates while accounting for spatial clustering.
Beta is the correlation coefficient.
As specified by the author, "GEEs extend the generalized linear model to accommodate clustered data, in addition to relaxing several assumptions  of traditional regression (i.e., normality)".
Additionally, the author notes that "clusters of observations must be defined based on the assumption that observations within a cluster are correlated while observations from different clusters are independent."

### Inference criteria and robustness

To make inferences, p-values and correlation coefficients are checked.

For the bivariate correlation, Pearson's rho coefficients with two-tailed p-values (p<0.01; p<0.05) were used to test significance for all independent variables.
The author of the original study seems to place more emphasis on the significance and direction of the coefficient than the magnitude.
Overall model fit was not checked.

For the GEE, Beta coefficients with two tailed p-values for a Wald chi-square test (p<0.01; p<0.05) were used to test significance of all independent variables.
The author of the original study seems to place more emphasis on the significance and direction of the coefficient than the magnitude.
To check robustness, the author notes that GEEs "require the specification of an intra-cluster dependency correlation matrix. Th 'exchangeable correlation matrix was selected for the results reported [here], since this specification yielded the best statistical fit based on the QIC model criterion"

### Exploratory analyses and contingency planning



## Reproduction study design

### Planned differences from the original study

We plan to implement the analysis to the greatest extent possible in Python Jupyter notebooks on CyberGISX and in R / RStudio, whereas the original study was conducted using ArcGIS (dekstop v 10.7), SPSS, and SaTScan (v9.6).

Checking for normality before correlations or switching to a Spearman's Rho.

### Evaluating the reproduction results



## Referencing the original paper

Chakraborty, J. 2021. Social inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S. *Disability and Health Journal* **14**:1-5. DOI:[10.1016/j.dhjo.2020.101007](https://doi.org/10.1016/j.dhjo.2020.101007)

### Sections

1. Introduction
2. Methods
3. Results
4. Discussion
5. Conclusions

### Tables, figures, other elements

- F1 County level distribution of COVID-19 incidence rate (cases per 100,000 people) in the continental USA. August 1, 2020.
- T1 Summary statistics for variables analyzed and bivariate correlations with county COVID-19 incidence rate.
- T2 Generalized estimating equations (GEE) for predicting county COVID-19 incidence rate: Standardized model coefficients and significance.

## Other references
