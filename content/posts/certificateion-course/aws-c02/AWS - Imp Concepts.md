---
title: "AWS - Imp Concepts"
draft: false
---

## EC2 Instance Metadata

[for more info](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-service.html)

- AWS EC2 Instance Metadata (IMDS) is powerful but one of the least known features to developers
- It allows AWS EC2 instances to "learn about themselves" without using IAM roles for that purpose
- The url is ` http://169.254.169.254/latest/meta-data`
- You can retrieve the IAM Role name from the metadata , But you CANNOT retrieve the IAM policy
- Metadata - Information about EC2 Instance
- Userdata - Launch script of the EC2 Instance

## MFA with CLI

- To use MFA with cli you must create temporary session 
- To do so, you must run the "STS getsession api" call
  ![[Pasted image 20240903164710.png]]

## AWS SDK

- If you want to perform action to aws with using code to perform multiple actions you should try aws sdk(software development kit)
- Some SDK are..
	- Java
	- Python (named boto3 or botocore)
	- c++ and some more...
-  What you can create with aws sdk.. 
	- ex- aws cli createted with python using aws sdk(boto3) 

## AWS Limits (Quotas)

- API Rate Limits
	- **DescribeInstances** API for ec2 have limit of 100 calls per seconds. 
	- **GetObject** on s3 have  limit of 5500 GET per second per prefix
	- For Intermittent Errors : Perorm Exponential Backoff
	- For Consistance Error Request an API throttling limit increase	
	
- Service Quotas ( Service Limits) 
	- Running on-Demand standard Instances : 1152 vCPU 
	- You can request to increase Service limit by **opening a ticket** 
	- You can request to increase service quotas by using **service quotas Api**	
	
		![[Pasted image 20240903170833.png]]
	
## Sign  

  ![[Pasted image 20240903174138.png]]
	

----
## Links

[[aws]]