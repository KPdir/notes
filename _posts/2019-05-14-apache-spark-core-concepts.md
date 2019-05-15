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

### Spark Components

![Spark Components][spark_components]

#### Spark Core
The basic functionlity of Spark - Responsible for:
- Distributed Processing
- Meory Management
- Task Scheduling
- Fault Tolerance
- Interfacing with storage systems

For more info on other components [look here][mapr_spark_article]


### Spark Internals
![Spark Internals][spark_internals_cluster_mode]

- Spark application runs as independent processes on a cluster, coordinated by SparkContext object in the main program called **Driver**.

- Spark conects to Cluster Managers - Cluster Managers allocate resources to applications. Once connected, Spark acquires executors on teh nodes of a Cluster which run computations and store data for your application. 

- Your application code (JAR or Python Files to SparkContext) is sent to executors as tasks to run on individual nodes. 

- Each application --> has its own executor procesesses --> each executor can run in multiple threads.

- Each executor runs it won tasks in different JVMs - which provides isolation between applications but also means - data cannot be shared between applications directly without writing to disk. 

- Spark is **Cluster Manager Agnostic**. 

- **Driver** must listen for incoming connections from executors throught its lifetime - must be addressable from **worker nodes**.

- Preferably the driver and wokkers are on the same LAN. If want to run remotely, open an RPC to driver and have it submit operations from nearby. 

#### Spark vs Pandas, Hadoop and Dask

Pandas:
- Tabular data
- Single Machine

Hadoop:
- HDFS storage system
- MapReduce compute model
- Spark is in memory vs Hadoop-Mapreduce is from Disk.

Dask:
- Python parallel computers
- 1- 1000 node cluster
- Part of Python Ecosystem


#### PySpark
A wrapper aroudn Spark Core. Uses PY4J to launch a JVM and creates a Java SparkContext. 

#### Partitions
How data is physically distributed between different machines during execution. 

#### Transformations
Instructions to modify teh dataframe. They are immutable. Spark does not act on Transformations until we perform an Action. Spark builds a plan for Transformations but does not execute - Lazy evaluation. 

#### Actions
Tell Spark to compute results of transformations.
- View data like .show()
- Collect Data like .collect()
- Write data like write.format()

#### Note:
User Defined Functions (UDFs) are not as fast when written in Python. Buil-in functions are highly optimized. UDFs written in Java or Scala are faster than Python.


### RDDs
- Support for in-memory data storage
- Fault Tolerance by tracking transformations applied.
- Transformations: Create a new RDD by changing original through mapping filtering etc. 
- Actions: Like counts measure but do not change original data. 
- Are immutable
- Chain of transformations - RDD1 ... RDDn are logged so it can be repeated in case of data loss or failure of cluster node. 
- Can improve performance of iterative processes due to caching. 

<!-- Links List -->
[spark_components]: /notes/images/spark-components.png "Spark Componenets Image Link"
[spark_internals_cluster_mode]: /notes/images/spark-internals-cluster-mode.png "Spark Componenets Image Link"
[mapr_spark_article]: https://mapr.com/ebooks/spark/03-apache-spark-architecture-overview.html


