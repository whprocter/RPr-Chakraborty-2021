# Rpr-Reproduction of Social Inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S.

Joseph Holler, Department of Geography, Middlebury College, Middlebury VT 05753  
Derrick Burt, Department of Geography, Middlebury College, Middlebury VT 05753  
Drew An-Pham, Department of Geography, Middlebury College, Middlebury VT 05753  
Peter Kedron, School of Geographical Sciences and Urban Planning, Arizona State University, Tempe AZ 85281  

Version 1.1 | Created Jul 7, 2021 | Last Updated June 1, 2022

## Abstract

Chakraborty (2021) investigates the relationships between COVID-19 rates and demographic characteristics of people with disabilities by county in the lower 48 states.
The study aims to examine public concern that persons with disabilities (PwDs) face disproportionate challenges due to COVID-19.
To investigate this, Chakraborty examines the statistical relationship between confirmed county-level COVID-19 case rates and county-level socio-demographic and disability variables.
Specifically, Chakraborty tests county-level bivariate correlations between COVID-19 incidence against the percentage of disability and socio-demographic category, with a separate hypothesis and model for each subcategory within disability, race, ethnicity, age, and biological sex.
To control for differences between states and geographic clusters of COVID-19 outbreaks, Chakraborty uses five generalized estimating equation (GEE) models to predict the relationship and significance between COVID-19 incidence and disability subgroups within each socio-demographic category while considering inter-county spatial clusters.
Chakraborty (2021) finds significant positive relationships between COVID-19 rates and socially vulnerable demographic categories of race, ethnicity, poverty, age, and biological sex.

This reproduction study is motivated by expanding the potential impact of Chakraborty's study for policy, research, and teaching purposes.
Measuring the relationship between COVID-19 incidence and socio-demographic and disability characteristics can provide important information for public health policy-making and resource allocation.
A fully reproducible study will increase the accessibility, transparency, and potential impact of Chakraborty's (2021) study by publishing a compendium complete with metadata, data, and code.
This will allow other researchers to review, extend, and modify the study and will allow students of geography and spatial epidemiology to learn from the study design and methods.

In this reproduction, we will attempt to identically reproduce all of the results from the original study.
This will include the map of county level distribution of COVID-19 incidence rates (Fig. 1), the summary statistics for disability and sociodemographic variables and bivariate correlations with county-level COVID-19 incidence rate (Table 1), and the GEE models for predicting COVID-19 county-level incidence rate (Table 2).
A successful reproduction should be able to generate identical results as published by Chakraborty (2021).

The reproduction study data and code will be made available in a GitHub repository to the greatest extent that licensing and file sizes permit.
The repository will be made public at [github.com/HEGSRR/RPr-Chakraborty2021](https://github.com/HEGSRR/RPr-Chakraborty2021).
To the greatest extent possible, the reproduction will be implemented with R markdown using packages geepack for the generalized estimating equation and SpatialEpi for the spatial scan statistics.

Chakraborty, J. 2021. Social inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S. *Disability and Health Journal* **14**:1-5. DOI:[10.1016/j.dhjo.2020.101007](https://doi.org/10.1016/j.dhjo.2020.101007)

### Keywords

COVID-19; Disability; Intersectionality; Race/ethnicity; Poverty; Reproducibility

## Study design

The reproduction study will try to implement the original study as closely as possible to reproduce the map of county level distribution of COVID-19 incidence rate, the summary statistics and bivariate correlation for disability characteristics and COVID-19 incidence, and the generalized estimating equations.
Our two confirmatory hypotheses are that we will be able to exactly reproduce Chakraborty's results as presented in figure 1, table 1, and table 2 of Chakraborty (2021). Stated as null hypotheses:

> H1: There is a less than perfect match between Chakraborty's bivariate correlation coefficient for each disability/sociodemographic variable and COVID-19 incidence rate and our bivariate correlation coefficient for each disability/sociodemographic variable and COVID-19 incidence rate.

> H2: There is a less than perfect match between Chakraborty's beta coefficient for the GEE of each disability/sociodemographic variable and our beta coefficient for the GEE of each disability/sociodemographic variable.

There are multiple models being tested within each of the two hypotheses. That is, H1 and H2 both encompass five models, including one for each dimension of socio-demographics: race, ethnicity, poverty status, age, and biological sex.

### Original study design

The original study is **observational**, with the **exploratory** objective of determining "whether COVID-19 incidence is significantly greater in counties containing higher percentages of socio-demographically disadvantaged [people with disabilities], based on their race, ethnicity, poverty status, age, and biological sex" (Chakraborty 2021).
This exploratory objective is broken down into five implicit hypotheses that each of the demographic characteristics of people with disabilities is associated with higher COVID-19 incidence rates.

The **spatial extent** of the study are the 49 contiguous states in the U.S.
The **spatial scale** of the analysis is at the county level.
Both COVID-19 incidence rates and demographic variables are all measured at the county level.
The **temporal extent** of the COVID-19 data ranges from 1/22/2020 (when John Hopkins began collecting the data) to 8/1/2020 (when the data was retrieved for the original study).
The data on disability and sociodemographic characteristics come from the U.S. Census American Community Survey (ACS) five-year estimates for 2018 (2014-2018).

There is no **randomization** in the original study.

The study was originally conducted using SaTScan software (unspecified version) to implement the spatial scan statistic.
Other software are not specified in the publication; however data files and communication with the author show that spatial analysis and mapping was conducted in ArcGIS and statistics were calculated in SPSS.

Our understanding of the original study design and our plan for the reproduction analysis are visualized in the workflow diagram.

![workflow](workflow.jpg)
*Figure 1*

## Sampling plan

### Existing data and data exploration

This registration is based upon a thorough reading of the original research article, searching and calculating summary statistics for American Community Survey data, accessing the Johns Hopkins Coronavirus Resource Center, and acquiring some additional information and data from the original author, Jay Chakraborty.
Specifically, Chakraborty informed us of the American Community Survey data table names used in the study (S1810 for demographic categories and disability status and C18130 for poverty status and disability status), provided Johns Hopkins county-level Coronavirus data downloaded on August 1, 2020, outputs from SaTScan spatial clustering analysis, and inputs for the GEE models.
The data provided by the author is not available in an online repository, but we will include the data in our research compendium with permission of the author.

In our reproduction attempt, we will use publicly available American Community Survey data downloaded directly from the Census API using the tidycensus package for R.
We will use Johns Hopkins Coronavirus data provided by the author because it is not possible to download that dynamic dataset in an archived form as it existed on August 1, 2020.
Johns Hopkins still provides aggregated COVID-19 incidence rate data, but does not publicly provide archived data identical to those used in the original study.
In preparing this preanalysis plan, we have only accessed data, viewed metadata, calculated summary statistics, and corresponded with the original author as described above.

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

The 2018 ACS 5 year estimates for disabilities can be accessed from the U.S. Census website or through the Census API.

## Variables

All variables in this study were derived from secondary data.
There are no experimentally manipulated variables in this experiment.
Eighteen independent variables, a percentage of total disabled persons per county and seventeen 'disaggregated' categories that break down socio-demographic characteristics of the disabled population.
COVID-19 incidence rate can be seen as the dependent variables.

The socio-demographic variables are broken down into the following categories.
Their table code from the ACS data has been included in this documentation

##### COVID-19 incidence rate

- cases per 100,000 people

##### Persons with disabilities

The American Community Survey (ACS) variables used in the study are outlined below.

Variable Name in Study | ACS Variable name
--- | ---
percent of total civilian non-institutionalized population with a disability | S1810_C03_001E
**Race** |
percent w disability: White alone | S1810_C03_004E
percent w disability: Black alone | S1810_C03_005E
percent w disability: Native American | S1810_C03_006E
percent w disability: Asian alone | S1810_C03_007E
percent w disability: Other race | S1810_C03_009E
**Ethnicity** |
percent w disability: Non-Hispanic White | S1810_C03_0011E
percent w disability: Hispanic | S1810_C03_012E
percent w disability: Non-Hispanic non-White | (S1810_C02_001E - S1810_C02_011E - S1810_C02_012E) / (S1810_C01_001E - S1810_C01_011E - S1810_C01_012E) * 100
percent w disability: Other race | S1810_C03_009E
**Poverty** |
percent w disability: Below poverty level | (C18130_004E + C18130_011E + C18130_018E) / C18130_001E * 100
percent w disability: Above poverty level | (C18130_005E + C18130_012E + C18130_019E) / C18130_001E * 100
**Age** |
percent w disability: 5-17 | S1810_C03_014E
percent w disability: 18-34 | S1810_C03_015E
percent w disability: 35-64 | S1810_C03_016E
percent w disability: 65-74 | S1810_C03_017E
percent w disability: 75+ | S1810_C03_018E
**Biological sex** |
percent w disability: male | S1810_C03_001E
percent w disability: female | S1810_C03_003E

#### Attribute variable transformations

The COVID-19 incidence rate is normalized at the county-level per 100,000 people.
All of the disability and sociodemographic variables are provided in the format that they are used, as a percentage of "people with disabilities in each subgroup by the total civilian non-institutionalized population relevant to the variable category" (Chakraborty 2011).

Before conducting the GEE, all independent variables are normalized into z-scores.

For the GEE, two different clustering scores are assigned to each county.
The first clustering score is just a categorical variable determined by the counties' state.
The second clustering score is a relative risk score calculated by identifying spatial clusters from a spatial scan statistic based on the Poisson Model.
We calculate the clusters using the spatial scan statistics package. We then calculate the relative risk score for each county using the formula: (rate of cases within the cluster) / (rate of cases outside the cluster). This is then classified into six categories based on the estimated relative risk values (<1.0, 1.00-1.99, 2.00-2.99, 3.00-3.99, 4.00-4.99, and 5.0 or more). The data is combined with the American Community Survey data to be used as input to the GEE models.

#### Geographic transformations

Although there are no explicit geographic transformations in this experiment, the variable transformations that occur during the SaTScan procedure are geographic in nature: they assign values based on spatial clustering of COVID-19 risk, which are subsequently used to define clusters in the GEE models.

Having looked at the SaTScan outputs from the original study, our best guess is that the author might have calculated centroids for each county before running the GEE, using a geographic coordinate system.

## Analyses


### Geographical characteristics

The **coordinate reference system** is not specified in the methodology.
Census data is provided in the NAD1983 Geographic Coordinate System.
We assume that the analysis was also conducted the NAD1983 Geographic Coordinate System because the SaTScan can perform a spherical distance calculation using latitude and longitude.

The **spatial extent** of the study were the contiguous 49 United States (including the District of Columbia).

The **spatial scale** and **unit of analysis** of the study is are U.S. counties.

**Edge effects** will not be accounted for in the analysis.

This analysis does create **spatial subgroups** based on **spatial clustering**.
The purpose of this grouping is to control for **spatial heterogeneity** between regions (defined as states) and spatial correlation within regions.
There are criteria for two different types of spatial clustering; we address these in the attribute variable transformation section.

This analysis does not measure or account for any **first order spatial effects**, **second order spatial effects**, or **spatial anisotropies**.

### Temporal characteristics

The **temporal extent** of the study is based on the COVID-19 incidence rate, which covers cases from 1/22/2020-8/1/2020.
The study also uses 5 year estimates for county disability and sociodemographic characteristics collected from 2014-2018.
This range is not explicitly stated in the original study.

The **temporal support** for the COVID-19 incidence rate was case data collected from 1/22/2020-8/1/2020.
The **temporal support** for the disability sociodemographic data was data collected from 2014-2018.
**Temporal effects** are not measured or accounted for.

### Data exclusion

There is no documentation of any **data exclusion** based on attribute criteria in the original study.

The study does not analyze the presence of **outliers**.
The study does not **weight samples**.

### Analytical specification

The county-level Pearson's rho correlation coefficient is used to test association between intra-categorical rates of disability and COVID-19 incidence rates.
As this is a parametric test, normality should be tested.
A separate hypothesis is formulated for each sociodemographic disability characteristic.

The generalized estimating equation models are used to test association between intra-categorical rates of disability and COVID-19 incidence rates while accounting for spatial clustering.
As specified by the author, "GEEs extend the generalized linear model to accommodate clustered data, in addition to relaxing several assumptions of traditional regression (i.e., normality)".
Additionally, the author notes that "clusters of observations must be defined based on the assumption that observations within a cluster are correlated while observations from different clusters are independent."

### Inference criteria and robustness

To make inferences, p-values and correlation coefficients are checked.

For the bivariate correlation, Pearson's rho coefficients with two-tailed p-values (p<0.01; p<0.05) were used to test significance for all independent variables.
The author of the original study seems to place more emphasis on the significance and direction of the coefficient than the magnitude.
Overall model fit was not checked.

For the GEE, Beta coefficients with two tailed p-values for a Wald chi-square test (p<0.01; p<0.05) were used to test significance of all independent variables.
The author of the original study places more emphasis on the significance and direction of the coefficient than the magnitude.
To check robustness, the author notes that GEEs "require the specification of an intra-cluster dependency correlation matrix. The 'exchangeable correlation matrix was selected for the results reported [here], since this specification yielded the best statistical fit based on the QIC model criterion".
Further, the author describes: "for each GEE, the normal, gamma, and inverse Gaussian distributions with logarithmic and identity link functions were explored.
The gamma distribution with logarithmic link function was chosen for all GEEs since this model specification provided the lowest QIC value."

### Exploratory analyses and contingency planning

There are no **exploratory** analyses in this analysis.
There is no need for a **contingency plan** in this study.

## Reproduction study design

### Planned differences from the original study

We plan to implement the analysis to the greatest extent possible in R / RStudio, using the geepack for the generalized estimating equation and SpatialEpi for the spatial scan statistics, whereas the original study was conducted using ArcGIS (Desktop v 10.7), SPSS, and SaTScan (v9.6).

We will plan to check the normality of our distribution of our independent variables before correlations. If they are not normal, we may choose to calculate the bivariate correlation using a Spearman's Rho.

### Evaluating the reproduction results

Before comparing results from our reproduction of the statistical models, we plan to compare summary statistics for all of our dependent and independent variables to those of the original study to confirm we are using the same inputs.

In order to test the results for both our bivariate correlation and GEE, we plan to compare the difference between our correlation coefficients and the original study's correlation coefficients.
If there are any non-zeroes, we will investigate further.
We will consider the reproduction an exact reproduction only if we can create identical coefficients for the Pearson's Rho bivariate tests of table 1 and the GEE models of table 2.
We will consider the reproduction to be approximate if we find coefficients with the same direction and significance levels as the original study.
We will consider the reproduction to have at least partially failed if we find coefficients with different directions or significance levels.

## Unplanned deviations

In our pre-analysis plan, we planned to test the independent variables for normality prior to using the Pearson's r correlation coefficient for bivariate tests of correlation between the independent variables and COVID-19 incidence rates.
Most of the independent variables do have non-normal distributions, therefore our reproduction has used the nonparametric Spearman's rank correlation coefficient for bivariate tests of correlation between the independent variables and COVID-19 incidence rates.

The original study did not directly report details for the results of the spatial scan statistic for COVID-19 clusters beyond the number of clusters detected.
In order to better understand the spatial scan statistic and to compare our reproduction with the SpatialEpi package to the original study using SaTScan software, we also ran the spatial scan statistic in SaTScan.
SaTScan produced three outputs:
- text file report of each cluster
- vector layer of circle polygons with the center and radius of each cluster, ID of the county at the center of the cluster, and a relative risk score for the cluster. The layer contained one feature for each cluster, identifying only the county at the center of the cluster.
- vector layer of points of the centroids of each county in any cluster, including a unique cluster ID, relative risk score of the cluster, and relative risk score of the location (the county).

Comparing our results to the original publication, data files provided by the author, and the number of clusters for GEE models, we discovered that the original study *most likely* conceptualized COVID-19 clusters as the cluster-based relative risk of the county at the center of the cluster.
Counties inside of a cluster but not at its center were excluded in the original study.
Additionally, the SpatialEpi package did not calculate relative risk.

Therefore, we changed our conceptualization of COVID-19 clusters to include all counties within any cluster.
We created a list of all county IDs in clusters derived from the SpatialEpi output and joined this information to the complete geographic layer of counties.
We then calculated a local relative risk score for each county in a cluster and classified the risk score from 1 to 6.
This method left null data for all of the counties outside of a cluster.
We inspected the original author's GEE input data to determine how to classify these counties, and accordingly assigned them to the 1 class.

While reproducing the study, we decided that additional data visualizations would improve our understanding of the spatial patterns and relationships in the study.
Therefore, we also created maps visualizing disability rates by county, spatial clusters of COVID-19 incidence according to the spatial scan statistic, and of the original and reproduced relative risk categories.

## Reproduction result

The first part of our reproduction analysis was to visualize the spatial distribution of COVID-19 cases per 100,000 in the US (Figure 2). The reproduction result closely resembled that of the original study.

![tmap1](../../results/figures/covid_rates.png)
*Figure 2*

In addition, we proceeded to create a map that illustrated the percentages of population with disability in each county (Figure 3).

![tmap2](../..//results/figures/disability_rates.png)
*Figure 3*

The second part of our reproduction analysis focused on computing the summary statistics for variables analyzed and the bivariate correlations with county COVID-19 incidence rates.
Our summary statistics and the Pearson's correlation coefficient were consistent with that of Chakraborty's, but slightly differ in magnitude (which might be due to the different ways of computing statistics in different computational environments).
Since the Pearson's correlation should only be used on variables with normal distribution, we then calculated the Spearman's Rho correlation coefficient (Table 1).
There seems to be more changes to the result in terms of their magnitude and direction.
For example, while the Pearson’s correlation coefficient shows a weak positive relationship between “COVID-19 incidence rate” and “Percentages with disability that are Native American” and “Percentages with disability that are female”, these turned into a weak negative relationship in Spearman’s correlation coefficient.

*Table 1*: Spearman's Ranked Correlation Coefficient between COVID-19 Incidence and Disability Subgroups

|Variable               |    rho|      t|     p|
|:----------------------|------:|------:|-----:|
|dis_pct                | -0.113|  6.312| 0.000|
|white_pct              | -0.421| 25.874| 0.000|
|black_pct              |  0.575| 39.163| 0.000|
|native_pct             | -0.084|  4.688| 0.000|
|asian_pct              |  0.194| 11.001| 0.000|
|other_pct              |  0.104|  5.825| 0.000|
|non_hisp_white_pct     | -0.454| 28.389| 0.000|
|hisp_pct               |  0.231| 13.210| 0.000|
|non_hisp_non_white_pct |  0.481| 30.564| 0.000|
|bpov_pct               |  0.062|  3.452| 0.000|
|apov_pct               | -0.205| 11.694| 0.000|
|pct_5_17               |  0.079|  4.411| 0.000|
|pct_18_34              |  0.034|  1.902| 0.029|
|pct_35_64              | -0.020|  1.136| 0.128|
|pct_65_74              | -0.151|  8.523| 0.000|
|pct_75                 | -0.285| 16.592| 0.000|
|male_pct               | -0.201| 11.430| 0.000|
|female_pct             | -0.014|  0.798| 0.212|

Although Chakraborty does not illustrate the classified relative risk of COVID-19 clusters, we enhanced the study by mapping both relative risk based on the SaTScan results (Figure 4) and on our modified R SpatialEpi results (Figure 5).

![tmap4](../../results/figures/rr_original.png)
*Figure 4: Relative risk score of original analysis*

![tmap3](../../results/figures/rr_reproduction.png)
*Figure 5: Relative risk score of reproduction analysis*

In the third part of our reproduction analysis, we implemented the GEE model (Table 2).
The results of our reproduction study are mostly consistent with that of from Chakraborty’s, with slight differences in the magnitude of correlation coefficients.
The significance of some of the results also changed:
the percent of Hispanics with disability changed from being significant to non-significant whereas the percentage of disabilities between 18-34 and 35-64 changed from being non-significant to significant.
This is in part due to one revision we have made to the Chakraborty’s work.

*Table 2*: Globalized Estimating Equation Model Outputs

|                         | Estimate| Std.err|      Wald| Pr(>&#124;W&#124;)|
|:------------------------|--------:|-------:|---------:|------------------:|
|Race Intercept           |    7.723|   0.076| 10336.073|              0.000|
|white_pct              |   -0.129|   0.007|   358.943|              0.000|
|black_pct              |    0.019|   0.008|     5.122|              0.024|
|native_pct             |    0.018|   0.005|    13.578|              0.000|
|asian_pct              |    0.022|   0.004|    28.546|              0.000|
|other_pct              |    0.022|   0.006|    14.714|              0.000|
|Ethnicity Intercept      |    7.716|   0.076| 10292.946|              0.000|
|non_hisp_white_pct     |   -0.150|   0.008|   365.943|              0.000|
|hisp_pct               |    0.006|   0.005|     1.658|              0.198|
|non_hisp_non_white_pct |    0.023|   0.008|     9.049|              0.003|
|Poverty Status Intercept |    7.774|   0.074| 10947.636|              0.000|
|bpov_pct               |    0.018|   0.006|     9.446|              0.002|
|apov_pct               |   -0.110|   0.007|   233.641|              0.000|
|Age Intercept            |    7.783|   0.073| 11483.331|              0.000|
|pct_5_17               |    0.022|   0.003|    39.514|              0.000|
|pct_18_34              |    0.014|   0.004|    14.751|              0.000|
|pct_35_64              |   -0.024|   0.007|    11.102|              0.001|
|pct_65_74              |   -0.056|   0.006|    97.325|              0.000|
|z_pct_75                 |   -0.053|   0.006|    77.410|              0.000|
|Biological Sex Intercept |    7.784|   0.073| 11427.103|              0.000|
|male_pct               |   -0.135|   0.008|   316.207|              0.000|
|female_pct             |    0.041|   0.006|    43.665|              0.000|


## Discussion

Differences in the GEE model can be explained by differences in our conceptualization of COVID-19 clusters.
The original study only calculates the relative risk score for the center of the cluster, whereas our reproduction analysis calculates the relative risk score for each county in the cluster.

## References

Chakraborty, J. 2021. Social inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S. *Disability and Health Journal* **14**:1-5. DOI:[10.1016/j.dhjo.2020.101007](https://doi.org/10.1016/j.dhjo.2020.101007)
