---
title: "EC2"
id: EC2
aliases: []
tags: []
---

## Amazon EC2

- Amazon elastic compute cloud(Amazon EC2) offers the deepest and boradest compute platform,with over 720 instances and choice over latest processor,storage,os and networking system 

**Use Cases**

- Run cloud-native and enterprises applications.
- Train and deploy ML applications.

**EC2 sizing and configuration options**

![[Pasted image 20240725105109.png]] 


**EC2 User Data**

- It is possible to bootstrap our instances using user data script.
- *Bootstrapping* means running some commands when instance start.
- That script only runs once at the instance first start.
- EC2 user data is used to automate boots task such as:
		- Installing Updates
		- Installing software
		- Download common files from internet.
		- Anything you can think off.
- The EC2 user data runs with root user. 

**EC2 Instance type: Example**

![[Pasted image 20240725111444.png]]



**EC2 Instance type - Overview**

![[Pasted image 20240725130103.png]]

**EC2 Instance type - General purpose**

-  Great for a diversity of workloads such as web-server or code repositories.
-  Balance between :
	 . Compute
	 . Memory
	 . Networking
-  for ex, t2.micro is general purpose ec2 instance.

 **EC2 Instance type - Compute Optimized**

- Great for compute-intensive tasks that require high performance processors:
		. Batch processing workloads
		. Media transcoding
		. High performance web server
		. High performance computing(HPC)
		. Scientific model & machine learning
		. Dedicated gaming server	
		
		![[Pasted image 20240725130830.png]]

**EC2 Instance type - Memory optmized**

- Fast performance fore workloads that process large data sets of memory.
- Use Cases:
	. High performance relational/non-relational databases.
	. Distributed web scale cache stores
	. In-memory databases optimized  for BI(Business Intelligence) 
	. Applications performing real-time processing on big unstructured data.
	
	
**EC2 Instance type - Storage optimized**

-  Great for storage intensive-tasks that require high, sequential read and write access to large data sets on local storage.  
- Use Cases:
	.  High processing online transactions processing(otlp) systems.
	.  Relational & NoSql databases.
	.  Distributed file system.



----
## Links

[[aws]]
[[productive]]
