# NYPD-Arrest-Records

Determine if specific demographic signatures, primarily age and race, vary significantly across New York City’s five boroughs. 

Pulled public data from NY City Government website, for 2025.

212,000 Total records pre EDA

Performed EDA and maintained 92,000 records post EDA.
___

# Includes:

## EDA
  - Encoded Age Groups
  - standardized borough names
  - checked missing values per borough
  - checked for dataset age group skewness and kurtosis
- Univariate Analysis of categorical variables
  -  Distribution of Arrests by Law Category code
  -  Arrests by perpetrator race
  -  Arrests by borough
  -  distribution of arrests by the type of law broken
- Numerical Univariate Analysis
  - Distribution of Arrests across age groups
  - Distribution of arrest precinct plus statistics
  - Distribution of perpetrator race across the boroughs
- Bivariate analysis
  - borough vs age groups to see the age distribution of arrestees across the boroughs
___

## Visualizations
  - Bar Chart for percent of missing age data by borough
  - Age distribution density
  - Cleaned age distribution
  - Violin plot of age distribution on my cleaned data
  - Histogram with KDE for distribution of arrests across age groups
  - Distribution of arrests precincts
  - distribution of perpetrator race across boroughs
  - Heatmaps for univariate analysis
  - stacked bar chart for age group composition of arrests by borough
  - Heatmap of top 10 offenses by borough
  - Daily arrest frequency with linear regression trend
  - geospatial distribution of arrests + colored by borough + colored by perpetrator sex
  - density of acre groups by borough
  - age density curves per borough by race
  - racial composition of arrests by borough heatmap
  - box plot for age distribution across boroughs segmented by race
  - arrest volume by borough and age heatmap
  - Hexbin plot for NYC arrest density for any record with coordinates
  - Pair Plot Matrix for all cleaned numeric variables

___

### Dataset Statistics After Cleaning Data
Rows Removed: 91878
Rows Retained: 120608
Age Group Skewness: -0.25
Age Group Kurtosis: 0.79

___

## Modeling

Hypothesis Testing: comparing age across boroughs

**Age Gap utilizing Welch's T-Test to compare the mean ages of arrests in Manhattan vs the Bronx**

### Results

- Manhattan Sample Size: 26801
- Bronx Sample Size: 22561

### T-Test Results

- T-Statistic: 20.2020
- p-value:     2.2530e-90
- Mean Difference: 0.1380

### Levene's Test for homogeneity of variance**

#### Levene's Test Results (F-test Equivalent) ---

- Test Statistic: 1.8958
- p-value:        1.6856e-01
- Contextual Spread
  - Manhattan Std Dev: 0.7491
  - Bronx Std Dev:     0.7619


## Multiple Linear Regression

### Regression Performance Metrics

- R-squared ($R^2$): 0.3890
- Mean Absolute Error (MAE): 21.92 precincts

___

## Classification using Random Forest Classifier

###  Classification Performance Metrics

- Overall Accuracy: 1.0000

#### Detailed Classification Report
               precision    recall  f1-score   support

        Bronx       1.00      1.00      1.00      4442
     Brooklyn       1.00      1.00      1.00      6664
    Manhattan       1.00      1.00      1.00      5381
       Queens       1.00      1.00      1.00      6200
Staten Island       1.00      1.00      1.00      1384

     accuracy                           1.00     24071
    macro avg       1.00      1.00      1.00     24071
 weighted avg       1.00      1.00      1.00     24071

___

## K-Means Clustering

### Cluster Centroids (Averages per Group)

-         AGE_NUMERIC  ARREST_PRECINCT   Latitude  Longitude  RACE_CODE
- Cluster                                                               
- 0           2.059308        30.257135  40.803554 -73.934967   3.374493
- 1           2.116928        88.227687  40.619826 -74.037403   3.916225
- 2           2.039085       101.227087  40.715789 -73.870950   5.775632
- 3           2.040952        91.195735  40.686979 -73.876508   1.933200

### Distribution of Arrests per Cluster

- 0    49336
- 3    36018
- 2    17654
- 1    17344
- Name: Cluster, dtype: int64

___

## Logistic Regression

### ML Logistic Regression Performance

- Mean CV Accuracy: 0.4942
- AUC-ROC Score:    0.5310
