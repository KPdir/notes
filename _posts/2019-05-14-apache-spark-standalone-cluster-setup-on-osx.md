---
layout:     post
title:      Setting Up Apache Spark Standalone Cluster on Mac OSX
date:       2019-05-14
summary:    Instructions for setting up a local Apache Spark Standalone Cluster on Mac OSX 
categories: Software, Data-Science
---

## Introduction
Notes on what Apache Spark is, its internals and workings is at [Apache Spark Core Concepts][spark_concepts]. 

This article details the install of Apache Spark (2.4.3) and setup of a Standalone-Cluster on Mac OSX.

## Setup
1) Install Java:
```bash
 brew cask install java 
 brew cask install homebrew/cask-versions/adoptopenjdk8
```
#### Set Java Environment Variables
```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home
```

2) Install Spark:
```bash
brew install apache-spark
```
#### Set Spark Environment Variables
```bash
export SPARK_HOME=/usr/local/Cellar/apache-spark/2.4.3/libexec
export PATH=$PATH:$SPARK_HOME/bin
```
In ```${SPARK_HOME}/conf/spark-env.sh``` add the following:
```bash
export SPARK_WORKER_MEMORY=2g       # The amount of memory per worker
export SPARK_WORKER_INSTANCES=2     # Number of worker instances
export SPARK_WORKER_CORES=2         # Nunber of processor cores per worker
```
In ```${SPARK_HOME}/conf/slaves``` add ```localhost``` to indicate that the the workers will also be started on the same local machine. 


3) Installing Hadoop (Optional):
See the [Installing Hadoop on Mac OSX][hadoop_on_mac] and set the respective environment variables. 

4) Setup SSH:
Since the master uses SSH to connect with slaves in the Standalone Mode, let us set up ssh keys for passwordless access.

```bash
ssh-keygen -t rsa
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
```

5) Create a Standalone Cluster:
Under ```${SPARK_HOME}/sbin``` run:
```bash
start-master.sh
start-slaves.sh
```
If everyting worked correctly, you can see the Spark server at: ```localhost:8080```. 

6) Connect the standalone cluster to a Jupyter Notebook:
```bash
# Install findspark and Open a Jupyter Notebook 
pip install findspark
jupyter notebook
```

```python
import findspark
findspark.init()

import pyspark
sc = pyspark.SparkContext(master='<master_url>', appName='<app_name>')
```
Here ```<master_url> and <app_name>``` are teh URL for the spark master shown on the spark server page at ```localhost:8080``` and the name for your application respectively. 

$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$

<!-- Links -->
[spark_concepts]: /notes/_posts/2019-05-14-apache-spark-core-concepts.md
[hadoop_on_mac]: https://isaacchanghau.github.io/post/install_hadoop_mac/