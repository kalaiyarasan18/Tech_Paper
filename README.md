# Performance and Scaling Analysis of NOSQL Databases

![image](https://blog.couchbase.com/wp-content/uploads/2017/04/nosql-vs-sql-overview-1.png)

## ABSTRACT:

Recently, NoSQL databases have emerged as alternative platforms to store, load and analyze Big Data. Most NoSQL systems,such as MongoDB, Redis, HBase, and Cassandra sacrifice consistency for scalability which means that users may not be able to retrieve the latest changes in the data but can execute faster queries. Alternatively, these systems provide what is known as eventual data consistency. Similarly, relational database systems allow relaxed levels of consistency to obtain performance improvements. Additionally, a relational database system not used in previous research was tested in this project, in addition to a new release of an already-tested open source relational system. The purpose of these article is to extend the previous evaluation to two relational systems and two non-relational database systems regardless of their data model by measuring the time needed to load and query persistent logs under different indexing and consistency settings. 


## Introduction

- Efficient storage and retrieval of data has always been an issue due to the growing needs in industry, business and academia. Larger amounts of transactions and experimentation
result in massive amounts of data which require organized storage solutions. Databases were created in order to satisfy this need of storing and retrieving data in an organized manner.
Since their inception in the 1960’s different types have emerged,each using its own representation of data and technology for handling transactions. They began with navigational databases
which were based on linked-lists, moved on to relational databases, afterwards object-oriented and in the late 2000s. 

## Types of NoSQL Databases

NoSQL databases started gaining popularity in the 2000’s when companies began investing and researching more into distributed databases. The most common NoSQL database

**Key-value stores**
  
- Data is stored as values with a key assigned to each value similarly to hash-tables. Also depending on the database a key can have a collection of values.

**Graph databases**
  
- Important aspect which differentiates graph from relational databases is the use of index-free adjacency, this means each element contains a pointer to its adjacent element and does not require indexing of every element. An important difference between relational
databases and NoSQL databases is they do not fully guarantee ACID properties.

**Database replication**

- Database Replication is the practice of deploying multiple servers which are clones of each other. This practice is used in NoSQL databases often in order to provide higher reliability and performance. In Mongo DB  replication is deployed using a primary-secondary server configuration whereby one server is the primary and all others are secondary.

## **COMPARISON**

PARAMETER|SQL|NOSQL
----|------|-------|
Definition | SQL databases are primarily called RDBMS or Relational Databases | NoSQL databases are primarily called as Non-relational or distributed database
Design for | Traditional RDBMS uses SQL syntax and queries to analyze and get the data for further insights. They are used for OLAP systems. | NoSQL database system consists of various kind of database technologies. These databases were developed in response to the demands presented for the development of the modern application.
Schema | SQL databases have a predefined schema | NoSQL databases use dynamic schema for unstructured data.
Ability to scale | SQL databases are vertically scalable | NoSQL databases are horizontally scalable
Consistency | It should be configured for strong consistency. | It depends on DBMS as some offers strong consistency like MongoDB, whereas others offer only offers eventual consistency, like Cassandra.
Best features | Cross-platform support, Secure and free | Easy to use, High performance, and Flexible tool

## Advantages and Disadvantages of Different NOSQL Databases

![image](https://dytvr9ot2sszz.cloudfront.net/wp-content/uploads/2019/06/image-2.png)

# Cassandra

Cassandra is the most popular wide column store database system on the market. Initially developed at Facebook for Facebook’s Inbox search feature, Cassandra was open-sourced in 2008 and subsequently made a top-level project for Apache on February 17, 2010. It is widely favored for its enterprise features, like scalability and high availability, that allow it to handle large amounts of data and provide near real-time analysis. Written in Java, Cassandra offers synchronous and asynchronous replication for each update. Its durability and fault-tolerant capabilities make it ideal for always-on applications.

## Cassandra Advantages

- Cassandra uses a masterless “ring” architecture which provides several benefits over legacy architectures like master-slave architecture. This, in turn, means that all nodes in a cluster are treated equally, and a majority of nodes can be used to achieve quorum.

- It provides agility in the sense that it allows rows to have different columns, and even allows a change in the format of the columns. Apart from this, its query language, Cassandra Query Language (CQL), closely resembles the traditional SQL syntax, and thus, can be easier for SQL users to understand.

- Cassandra offers advanced repair processes for read, write, and entropy (data consistency), which makes its cluster highly available and reliable. It can provide a highly available architecture if a quorum of nodes is maintained and the replication factor is tuned accordingly. This also allows for better fault tolerance compared to document stores, which might take up to 40 seconds to recover.

## Cassandra Disadvantages

- The architecture is distributed, replicas can become inconsistent. If a node in a cluster goes down, its coordinator node tries to preserve the data in the form of hints. When the failed node is brought online, the coordinator node hands off the hints to aid in the repair. 

- Cassandra handles itself well if the primary key is known, but suffers severely if it is not. This is because it has to scan all its nodes in the cluster, resulting in high read time penalties.

- lack of solid official documentation from the Apache Software Foundation. you must rely on third-party companies like DataStax for this.

# MongoDB

MongoDB is the most popular document store on the market and is also one of the leading Database Management Systems. It was created in 2007 by the team behind DoubleClick (currently owned by Google) to address the scalability and agility issues in serving Internet ads by DoubleClick. MongoDB offers both a community and an enterprise version of the software. The enterprise version offers additional enterprise features like LDAP, Kerberos, auditing, and on-disk encryption.


## Advantages of MongoDB
- MongoDB is a schema-less database and stores data as JSON-like documents (binary JSON). This provides flexibility and agility in the type of records that can be stored, and even the fields can vary from one document to the other. Also, the embedded documents provide support for faster queries through indexes and vastly reduce the I/O overload generally associated with database systems. 

- MongoDB  provides high availability and horizontal scalability. High availability is achieved through replica sets which boast features like data redundancy and automatic failover. This ensures that your application keeps serving, even if a node in the cluster goes down.

- MongoDB  provides support for several storage engines, ensuring that you can fine-tune your database based on the workload it is serving. Some of the most common use cases of MongoDB include a real-time view of your data, mobile applications, IoT applications, and content management systems. 

## Disadvantages of MongoDB
- Unless you opt for one of the DBaaS flavors, management operations like patching are manual and time-consuming processes. Although it has improved in the newer versions, MapReduce implementations still remain a slow process, and MongoDB also suffers from memory hog issues as the databases start scaling.


# HBase

HBase is an open-source wide column store distributed database that is based on Google’s Bigtable. It was developed in 2008 as part of Apache’s Hadoop project. Built on top of HDFS, it borrows several features from Bigtable, like in-memory operation, compression, and Bloom filters. Built on Java, HBase provides support for external APIs like Thrift, Avro, Scala, Jython, and REST. Hbase offers a stand-alone version of its database, but that is mainly used for development configuration, not in production scenarios.

## Advantages of HBase
- One of the strengths of HBase is its use of HDFS as the distributed file system. This allows the database to store large data sets, even billions of rows, and provide analysis in a short period. This support for sparse data, along with the fact that it can be hosted/distributed across commodity server hardware, ensures that the solution is very cost-effective when the data is scaled to gigabytes or petabytes. That distribution contributes to one of its big pros: failover support includes automatic recovery.

- Several concepts from Bigtable, like Bloom filters and block caches, can also be used for query optimization. HBase also has a leg up in any HBase vs. Cassandra comparison when it comes to consistency, as the reads and writes adhere to immediate consistency, compared to the eventual consistency in Cassandra. Its close integration with Hadoop projects and MapReduce makes it an enticing solution for Hadoop distributions.

- HBase’s  use cases include online log analytics, Hadoop distributions, write-heavy applications, and applications in need of large volume (like Tweets, Facebook posts, etc.).

## Disadvantages of HBase
- HBase proves to be a single point of failure, as failing from one HMaster to another can take time, which can also be a performance bottleneck. If you are looking for an always-available system, then Cassandra might be a better choice.

- To achieve SQL-like capabilities, one must use the JRuby-based HBase shell and technologies like Apache Hive. The major problem with this approach is the high latency and steep learning curve in employing these technologies.

- HBase scales well by adding DataNodes to its cluster, it has some high hardware requirements, mainly because of its dependency on HDFS, which would require five DataNodes and one NameNode as a minimum. This, in turn, translates to high running and maintenance costs.


>_This Article show that there is no specific type of system consistently outperforming the others but the best option can vary depending on the features of the data, the type of query and the specific system._

## References:

* [Nosql vs Sql](https://www.dataversity.net/nosql-vs-sql-its-about-the-performance-and-scale/)
* [NoSql DB Comparison](https://logz.io/blog/nosql-database-comparison/)
* [Performance and Scaling Comparison](https://logz.io/blog/nosql-database-comparison/)

