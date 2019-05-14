---
layout:     post
title:      Apache Spark Core Concepts
date:       2019-05-14
summary:    Notes on concepts, applications of Apache Spark
categories: Software, Data-Science
---

## Introduction
- Spark is a fault tolerant distributed computing framework that can run large data processing jobs on compute clusters.

- Spark is versatile: you can do data processing, data warehousing, machine learning, stream processing (real-time analytics) and graph processing of large-out of memory datasets. 

- Spark provides APIs for low level (ex: RDDs and Dataset API) and high level (ex: Data Frames API) for data manipulation. 

- Spark supports Python, R, Scala and Java. Spark is written in Scala and runs on JVM. It integrates with Hive, Cassandra, HDFS, HBase

- Can run locally, on-premise or in the Cloud. Can run in Standalone mode (using its own cluster manager), or can use Hadoop YARN, Amazon Mesos or IBM Bluemix or in a Kubernetes Cluster.

## Spark Components

![Spark Components][spark_components]

[spark_components]: /notes/images/spark-components.png "Spark Componenets Image Link"



