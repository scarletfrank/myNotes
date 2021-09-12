# README

> hadoop_thedefinitiveguide

## 目录

- Hadoop Fundamentals
- MapReduce
- Hadoop Operations
- Related Projects
- Case Studies

## 2天快速阅读

### Hadoop Fundamentals

#### MapReduce

**Streaming** : 任何支持，从标准输入读取和写到标准输出的，编程语言，能够利用Hadoop。

指定 `streaming.jar`，然后将`mapper/reducer`指向`Ruby/Python`脚本

#### HDFS

> hadoop distributed filesystem

**概念**

- blocks
- namenodes and datanodes
- block caching
- HDFS federation
- HDFS High Availbility
- Failover and fencing

*single point of failure* (SPOF)


##### 分布式拷贝 distcp

```bash
hadoop distcp -update -delete -p hdfs://namenode1/foo hdfs://namenode2/foo
```

#### YARN

> Yet Another Resource Negotiator
> Hadoop's resource management system
> two types of long-running daemon: a resource manager (one per cluster) and node managers(all nodes)

##### Scheduler

- FIFO
- Capacity
- Fair Scheduler

### Related Projects

项目一览（缩略版）
- Sqoop
- Pig
- Hive
- Spark
- HBase
- ZooKeeper


#### Sqoop

> an open source tool that allows users to extract data from a structured data store into Hadoop for further processing

##### from RDBMS to Hive

```bash
sqoop import --connect jdbc:mysql://localhost/hadoopguide --table widgets -m 1 --hive-import
# 当然，还有对应的export
```

#### Hive

> Information Platforms: "the locus of their organizations effors to ingest, process and generate information"

**Hive Services**
- cli
- hiveserver2
- beeline
- hwi
- jar
- metastore

**SQL-on-Hadoop Alternatives**
- Impala
- Tez
- Presto
- Trino
- Drill
- Spark SQL
- Phoenix

**Partitions and Buckets**：分区表和分桶表

**UDF**

####

#### HBase

#### ZooKeeper

#### Spark

#### Pig

