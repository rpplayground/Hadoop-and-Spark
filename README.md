# Hadoop and Spark for Data Science

This is my own study notes from of the book [Practical Data Science with Hadoop and Spark](https://www.amazon.com/Practical-Data-Science-Hadoop-Spark-ebook/dp/B01N7G1M8J) written by [Ofer Mendelevitch](https://www.google.com.eg/search?q=Ofer+Mendelevitch&stick=H4sIAAAAAAAAAOPgE-LVT9c3NEwqTys3MM7LVkJwzUss0rRkspOt9JPy87P1y4syS0pS8-LL84uyrRJLSzLyiwBgwlI7PgAAAA&sa=X&ved=0ahUKEwi2rNCr183bAhWDXMAKHQnSDLYQmxMIhwEoATAQ), [Casey Stella](https://www.google.com.eg/search?q=Casey+Stella&stick=H4sIAAAAAAAAAOPgE-LVT9c3NEwqTys3MM7LVoJzSwpKygu1ZLKTrfST8vOz9cuLMktKUvPiy_OLsq0SS0sy8osANaf7MT4AAAA&sa=X&ved=0ahUKEwi2rNCr183bAhWDXMAKHQnSDLYQmxMIiAEoAjAQ) and [Doug Eadline](https://www.google.com.eg/search?q=Doug+Eadline&stick=H4sIAAAAAAAAAOPgE-LVT9c3NEwqTys3MM7LVoJwU-KrzDIKk0u0ZLKTrfST8vOz9cuLMktKUvPiy_OLsq0SS0sy8osAnXzX1T4AAAA&sa=X&ved=0ahUKEwi2rNCr183bAhWDXMAKHQnSDLYQmxMIiQEoAzAQ).

I used [IBM **Cloud** Virtual Servers](https://console.bluemix.net/catalog/infrastructure/virtual-server-group) for setting up the Hadoop Cluster. More setup details can be found in.......

All code used for performing Hadoop operations are provided by the Book Authors and is available from their [GitHub Repo](https://github.com/ofermend/practical-data-science-with-hadoop-and-spark).

---

## What is Hadoop.

Hadoop is an open-source, Java-based, distributed computing platform built to do scalable, parallel processing and analytics on big data.

---

## Components of Hadoop.

**1. Hadoop Distributed File System (HDFS):**

&nbsp;&nbsp;&nbsp;&nbsp;This is a distributed, scalable file system with built-in redundancy. It is further composed of many  
&nbsp;&nbsp;&nbsp;&nbsp;nodes, each containing a regular file system. Data is stored in blocks that are replicated across many  
&nbsp;&nbsp;&nbsp;&nbsp;nodes, this approach achieves high reliability as well as fault tolerance, which is handled at a software level.
   
**2. Resource Manager and Scheduler (YARN):**

&nbsp;&nbsp;&nbsp;&nbsp;This component's job is to direct the allocation of compute resources by partitioning them into  
&nbsp;&nbsp;&nbsp;&nbsp;containers that have a CPU core and an amount of memory, with the ability of adding more resources to  
&nbsp;&nbsp;&nbsp;&nbsp;a specific container according to the processing intensity of the job. It is also responsible for  
&nbsp;&nbsp;&nbsp;&nbsp;scheduling user applications in the most efficient way.
   
**3. Distributed Data Processing Frameworks:**  
   - MapReduce: distributed data processing model whereby a problem can be broken down into three phases, Map, Shuffle and                     Reduce. Not suitable for highly iterative jobs.
   - Apache Tez: a lower-level software API that transfers data between multiple reduce jobs without writing the intermediate                  results to HDFS.
   - Apache Spark: an in-memory data processing engine for iterative style computing. Its basic construct is RDD (resilient                      distributed dataset), which is a set of distributed sequence of objects, often stored in RAM, with an                          implicit mechanism to support failure. It provides relational operators such as joins, union, filter and                      distinct.
   - Apache Flink: similar to Apache Spark, but with a heavier focus on real-time stream processing.

---

## Hadoop Tools for Data Science.

__* Apache Sqoop:__

&nbsp;&nbsp;&nbsp;&nbsp;Allows for bulk data transfer between Hadoop and other datastores (RDBMS or NoSQL). Data is imported  
&nbsp;&nbsp;&nbsp;&nbsp;on to HDFS and tables are populated in Hive and HBase. During the data transfer process, every  
&nbsp;&nbsp;&nbsp;&nbsp;dataset is sliced into partitions and a map only job is launched for handling each partition.

__* Apache Flume:__

&nbsp;&nbsp;&nbsp;&nbsp;Distributed, reliable and available service for effeciently collecting, aggregating and moving  
&nbsp;&nbsp;&nbsp;&nbsp;large amounts of log data from servers into HDFS. Its architecture is based on _agents_ that stream  
&nbsp;&nbsp;&nbsp;&nbsp;data from a source location to a sink location. It is robust and fault tolerant with tunable  
&nbsp;&nbsp;&nbsp;&nbsp;reliability mechanisms and many failover and recovery mechanisms.

__* Apache Oozie and Apache Falcon:__

&nbsp;&nbsp;&nbsp;&nbsp;Data processing and management solutions that cover various levels of data motion, coordination of  
&nbsp;&nbsp;&nbsp;&nbsp;data pipelines, lifecycle management and data discovery. Falcon specifically enables end consumers  
&nbsp;&nbsp;&nbsp;&nbsp;to quickly onboard their data and its associated processing and management tasks on Hadoop.

__* Apache Hive:__

&nbsp;&nbsp;&nbsp;&nbsp;Facilitates the use of SQL to run analytics on Hadoop. Queries are compiled and executed by _Tez_  
&nbsp;&nbsp;&nbsp;&nbsp;engine on the Hadoop cluster. It supports large-batch queries that may take days, as well as  
&nbsp;&nbsp;&nbsp;&nbsp;interactive, real-time queries (it shines for ad-hoc queries). It allows for the addition of some  
&nbsp;&nbsp;&nbsp;&nbsp;programmatic extensions such as _User Defined Functions (UDF)_ and _User Defined Aggregation  
&nbsp;&nbsp;&nbsp;&nbsp;Functions_

__* Apache Pig:__

&nbsp;&nbsp;&nbsp;&nbsp;Domain-specific language designed to help with _Extract, Load, Transform (ETL)_ tasks. It splits  
&nbsp;&nbsp;&nbsp;&nbsp;processing into multiple logical steps that are optimized into the minimal number of _MapReduce_  
&nbsp;&nbsp;&nbsp;&nbsp;or _Tez_ jobs on execution. It is best used for complex queries requiring many intermediate results  
&nbsp;&nbsp;&nbsp;&nbsp;or involving many joins or intermediate tables.

__* Apache Datafu:__

&nbsp;&nbsp;&nbsp;&nbsp;A set of _Apache Pig User Defined Functions_ which aim at making data science tasks easier on Hadoop.  
&nbsp;&nbsp;&nbsp;&nbsp;Contains robust data sampling techniques as well as descriptive statistical primitives.

__* Apache Spark:__
&nbsp;&nbsp;&nbsp;&nbsp;As previously mentioned, it is an in-memory data processing engine that supports Scala and Python.  
&nbsp;&nbsp;&nbsp;&nbsp;It supports RDD as well as DataFrames. _SparkSQL_ proviedes an alternative to _Hive_ for SQL.  
&nbsp;&nbsp;&nbsp;&nbsp;_SparkMLlib_ provides a machine learning library. _Spark GraphX_ provides a library for graphs and  
&nbsp;&nbsp;&nbsp;&nbsp;graph-parallel computations. _Spark Streaming_ is availble for building scalable, fault tolerant  
&nbsp;&nbsp;&nbsp;&nbsp;streaming applications, similar to _Apache Storm_.

---

## Why Use Hadoop.

- Cost-effective and fault-tolerant. Allows for the use of many nodes of much cheaper hardware and pushes the complexity of handling replication and resiliency to the software layer.
- Multi-language tool.
- Schema-on-read where data that is ingested may be interpreted at runtime. Hence, data interpretation is decoupled from its storage.
- Supports ingestion of unstructured or semi-structured data.
- Robust scheduling and resource management.
- Levels of distributed system abstractions.
- Scalable creation and application of machine learning models.
