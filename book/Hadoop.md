# Hadoop: The Definitive Guide

> Humble Bundle上买的

## Keywords

- 2015, Hadoop 2 (Released date of the book). 2020, Hadoop 3 released.
- MapReduce, HDFS, YARN
- High-level data processing tools like Hive, Spark

## HDFS, Hadoop Distributed Filesystem

- a reliable, scalable platform for storage and analysis.

- beyond batch processing system
    - YARN, Yet Another Resource Negotiator
    - Interactive SQL, *IMPALA*
    - Interactive processing, Spark
    - Stream processing
    - Search

### Compared

e.g. RDBMS, relational database management systems

列了很多例子：
- MapReduce适合通过批处理方式处理整个数据集，尤其是特殊分析（ad hoc analysis）;关系型数据库适合点查询和更新（低延迟的查询和小数据更新）
- 前者可以处理非结构式数据。
- 服务器的日志无法正规化（normalization），适合Hadoop

> RDBMSHive体现了Hadoop尝试吸收关系型数据库的特性。

### Grid Computing

High-performance computing communities can be benefited from Hadoop. 

> tradition: MPI, Message Passing Interface