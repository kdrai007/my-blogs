---
title: "AWS s3 - Advanced"
draft: false
---

## Amazon s3 - moving between  Storage Classes

- You can trnasition object with storage classes.
- For infrequently accessed object move them to Standard IA
- For archieve object that you don't need fast access to move them to **Glacier** or **Glacier deep archieve**

### Amazon s3 - Lifecycle Rules

- **Transition Actions** - configure  objects to transition to another stroage class
	- Move objects to Standard IA class after 60 day creation
	- Move glacier for archiving after 6 months 

- **Expiration Actions** - Confgire objects to expire (delete) after some time. 
	- Access log files can be set to delete after 365 days 
	- Can be used to delete old versions of file (if versioning is enabled)
	- Can be used to delete multip part upload if it's incomplete
	
	![[Pasted image 20240904105457.png]]

### Amazon s3 Analytics - Storage Class Analysis

- Help you decide when to transition object to the right storage class
- Recommendation for Standard and Standard IA :
	-  Does not work for One zone IA or Glacier
	
- Report is updated daily.
- 24 to 48 hours to start seeing data analysis

## s3 Event Notification

- Currently, Amazon S3 can publish notifications for the following events:
	- New object created events
	- Object removal events 
	- Restore object events 
	- Reduced Redundancy Storage (RRS) object lost events 
	- Replication events 
	- S3 Lifecycle expiration events 
	- S3 Lifecycle transition events 
	- S3 Intelligent-Tiering automatic archival events 
	- Object tagging events 
	- Object ACL PUT events  
	
- Use Case: generate thumnails of images uploaded to s3 
- Can create as many s3 events as desired
- *s3 event notification can be delivered in seconds but sometimes can take 1 to 2 minutes*

	![[Pasted image 20240904121717.png]]

## s3 -  Baseline Performance

- Amazon s3 automatically scales to high request rates , latency 200-300 ms
- Your application can acheive at least 3500 put/copy/post/delete or 5,500 get/head request per second per prefix in  a bucket.
- There are no number of limit of prefixes in bucket
- Example (object path =>prefix):
	- '/bucket/f1/file' => '/f1/'
	- '/bucket/f2/file' => '/f2/'
	
- If you spread reads across these 2 prefixes evenly, you can increase get/head request up to 11000 per second  

### s3 Performance
 - [read this](https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html)
 
 - **Multi Part Upload:**
	 - Recommendation for file > 100MB
		must use for files > 5GB 
	- can help prallelize upload (speed up transfers) 

- **s3 transfer Acceleration** :
	- Increase transfer speed by transferring file to an aws Edge location which will forward the data to the s3 bucket in the target location	
	- Compatible  with multi-part upload

### s3 Performance - s3 byte-Range Fetches 

- prallelize GETs by requesting specific byte size 
- Better resilience in case of failures
----
## Links

[[aws]]
[[Amazon S3]]