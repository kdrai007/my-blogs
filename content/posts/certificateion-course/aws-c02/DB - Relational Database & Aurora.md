---
title: "DB - Relational Database & Aurora"
draft: false
---

## RDS - Relational Database Service

[checkout](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)

-- Amazon Relational Database Service (Amazon RDS) is a web service that makes it easier to set up, operate, and scale a relational database in the AWS Cloud.

- it's managed DB service for DB use sql as a query language
- It allows to create database on cloud managed by amazon 
	ex - 
	-  postgres, Mysql , mariaDB, Oracle , Microsoft Sql Server
	- Aurora (AWS proprietary database)		

#### Advantage of deploying RDS on AWS 

- RDS is a managed service : 
	 - Automated provisioning , OS patching  
	 - Continous backup and restore to specific timestamp (Point in time restore). 
	 - Monitoring dashboards
	 - Read replica for improved read performance
	 - Multi AZ setup for DR (Damage Recovery)
	 - Maintenance  windows for upgrades
	 - Scaling capablity (both horizontal and vertical)
	 - Storage backed by EBS
-  You can't ssh into your instances


#### Amazon RDS Proxy

- Fully managed database proxy for RDS
- Allows apps to pool and share DB connections established with the database
- Improving database efficiency by reducing stress from database resources ( e.g, RAM,CPU) and minimize open connnections (and timeouts)
-  Serverless , autoscaleing , highly available (multi AZ)
- Reduced failover time by up-to 66% of RDS &  Aurora
- Supports RDS (Mysql,Postgres,MariaDB,MS-SQL server) and Aurora(mySql, Postgres) DB
- No code changes required for most apps
- Enforce IAM Authentication for DB , and securely store credentials in AWS Secrets Manager
- RDS proxy is never publicly avaialble (must be accessed through VPC)

### RDS Read Replica  vs Multi-AZ

-- Amazon RDS Multi-AZ and Read Replicas maintain a copy of database but they are different in nature. Use Multi-AZ deployments for High Availability / Fail-over and Read Replicas for read scalability.

#### Read Replica for Read Scalibility 

- Up to 15 Read Replica
- Within AZ, Cross AZ or Cross Origin
- Replication is **ASYNC***, so reads are eventually consistent
- Replicas can be promoted to their own DB
- Application must update the connection string to leverage read replicas

  ![[Pasted image 20240806222224.png]]
  
### RDS - Storage Auto Scaling

- Helps you increase storage on your RDS instance dynamically
- When RDS scans you are running out of database storage , it scales automatically
- Avoid manually scaling your database storage
- You have to set **Maximum Storage Threshold** (maximum limit for DB storage)
- Automatically modify storage if : 
    1. Free storage is less than 10% of allocated storage
	2. Low-storage lasts at least 5 minutes
	3. 6 hours have passed since last modifications. 
- Useful for application with unpredictable workloads
-  Supports all RDS Database engines

  ![[Pasted image 20240806214718.png]][


### Amazon RDS & Aurora Security

- **At-rest encryption**
	- Database master & replicas encryption using AWS KMS - must be defined during launch time
	- If the master db is not encrypted , the replicas can't be encrypted
	- To encrypt a un-encrypted database  , go through the Db snapshot and re-create as encrypted
-  **In-Flight encryption** : TLS- ready by default , use AWS TLS root certificates client-side
- **IAM authentication** : IAM roles to connect to your database (instead of username/pw)
- **Security Groups** : Controls Network Access to RDS & Aurora
- No SSH based connection except on RDS custom
- **Audit logs** can be enabled and sent to CloudWatch for longer retention
## Amazon Aurora

[checkout](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html)

- Aurora is a proprietary technology from AWS (not open sources)
- Postgres and Mysql both supported as Aurora DB ( that means your drives works as if Aurora was a postgres or mysql)
- Aurora is "Aws cloud optimized " and claims 5x performance improvement over mysql and with with postgres over 3x on RDS
- Aurora storage autmatically increments 10 GB, up to 128 TB
- Aurora can have up to 15 replicas and the replication process is faster than mySQ (sub 10 ms replica lag )
- Aurora costs more than RDS (20% more) - but is more efficient

### Aurora High Availability and Read Scaling

- 6 copies of your data in 3 AZ
	- 4 copies out of 6 needed for writes 
	- 3 copies out of 6 needs for reads
	- Self-healing and peer to peer replication 
	- Storage is striped  across of 100s of volumes
-  One instance takes writes (master)
- Automated failover for master takes 30 seconds 
- Master + up to 15 Aurora read replica  serve reads
- Supports for cross region replication 

- Backtrack : Restore data at any point of my without using backups
-	**Aurora DB Cluster**	
	![[Pasted image 20240809132924.png]]



----
[[aws]]
[[EC2]]




