# Rpr-Reproduction of Social Inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S.

Joseph Holler, Department of Geography, Middlebury College, Middlebury VT 05753  
Junyi Zhou, Department of Geography, Middlebury College, Middlebury VT 05753  
Drew An-Pham, Department of Geography, Middlebury College, Middlebury VT 05753  
Derrick Burt, Department of Geography, Middlebury College, Middlebury VT 05753  
Peter Kedron, School of Geographical Sciences and Urban Planning, Arizona State University, Tempe AZ 85281  

Version 1.1 | Created Jul 7, 2021 | Last Updated July 11, 2022

## Abstract

Chakraborty (2021) investigates the relationships between incidence of confirmed COVID-19 cases and socio-demographic characteristics of people with disabilities by county in the lower 48 states and Washington D.C.
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

### Keywords

COVID-19; Disability; Reproducibility, United States, Kulldorff Spatial Scan Statistic, Generalized Estimating Equations

## Study design

The reproduction study will try to implement the original study as closely as possible to reproduce the map of county level distribution of COVID-19 incidence rate, the summary statistics and bivariate correlation for disability characteristics and COVID-19 incidence, and the effect estimates of the generalized estimating equations.
Our two confirmatory hypotheses are that we will be able to exactly reproduce Chakraborty's results as presented in figure 1, table 1, and table 2 of Chakraborty (2021).
Stated as null hypotheses:

> H1: There is a less than perfect match between Chakraborty's bivariate correlation coefficient for each disability/sociodemographic variable and COVID-19 incidence rate and our bivariate correlation coefficient for each disability/sociodemographic variable and COVID-19 incidence rate.

> H2: There is a less than perfect match between Chakraborty's GEE-based beta coefficient estimates for the of each disability/sociodemographic variable and our GEE-based beta coefficient estimates for the GEE of each disability/sociodemographic variable.

There are multiple models being tested within each of the two hypotheses.
*H1* compares the results 18 different bivariate correlation tests, while *H2* compares the results of 5 different generalized estimation equation models, including one for each dimension of socio-demographics: race, ethnicity, poverty status, age, and biological sex.

### Original study design

The original study is **observational**, with the **exploratory** objective of determining "whether COVID-19 incidence is significantly greater in counties containing higher percentages of socio-demographically disadvantaged [people with disabilities], based on their race, ethnicity, poverty status, age, and biological sex" (Chakraborty 2021).
The independent variables are derived from Census crosstabulations between people with disabilities and different socio-demographic categories.
For example, the independent variable `white people with disabilities` is the number of people with disabilities identifying as one race (white) divided by the total number of people for whom disability and race status are determined.
This exploratory objective is broken down into five implicit hypotheses that each of the demographic characteristics of people with disabilities is associated with higher COVID-19 incidence rates.

The **spatial extent** of the study are the 48 contiguous states and Washington D.C. in the U.S.
The **spatial scale** of the analysis is at the county level.
Both COVID-19 incidence rates and demographic variables are all measured at the county level.
The **temporal extent** of the COVID-19 data ranges from 1/22/2020 (when John Hopkins began collecting the data) to 8/1/2020 (when the data was retrieved for the original study).
The data on disability and sociodemographic characteristics come from the U.S. Census American Community Survey (ACS) five-year estimates for 2018 (2014-2018).

There is no **randomization** in the original study.

The study was originally conducted using SaTScan software (citing version 9.6) to implement the spatial scan statistic.
Other software are not specified in the publication; however data files and communication with the author show that spatial analysis and mapping was conducted in ArcGIS and statistics were calculated in SPSS.

Our understanding of the original study design and our plan for the reproduction analysis are visualized in the workflow diagram (Figure 1).
![workflow](workflow.jpg)
*Figure 1*

## Sampling plan

### Existing data and data exploration

This registration was based upon a thorough reading of the original research article, searching and calculating summary statistics for American Community Survey data, accessing the Johns Hopkins Coronavirus Resource Center, and acquiring some additional information and data from the original author, Jay Chakraborty.
Specifically, Chakraborty informed us of the American Community Survey data table names used in the study (S1810 for demographic categories and disability status and C18130 for poverty status and disability status), provided Johns Hopkins county-level Coronavirus data downloaded on August 1, 2020, outputs from SaTScan spatial clustering analysis, and inputs for the GEE models.
The data provided by the author is not available in an online repository, but we will include the data in our research compendium with permission of the author.

In our reproduction attempt, we used publicly available American Community Survey data downloaded directly from the Census API using the tidycensus package for R.
We used Johns Hopkins Coronavirus data provided by the author because it is not possible to download that dynamic dataset in an archived form as it existed on August 1, 2020.
Johns Hopkins still provides aggregated COVID-19 incidence rate data, but does not publicly provide archived data identical to those used in the original study.
This pre-analysis plan was based on information from the original paper, correspondence with the original author (as described above), viewing metadata and data sources provided by the author and the U.S. Census, and calculating summary statistics.  

*Disclaimer*: For demonstration purposes, we were registering this plan *after* running the full analysis in R-studio, based upon our documented plan and knowledge of the study prior to completing the analysis.

### Data collection and spatial sampling

The study exclusively used secondary data sources.
The study did not sample from the secondary data sources.

The published results were based on COVID-19 cases reported at the county-level and this is not a sampled dataset.
The disability data from the ACS were collected at the county level.
Details on the data collection could be found at [https://www.census.gov/topics/health/disability/guidance/data-collection-acs.html](https://www.census.gov/topics/health/disability/guidance/data-collection-acs.html) and details on sampling methods could be found at [https://www.census.gov/programs-surveys/acs/technical-documentation/code-lists.html](https://www.census.gov/programs-surveys/acs/technical-documentation/code-lists.html).

## Data description

Although the data specifications are described in detail in the original study, none of the data from the original study is provided in an online repository.

We received the COVID-19 case data through 8/1/2020 from the author, as there is no readily apparent way to access archived data from the Johns Hopkins University Center for Systems Science Engineering database.
The COVID-19 case data expresses cumulative count of reported COVID-19 from 1/22/2020 to 8/1/2020. The data can be found at the John Hopkins CCSE COVID-19 Data Repository ([https://github.com/CSSEGISandData/COVID-19](https://github.com/CSSEGISandData/COVID-19)).
However, archived data only provides summaries at the national scale.

We accessed the 2018 ACS 5 year estimates for disabilities from the U.S. Census website. The data is also available through the Census API.

## Variables

All variables in this study were derived from secondary data.
There were no experimentally manipulated variables in this experiment.
COVID-19 incidence rate was used as the dependent variable.
Following the original study, we examined eighteen independent variables, a percentage of total disabled persons per county and seventeen 'disaggregated' categories that break down socio-demographic characteristics of the disabled population.


The socio-demographic variables are broken down into the following categories.
Their table code from the ACS data has been included in this documentation

##### COVID-19 incidence rate

COVID-19 Incidence is calculated as the number of known cases per 100,000 people, based upon the Johns Hopkins University COVID-19 Resource Center database.

##### Persons with disabilities

The American Community Survey (ACS) variables used in the study are outlined below.

*Table 1: Disability Subgroup Variables*

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
Most of the disability and sociodemographic variables are provided in the format that they are used, as a percentage of "people with disabilities in each subgroup by the total civilian non-institutionalized population relevant to the variable category" (Chakraborty 2011).
Non-Hispanic non-White, Below poverty level and Above poverty level are calculated as shown in Table 1 above.

Before conducting the GEE, all independent variables are normalized into z-scores.

For the GEE, two different clustering scores are assigned to each county.
The first clustering ID is a categorical variable determined by the counties' state.
The second clustering ID is a relative risk score calculated by identifying spatial clusters from a spatial scan statistic based on the Poisson Model.
We will calculate the clusters using the SpatialEpi package in R.
We then calculate the relative risk score for each county using the formula: ``(rate of cases within the cluster) / (rate of cases outside the cluster)``.
The relative risk score is then classified into six categories based on the estimated relative risk values (<1.0, 1.00-1.99, 2.00-2.99, 3.00-3.99, 4.00-4.99, and 5.0 or more).
The first clustering ID (State) and second clustering score (Classified Relative Risk) are combined to form IDs for each unique combination of state and relative risk class.
The clustering ID's will then be joined with the American Community Survey data on disability subgroups to be used as input to the GEE models.

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

> H1.1: There is no correlation between the COVID-19 incidence rate and the percentage of people with disabilities at the county level.
> H1.2: There is no correlation between the COVID-19 incidence rate and the percentage of white people with disabilities at the county level.
...
> H1.18 There is no correlation between the COVID-19 incidence rate and the percentage of female people with disabilities at the county level.

The generalized estimating equation (GEE) models are used to test association between intra-categorical rates of disability and COVID-19 incidence rates while accounting for spatial clustering.
Although the original publication does not clearly state hypotheses for each model, we may formulate null as follows:

> H2.1: The percentages of people with disability, categorized by race, are not associated with COVID-19 incidence at the county level when accounting for the state and risk level of COVID-19 clusters.
...
> H2.5: The percentages of people with disability, categorized by gender, are not associated with COVID-19 incidence at the county level when accounting for the state and risk level of COVID-19 clusters.

As specified by the author, "GEEs extend the generalized linear model to accommodate clustered data, in addition to relaxing several assumptions of traditional regression (i.e., normality)".
Additionally, the author notes that "clusters of observations must be defined based on the assumption that observations within a cluster are correlated while observations from different clusters are independent."
Following Chakraborty, all five GEE models will be specified with exchangeable correlation matrices, gamma distributions, and logarithmic link function.
These specifications were chosen after testing each alternative and choosing the models with the best quasilikelihood under the independence model criterion (QIC).

### Inference criteria and robustness

Bivariate inference will be assessed with correlation coefficients and p-values.

Multivariate inference will not be made because GEE models provide estimated coefficients for the independent variables and these are best interpreted as exploratory estimates.
Model fit will be assessed with QIC.
Statistical significance of independent variable coefficients will be tested with Wald Chi Square and assessed for the 0.01 and 0.05 confidence levels.

### Exploratory analyses and contingency planning

There are no **exploratory** analyses in this analysis.
There is no need for a **contingency plan** in this study.

## Reproduction study design

### Planned differences from the original study

We implemented the analysis to the greatest extent possible in R / RStudio, using the geepack package for the generalized estimating equation and SpatialEpi package for the spatial scan statistics, whereas the original study was conducted using ArcGIS Desktop (unknown version), SPSS (unknown version), and SaTScan (v9.6).

We will plan to check the normality of our distribution of our independent variables before correlations. If they are not normal, we may choose to calculate the bivariate correlation using a Spearman's Rho.

### Evaluating the reproduction results

Before comparing results from our reproduction of the statistical models, we plan to compare summary statistics for all of our independent variables to those of the original study to confirm we are using the same inputs.
We will compare the summary statistics (in table 1) and geographic distribution (in figure 1) of the dependent variable, COVID-19 incidence.

Considering that we will use a different computational environment from the original authors, we will compare the bivariate correlation coefficients and significance levels expecting extremely similar coefficients and p-values.

Considering that both the computational environment and some analytical decisions will vary in our reproduction of the clusters for GEE modeling, we will compare the coefficients and significance levels with expectation that the direction and significance level will be the identical, but magnitudes and Chi Square values may vary.

In order to test the results for both our bivariate correlation and GEE, we plan to construct tables (or matrices) that show the difference between our correlation coefficients and the original study's correlation coefficients.
If there are any non-zeroes, we will investigate further.

We will consider the reproduction an exact reproduction only if we can create identical coefficients for the Pearson's Rho bivariate tests of table 1 and the GEE models of table 2.
We will consider the reproduction to be approximate if we find coefficients with the same direction and significance levels as the original study.
We will consider the reproduction to have at least partially failed if we find coefficients with different directions or significance levels.

## Unplanned deviations

One county was unexpectedly missing disability and poverty data: Rio Arriba County, New Mexico.
We replaced the missing values with zeroes and, with this missing data treatment, confirmed that our descriptive statistics matched the original publication.

In our pre-analysis plan, we planned to test the independent variables for normality prior to using the Pearson's r correlation coefficient for bivariate tests of correlation between the independent variables and COVID-19 incidence rates.
Most of the independent variables have significantly non-normal distributions; and therefore our reproduction has used the nonparametric Spearman's rank correlation coefficient for bivariate tests of correlation between the independent variables and COVID-19 incidence rates.
In order to better understand the geographic patterns underlying the correlations between disability and COVID-19, we also visualized disability rates by county.

The original study did not directly report details for the results of the Kulldorff spatial scan statistic for COVID-19 clusters beyond the number of clusters detected.
In order to better understand the spatial scan statistic, and to compare our reproduction using the SpatialEpi package to the original study using SaTScan software, we also ran the spatial scan statistic in SaTScan.
SaTScan produced three outputs:
- text file report of each cluster
- vector layer of circle polygons with the center and radius of each cluster, ID of the county at the center of the cluster, and a relative risk score for the cluster. The layer contained one feature for each cluster, identifying only the county at the center of the cluster.
- vector layer of points of the centroids of each county in any cluster, including a unique cluster ID, relative risk score of the cluster, and relative risk score of the location (the county).

We compared our results to the original publication, data files provided by the author, and the number of clusters for GEE models.
We discovered that the original study most likely conceptualized COVID-19 clusters as the local relative risk of the county at the center of the cluster.
This conceptualization excluded all but the center county of each cluster and assigned the other counties to the lowest risk category.
Additionally, the SpatialEpi package did not calculate relative risk.

Therefore, we changed our conceptualization of COVID-19 clusters to include all counties within any cluster and to calculate relative risk for localities (counties) and clusters.
We calculated the local relative risk to investigate intra-cluster variations and created a map showing the relative risk score of each county.
To calculate the cluster relative risk, we created a list of unique cluster IDs and extracted the counties contained within each cluster from SpatialEpi output.
We combined these counties with their geographic, demographic, and COVID data to calculate and visualize cluster relative risk, classified on a scale from 1 to 6.
This approach left `null` data for all counties outside of any cluster.
We inspected the original author’s GEE input data to determine how to classify these counties, and accordingly assigned them to the 1 class.

At this point we considered the original purpose of calculating clusters and relative risk classes, which was to control for spatial dependence within states and COVID-19 hotspots.
In order to better understand how the original research used the Kulldorff spatial scan statistic, we decided that additional data visualizations would improve our understanding of the spatial patterns and better illustrate the differences in results.
We created maps visualizing the spatial clusters of COVID-19 incidence based on the output of SpatialEpi and SaTScan.
Since the local relative risk classification divided COVID-19 clusters into different classes, we also decided to calculate a cluster-based relative risk score similar to that of the SaTScan software.
We then re-classified each county based on this cluster relative risk and recalculated the generalized estimating equations using this alternative conceptualization of COVID-19 risk.

After finding our results differed from the original publication, we sought to confirm whether differences could be caused by the computational environment.
Therefore, we loaded data provided by the original author into R and used this original data as input to the GEE models.

## Reproduction result

The **first part** of our reproduction analysis was to visualize the spatial distribution of COVID-19 cases per 100,000 in the US (Figure 2). The reproduction result closely resembled that of the original study.

![tmap1](../../results/figures/covid_rates.png)
*Figure 2: Cumulative incidence rate of confirmed COVID-19 cases*

In addition, we proceeded to create a map that illustrated the percentages of population with disability in each county (Figure 3).

![tmap2](../..//results/figures/disability_rates.png)
*Figure 3: Percent of population with a disability*

The **second part** of our reproduction analysis focused on computing the summary statistics for variables analyzed and the bivariate correlations with county COVID-19 incidence rates.
Our summary statistics and Pearson's correlation coefficients were consistent with those of Chakraborty's, but differ slightly in magnitude.
Since the Pearson's correlation should only be used on variables with normal distribution, we calculated the Spearman's Rho correlation coefficient (Table 2).
There seems to be more changes to the result in terms of their magnitude and direction.
For example, while the Pearson's correlation coefficient shows a weak positive relationship between "COVID-19 incidence rate" and "Percentages with disability that are Native American" and "Percentages with disability that are female", these turned into weak negative relationships in Spearman's correlation coefficient.

*Table 2*: Spearman's Ranked Correlation Coefficient between COVID-19 Incidence and Disability Subgroups

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

Although Chakraborty does not illustrate the classified relative risk of COVID-19 clusters, we enhanced the study by mapping both relative risk based on the SaTScan results (Figure 4) and on our R SpatialEpi results (Figure 5).

![fig4](../../results/figures/rr_original.png)
*Figure 4: Relative risk score of original analysis*

![fig5](../../results/figures/rr_reproduction_loc.png)
*Figure 5: Local relative risk score of reproduction analysis*

On top of that, we calculated and mapped the relative risk score for each cluster (Figure 6).

![fig6](../../results/figures/rr_reproduction_cluster.png)
*Figure 6: Cluster based relative risk score of reproduction analysis*


In the **third part** of our reproduction analysis, we implemented the GEE model (Table 3).

The results of our reproduction study are mostly consistent with that of from Chakraborty's, with slight differences in the magnitude of correlation coefficients.
The significance of some of the results also changed: the percent of people with disability who fall into none of the racial group and percent of people with disability who are Hispanics changed from being significant to non-significant whereas the percentage of disabilities between 18-34 changed from being non-significant to significant.

*Table 3*: Globalized Estimating Equation Model Outputs

|                         | Estimate| Std.err|     Wald| Pr(>&#124;W&#124;)| Orig Coef| Coef Diff|
|:------------------------|--------:|-------:|--------:|------------------:|---------:|---------:|
| *Race Model* |
| Intercept           |    7.370|   0.083| 7813.513|              0.000|      7.11|      0.26|
|z_white_pct              |   -0.163|   0.010|  275.756|              0.000|     -0.20|     -0.04|
|z_black_pct              |    0.104|   0.011|   88.678|              0.000|      0.11|     -0.01|
|z_native_pct             |    0.036|   0.008|   21.126|              0.000|      0.05|     -0.02|
|z_asian_pct              |    0.039|   0.008|   21.766|              0.000|      0.08|     -0.04|
|z_other_pct              |    0.010|   0.010|    1.029|              0.310|      0.08|     -0.07|
| *Ethnicity Model* |
| Intercept      |    7.360|   0.083| 7769.795|              0.000|      7.19|      0.17|
|z_non_hisp_white_pct     |   -0.190|   0.012|  247.675|              0.000|     -0.24|     -0.05|
|z_hisp_pct               |    0.005|   0.027|    0.032|              0.857|      0.12|     -0.11|
|z_non_hisp_non_white_pct |    0.105|   0.011|   92.967|              0.000|      0.12|     -0.01|
| *Poverty Model* |
| Intercept |    7.382|   0.074| 9974.919|              0.000|      7.18|      0.20|
|z_bpov_pct               |    0.109|   0.018|   35.408|              0.000|      0.15|     -0.04|
|z_apov_pct               |   -0.194|   0.014|  204.920|              0.000|     -0.27|     -0.07|
| *Age Model* |
| Intercept            |    7.422|   0.077| 9253.948|              0.000|      7.24|      0.18|
|z_pct_5_17               |    0.028|   0.010|    7.132|              0.008|      0.05|     -0.02|
|z_pct_18_34              |    0.048|   0.018|    6.945|              0.008|      0.04|      0.01|
|z_pct_35_64              |   -0.014|   0.020|    0.481|              0.488|     -0.03|     -0.01|
|z_pct_65_74              |   -0.073|   0.017|   17.382|              0.000|     -0.09|     -0.02|
|z_pct_75                 |   -0.079|   0.013|   36.943|              0.000|     -0.11|     -0.03|
| *Biological Sex Model* |
| Intercept |    7.421|   0.077| 9279.250|              0.000|      7.22|      0.20|
|z_male_pct               |   -0.222|   0.016|  201.110|              0.000|     -0.30|     -0.08|
|z_female_pct             |    0.121|   0.017|   49.606|              0.000|      0.15|     -0.03|

## Discussion

Our reproduction of the original study was partially successful, leading to similar, but inexact results compared to the original study.
A portion of the inexactitude may be attributed to differences in the computational environments.
However, we have also reanalyzed the study and tested its robustness by changing some research parameters.
Our results suggest support for the conclusions of the original study, but also emphasize the importance of reproduction studies to understand the full details of the research design, to evaluate internal validity, and to test for uncertainty and robustness to key parameters.

The choropleth map we made in the **first part** of the reproduction analysis closely resembles that of the original study, confirming the equivalence of our dependent variable with that of the original study.
Both maps revealed that COVID-19 cases were distributed unevenly across space.
In particular, cases were more prevalent in the southern part of the country, in the metropolitan areas of the northeast, Chicago, and California, and in some rural areas, including eastern Washington, New Mexico, and Iowa.
Prior to Chakraborty's bivariate analysis of disability and COVID-19 incidence, we also mapped the spatial distribution of disability.
This spatial visual analysis reveals many regions in which disability rates are high but COVID-19 incidence was still low, including rural New England, Appalachia, and northern Michigan.
Conversely, many hotspots of COVID-19 incidence had low rates of disability, including metropolitan New England, South Florida, and Chicago.
The two spatial distributions help explain the negative bivariate relationship between disability rates and COVID-19 incidence.

The summary statistics for the **second part** of the reproduction analysis matched perfectly with those of the original study, confirming that the reproduction uses identical original data.
The Pearson's correlation coefficient closely resembled the original result, indicating a successful but inexact reproduction.
Differences in magnitude could be attributed to differences in the computational environments.
Nevertheless, our results validated the original findings by displaying a relatively weak but significantly negative correlation between COVID-19 incidence and the overall disability percentages in the country.
COVID-19 incidence was also found to be higher in counties where there are higher percentages of people with disabilities (PwDs) who are Black, Asian, Hispanic, non-Hispanic non-White, below poverty, and aged 5-34 years.
The original study used Pearson's correlation to test bivariate relationship between variables that are non-normally distributed, and we revised this to use the nonparametric Spearman's correlation coefficient.
Results indicate that biological sex might not be correlated with COVID-19 incidence rates, but other demographic factors of minority status were still significantly correlated with higher COVID-19 rates at the county level.

Results and interpretation of the Kulldorff spatial scan statistic varied significantly between the original study and our reproduction and re-analysis with regards to selection of secondary clusters, interpretation of clusters, and relative risk scores.
SatScan and SpatialEpi identify the same most likely cluster, but different sets of secondary clusters.
On one hand, SaTScan uses GINI statistics to select secondary clusters which maximize the difference between the population within clusters and the population outside of clusters, allowing for geographic overlap and finding 96 total clusters.
The original study used this default method.
On the other hand, SpatialEpi selects the most likely secondary clusters while excluding clusters with any geographic overlap, finding 135 total clusters.
This difference of parameters and computational environment explains the two different sets of clusters.
The different sets of secondary clusters largely agree in terms of the most likely cluster in a region and diverge in terms of overlapping, small, and less likely clusters.

In addition to the computational differences, the original study classified COVID risk using a local relative risk score for the county at the center of each cluster. Considering the relatively small number of clusters (102) compared to counties (3108), this method implies that the majority of counties in each state are classified as one low-risk cluster for the GEE analysis, and the remaining 53 clusters were composed of just a few counties at the centers of various COVID hotspots.
When we extended the interpretation of clusters to use the local relative risk score of any county within a cluster (Figure 5), we find significantly more variance in COVID risk within states, resulting in 139 unique GEE clusters.
However, this conceptualization apparently created GEE clusters defined in part by an ordinal classification of the dependent variable -- COVID incidence.
Considering that the original motivation for using GEE models was to account for spatial dependence within states (accounting for COVID response policy) and within COVID hotspots (accounting for the uneven geographic diffusion of the pandemic).
Therefore, a cluster-based relative risk classification seemed more appropriate than a local county-based relative risk classification, by applying the same risk level to the entire COVID cluster and allowing the GEE models to analyze variance within the clusters.
However, many of the most likely clusters extend across multiple states (see Figure 6, especially the southern states from Louisiana to South Carolina).
This resulted in creation of GEE clusters composed of every county within a state, amounting to 111 unique GEE clusters overall.

Our analysis of COVID-19 clusters in the context of controlling for spatial dependence has revealed several challenges and limitations to application of Kulldorff spatial scan statistics across different computational environments.
These include inconsistent methods for determining secondary clusters, limitation to circular or ellipsoidal cluster shapes, inclusion of single-county clusters, and choosing a method to control for spatial dependence in COVID 19 risk without controlling for too much of the variance in the dependent variable.
Ideally, we would have liked to use a GINI-based secondary cluster detection to classify counties by their maximum cluster-based relative risk score, but this particular conceptualization is not possible in available R packages.

In the **third part** of our reproduction analysis, the results from each the five GEE models were largely consistent with Chakraborty's, suggesting robustness to modeling decisions with regards to GEE clusters.
However, a few independent variables exhibited instability across models, suggesting weak or spurious relationships.
We ultimately modeled three different scenarios:
1. We reproduced the original analysis with the original data while changing only the computational environment to geepack in R.
2. We reproduced the Kulldorff spatial scan in R and reanalyzed the data by applying a local relative risk score to every county within any cluster.
3. We reproduced the Kulldorff spatial scan in R and reanalyzed the data by applying a cluster relative risk score to every county in a cluster.

We found that reproducing the analysis with **geepack** resulted in slightly different GEE results than the original study, even when using data provided by the author from the original study.
This suggests that the computational environments differ in their implementation of GEE, or we have incorrectly specified one or more GEE parameters.
Still, the coefficients trend in the same direction with similar magnitudes, with the exception of the 35-64 age group.
In our model that assigns local relative risk scores for all counties in clusters, the coefficients are weaker while more of the variance in COVID-19 incidence is accounted for in the GEE clustering method.
When we moved to cluster-level relative risk scores, the coefficients again performed more similarly to the original publication.
Although the results of the original publication and the cluster-level relative risk model version are similar, the model conceptualization is very different.
The original model excludes most counties from COVID-19 hotspots, assigning them the lowest level of risk and inadvertently avoiding the problem of controlling for too much variance in COVID-19 through definition of clusters.
Conversely, the reanalyzed cluster-based model includes most counties in COVID-19 hotspots at the same risk level.
The results are similar because in both scenarios the majority of counties in each state are aggregated into the same cluster.

Comparing across each version of the model, we observed that most variables exhibit stability in the direction and magnitude of the coefficients.
However, some variables are less stable -- especially the black and other race categories, Hispanic ethnicity, and some age groups less affected by severe COVID-19 cases (18-34 and 35-64).
Therefore, these variables are more sensitive to the design of GEE clusters, warranting further investigation to evaluate the internal validity of these relationships with regard to the model assumptions of GEE.

We confirmed support for Chakraborty's conclusion that controlling for spatial clustering, although the overall disability percentage is negatively associated with confirmed COVID-19 cases, intra-categorical analysis reveals that socio-demographically disadvantaged PwDs were significantly over-represented in counties with higher COVID-19 incidence.
We found the same direction for each independent variable of intra-categorical disability and COVID-19 incidence.
However, we found weaker significance levels for the Black category and the Hispanic or Latino category.
We found stronger significance levels for the 18-34 and 35-64 age categories.
Differences in our results can be attributable to our different approach to classifying relative risk scores and our different computational environments.
Closer inspection of the clusters for the GEE models revealed a highly skewed distribution of cluster sizes, with most clusters containing very few counties and a few clusters containing 50 or more counties.
The combination of very differing cluster sizes and use of a clustering criteria related to the dependent variable warrant further analysis with alternative approaches to controlling for spatial dependence.

With regards to the **overall conclusions** and **research design**, we agree with the original author's cautious interpretation emphasizing "county-level associations" and the need for "additional data and analysis".
There are at least four sources of uncertainty in this study: ecological fallacy, scale dependency, modifiable areal unit problem, and variable measurement.
There is a risk of ecological fallacy with this research design, whereby county-level statistics for the whole population should not be interpreted as definitive inferential proof of individual-level relationships, especially for populations comprising no more than one third of any county.
There is a real possibility that the study findings are scale-dependent, but it is also impossible to replicate the study using a finer spatial support without also limiting the extent to one or more adjacent states with sub-county data on COVID-19.
The modifiable areal unit problem (MAUP) may also be a source of uncertainty, especially when considering the variable population sizes of counties, which all carry equal weights in the analysis.
Finally, there are well-known problems with the testing and reporting of COVID-19 cases across time and space during the pandemic in the United States, and there is also uncertainty in American Community Survey (ACS) data, particularly when cross-tabulating multiple demographic characteristics.
This study partially mitigates measurement uncertainty by aggregating data across time (more than one year of the pandemic and the five-year ACS estimate) and into relatively large geographic units (counties).

In sum, although some of our results differed from Chakraborty's because of differences in analytical methods, conceptualizations, and computational environments, our reproduction results still suggest that PwDs are likely to experience multiple jeopardy based on the convergence of their disability, racial/ethnic minority, and poverty status.
We reiterate Chakraborty's carefully limited interpretation emphasizing county-level relationships and the need for additional data and research, because the estimated relationship at the county level may not hold at the individual level. Interpretation of the results were based on aggregate statistics at the county level and on statistical methods which produce approximate estimates, not inferences.
Further work is needed to reliably infer relationships between minority PwDs and COVID-19 morbidity and mortality, especially at finer geographic scales.

## References

Chakraborty, J. 2021. Social inequities in the distribution of COVID-19: An intra-categorical analysis of people with disabilities in the U.S. *Disability and Health Journal* **14**:1-5. DOI:[10.1016/j.dhjo.2020.101007](https://doi.org/10.1016/j.dhjo.2020.101007)
