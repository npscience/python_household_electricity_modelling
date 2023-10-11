Rewrite in Python:

1. Prepare household energy data

Based on R script (prepare_household_energy_data.R) to read in raw csv and output cleaned data "daily_energy_all_hholds.csv"

Steps:

* read in raw csv
* clean column names (all to lowercase, snake case)
* add columns for month, season, weekday type, quarter, season (so can filter for Summer and Winter 2013)
* trim data for dates: 2011-12-01 to 2014-02-27
* write to new csv

2. Prepare data for clustering

Create summary df:
* Take data from above and filter for only Summer 2013 and Winter 2013
* Create the five summary variables per household, join into one df (1 row per 5,078 hholds * 6 vars inc hhold id)
* log transform variables (with log(x +1)) as needed - did this for winter_mean_klwh, winter_fold_change, winter_fold_chg_sd in R notebook)

Check for correlations:
* e.g. corrplot (plot each var against the others, find correlation coefficient)

Dedupe vars:
* select only the log/non-log version of each of 5 vars

Prep for k-means clustering:

_look up what's needed for python package_

* name the rows by household id (ie lose this as a var)
* scale all data (mean = 0, sd = 1, normally distributed)

3. Clustering model

K-means

* try out diff settings (hyperparameter optimisation), inc diff number of k (e.g. 1:10)
* ensure to record outcome metrics in a table to compare, as well as output models
* evaluate - elbow, silhouette methods (and third method?)
* visualise clusters - try PCA?

