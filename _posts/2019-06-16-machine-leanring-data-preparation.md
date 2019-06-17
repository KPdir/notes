---
layout:     post
title:      Machine Learning Data Preparation
date:       2019-06-17
summary:    Data preparation checklist
categories: Software, Data-Science
---

### TOC: 
- Handling Missing Values
- Handling Categorical and Ordinal Featues
- Data Cleaning
- Checking For Data Leakage (for Competetions)


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

### Handling Categorical and Ordinal Featues
- Categorical features (No hierarchy in categories, ex: day of week, gender etc.)
- Ordinal features (Hierarcy exists but cannot be quantified. ex: Cabin class, driver's licence type etc.)
- Encoding Categorical Features:
    - Label Encoding: Map each category to a number. 
        - Works for Tree based methods. 
        - Problematic in general since: as you are imposing oridnality. 
    - One-Hot Encoding: 
        - Works for all kinds of methods but increases dimensionality & sparsity. 
        - Can be used by reducing categroies or sparsity reducing methods if needed. 
        - Useful/Necessary for non-tree methods
    - Frequency Encoding:
        - Encode each category with its frequency in the data. 
        - This helps if the frequency of categories is correlated with the target. 
        - It can help both tree and non-tree based models. (It can help trees have lesser splits?) 
        - Can randkdata to break ties between categories that have the same frequencies. 
- Encoding interatcions between categories can help non-tree models to pick up such interactions easily.

### Data Cleaning
- Check for constant features (no-variability) across entire dataset. This can slow down the training without providing any new info.
- Check for duplicated featues 
    - Can use label-encoding based on appearance (pandas factorize) to check if two categorical features are the same.
- Check for duplicated rows. 
    - This can affect training and test scores and hence the model
- Check if dataset was shufflued. 
    - Can plot rolling_mean of target vs the row index to see if there is a systematic departure of the rolling_mean from the mean. 





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