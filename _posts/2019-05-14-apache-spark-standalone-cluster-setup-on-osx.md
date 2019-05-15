---
layout:     post
title:      Setting Up Apache Spark Standalone Cluster on Mac OsX
date:       2019-05-14
summary:    Instructions for setting up Apache Spark Standalone Cluster on Mac OsX 
categories: Software, Data-Science
---

## Introduction
Notes on what Apache Spark is, its internals and workings is at [Apache Spark Core Concepts][spark_concepts]. 

This article details the install of Apache Spark (2.4.3) and setup of a Standalone-Cluster on Mac OsX.

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
In ```${SPARK_HOME}/conf``` add the following:
```bash
export SPARK_WORKER_MEMORY=2g       # The amount of memory per worker
export SPARK_WORKER_INSTANCES=2     # Number of worker instances
```


<!-- Links -->
[spark_concepts]: /notes/_posts/2019-05-14-apache-spark-core-concepts.md