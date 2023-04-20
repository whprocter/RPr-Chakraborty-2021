REL_RISK is the cluster relative risk

the SaTScan "no geographical overlap" option actually gives two versions of results: hierarchical and gini coefficient.
The hierarchical version sequentially adds clusters without overlap and having the highest log likelihood scores first until clusters with p < 1.0 are exhausted.
The GINI version creates a variety of the hierarchical versions, each with a different upper limit on the percent of total population allowed within each cluster. The version with the greatest GINI coefficinet is selected.
