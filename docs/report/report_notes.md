# Issues for Discussion

Ecological fallacy: the analysis is at the county level, but is interested in socio-demographics, disability and COVID-19 at the individual level.

Other conceptualizations by Chakraborty use urban - urban-adjacent - rural classifications or the covid vulnerability index to create clusters

GEE models are run at the county level, but counties also vary tremendously by population.

Should clusters be weighted, and are there consequences for not doing so?

SpatialEpi's Kulldorff doesn't include any overlap in the clusters --
does satscan exclude clusters of just one county? NO, it does not.
WHY does spatialepi discover more clusters than satscan?

Should we have used county-level local relative risk or cluster-level cluster relative risk? This probably indicates that we should use county-level local relative risk: "estimate relative risk (RR) for COVID-19 incidence rates at the county level"

There are definitely differences in Kulldorf spatial scan statistic between SatScan and SpatialEpi. What are they?

# Unplanned Deviations

- add cluster relative risk score

# Results

- add relative risk Results

# Discussion

- discuss differences between local and cluster relative risk results
