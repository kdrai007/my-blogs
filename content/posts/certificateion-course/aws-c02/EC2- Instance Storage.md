---
title: "EC2- Instance Storage"
draft: false
---


## EBS - Elastic Block Store

- An Ebs Volume is network drive you can attach to your instances while they run.
- It allows your instances to persist data ever after the termination of your instance.
- They can be mounted to only to instance (at CCP level).
- They are bound to the specific  availability zones.
- Analogy:Think  of them as a "network  USB  stick"

**EBS Volume**

![[Pasted image 20240726114353.png]]

**EBS - Delete on Termination attribute**

![[Pasted image 20240726114714.png]]

- Controls the ebs behaviour when an EC2 instance terminates. 
	. By Default , the root EBS volume  is deleted (attribute enabled).
	.  By default any other attached  ebs volume  is not deleted (attribute disabled)
- This operations can be controlled by CLI. 

=> Use Case :  preserve root volume when instance is terminated. 


## EBS Snapshots

- Make a backup (snapshot) of your EBS volume at any point of time.
- Not necessary to detach your volume to create snapshot but its recommended.
- Can copy EBS to different AZ or region  ![[Pasted image 20240726152412.png]]

**EBS Snapshot Features**

![[Pasted image 20240726152720.png]]

**EBS Volume Types**

- EBS volume types comes with 6 types
	1. gp2/gp3 (ssd) - General purpose (SSD)
	2. io1/io2 Block Express (SSD) - Highest performance SSD
	3. st 1 (HDD) - Low cost HDD volume designed for frequently accessed.
	4. sc 1 (HDD) - Lowest cost HDD  designed for less frequently accessed workloads. 
	
	
-  EBS Volume are characterized  in Size | Throughput | IOPS (I/O Ops per sec) 
- Only gp2/gp3 and io1/io2 Block express can be used as  boot volumes.

**EBS Volume Types use cases**

- General Purpose SSD

    ![[Pasted image 20240729123606.png]]
	
- Provisioned IOPS (PIOPS) SSD  	 

    ![[Pasted image 20240729124449.png]]
	
- Hard Disk Drives (HDD) 					

![[Pasted image 20240729124854.png]] 
**EBS Multi Attach - io1/io2 family**

-  Attach the same EBS volumes to multiple instances in the same AZ(Availability zones)
- Each instance has full read & write permissions to the highand  performance volume.
- Use Case : 
	- Achieve higher application availablity in clustered linux applications ( ex: Teradata)	
	- Application must manage concurrent write operations 
-  *Up to 16 instances at a time*
-  Must use  a file system  that's cluster aware not (xfs,ext4 etc...)

    ![[Pasted image 20240729135808.png]]
## AMI - Overview

- AMI - Amazon Machine Image
- AMI are a customization of an EC2 instance
	. You add your own software, configuration, operating system etc . . . 
	. Fast boot / configuration time because software is pre - packaged 
- AMI are built for a specific region ( and can be copied across regions)
- You can launch EC2 instances from :
		- A Public AMI - aws provided
		- Your own AMI - you make and maintain them yourself
		- An AWS marketplace AMI - an AMI someone else made (potentially sells)

**AMI process(From an EC2 instance)**

- Start an Ec2 instance and customize it 
- Stop the ec2 instance (for data integrity)
- Build an AMI - this will also create EBS snapshots
- Launch instances from other AMIs
  ![[Pasted image 20240726174145.png]]
	

## EC2 Instance Store

- EBS volume are network drives with good but "==limited==" performance
- *If You need high-performance hardware disk, use EC2 instance store*

- Better I/o performance
- EC2 instances store lost their storage if they're stopped (ephemeral)
- Good for buffer/cache /scratch data / temporary content
- Risk of data loss if hardware fails
- Some examples of ec2 instance store power -   
    ![[Pasted image 20240726184453.png]]
## Links

[[aws]]
[[EC2]]