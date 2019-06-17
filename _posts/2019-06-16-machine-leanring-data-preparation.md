---
layout:     post
title:      Machine Learning Data Preparation
date:       2019-06-17
summary:    Data preparation checklist
categories: Software, Data-Science
---

### TOC: 
- Handling Missing Values: 
- Checking For Data Leakage (for Competetions)
- Data Cleaning

### Handling Missing values - Remarks

- In general: avoid filling (replacing) NAs before feature generation - it can reduce the usefulness of features.
- Create Indicator variables to mark missing values. 
- Understand data generating process before imputation (reconstruction of missing value). 
- Can treat outliers as missing values sometimes.
- Can use frequency encoding for including information about feature values 
that are present in test data but not in train data. 
    - For Categorical features: we want the model to treat the new categories not present in training data randomly when encountered in prediction.  
- Check for missing values that have been replaced by outliers in the data-acquisition or curation process.
    - Be careful of these when doing feature engineering or generation - they can screw up our generated features. Best to leave such outliers and missing values during early feature generation. 













<!-- Links List Example

#### INSIDE BODY #####

## IMAGE
![Spark Components][spark_components]

## PAGE LINK
For more info on other components [look here][mapr_spark_article]

#### LINK FOOTER #####
[spark_components]: /notes/images/spark-components.png "Spark Componenets Image Link"
[mapr_spark_article]: https://mapr.com/ebooks/spark/03-apache-spark-architecture-overview.html
-->