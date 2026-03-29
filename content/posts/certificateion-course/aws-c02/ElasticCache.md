---
title: "ElasticCache"
draft: false
---


## Amazon ElasticCache

[checkout](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/elasticache-use-cases.html)

**AWS ElastiCache** is a managed in-memory caching service that supports both Redis and Memcached. It’s used to improve the performance of web applications by retrieving data from a fast, managed in-memory cache, instead of relying entirely on slower disk-based databases.

- The same way RDS get maganed Relational Databaseses... 
- ElastiCache  is to get managed Redis or Memcached
- Caches are in-memory databases with really high performance , low latency
- Helps reduce loads of databases for read intensive workloads 
- Helps make your application stateless
- AWS takes care of OS maintenance / patching , optimizations , configuration , monitoring , failure recovery and backups
- Using Elasticache can be pain in the a** because you have to do heavy code changes to make your application work

### Solution Architecture  - DB Cache

![[Pasted image 20240810204043.png]]

- Applications queries ElasticCache  , if not available , get from RDS and store in ElastiCache
- Helps relive load on RDS
- Cache must have an invalidation strategy  to make sure only the most current data is used  in there

![[Pasted image 20240810204439.png]]

1. User logs into any of  the aplication 
2. The application writes session data into ElastiCache
3. The user hits another instance of our application 
4. The instance retrives the data and the user is already logged in 

### Redis vs Memcached


| Redis                                                        | Memcached                                        |
| ------------------------------------------------------------ | ------------------------------------------------ |
| - **Multi AZ** with auto failover                            | - Multi-node for partitioning of data (sharding) |
| - **Read Replicas** to scale reads and has high availability | - **No high aviailability** (replication)        |
| - Data Durability using AOF persistence                      | - Non  Persistent                                |
| - **Backup and restore feature**                             | - No backup and restore                          |
| - Supports Sets and sorted Sets                              | - Multi threaded architecture                    |
| ![[Pasted image 20240810210121.png]]                         | ![[Pasted image 20240810210148.png]]             |



----
[[aws]]
[[DB - Relational Database & Aurora]]