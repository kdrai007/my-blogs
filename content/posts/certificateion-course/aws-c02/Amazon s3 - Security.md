---
title: "Amazon s3 - Security"
draft: false
---

## Amazon s3 - Object Encryption 
[for more info:-](https://docs.aws.amazon.com/AmazonS3/latest/userguide/security.html)



- You can encrypt object in s3 using one of the 4 methods
-  Server Side Encryption (SSE)
	 -  SSE with Amazon-s3 managed keys (SSE=S3) - Enabled by default
	 - SSE with KMS keys stored in AWS KMS (SSE-KMS)
		 - Levrage aws key management service to manage encryption keys
	- SSE with customer provided keys (SSE-C) 
		- When you want to manage your encryption keys

-  Client Side Encryption (CSE)
	- To Encrypt your data before you send them on s3 buckets

- Amazon s3 - Encryption in transit(SSL/TLS)
	- Encryptin in flight also called (SSL/TLS)
	- Amazon s3 Exposes 2 endpoints:
		- HTTP endpoint : non-encryption endpoing
		- HTTPS endpoint : encryption in flight  
	- HTTPS is recommended
	- HTTPS is mandatory for SSE-C

### Amazon s3 - Default Encryption vs Bucket Policies

- SSE-S3 encryption is automatically applied to new objects stored in s3 bucket.
- Optionally you can use "Force Encryption" using a bucket policy and refuse any API call to PUT an s3 objects without encryption headers (SSE-KMS or SSE-C) 
	![[Pasted image 20240905173311.png]]
	
- Bucket Policies are evaluated before "Default Encryption" 

## CORS 

- Cors is Cross Origin Resouce Sharing
-  Origin = Scheme(protocol) + host(domain) + port
	-  example : `https://localhost.com` (implied port 443 for HTTPS, 80 for HTTP)
- **Web Browser** based machanism  to allow request to other origin while visting the main origin	![[Pasted image 20240905175147.png]]

### Amazon s3 - CORS

- If a client make a cross-origin request to our s3 bucket, we need to enable correct cors Headers
- You can allow for a specific origin or * (all origin) 

##  Amazon s3 - MFA Delete

- MFA (Multi-Factor Authentication) - Force users to generate code on a device ( usually mobile or hardware ) for  doing important functions on s3
- MFA required for: 
	- To Permanentaly delete a s3 bucket
	- Suspend versioning on s3 bucket
	
- MFA won't be required for:
	- To enabling versioning
	- List deleted versions

-  To use MFA delete **Versioning must be enabled** on the bucket
- **Only the bucket owner(root account) can enable/disable MFA delete**

## Amazon s3 - Access Logs

- For Audit purposes you may  want, to log all your access logs to s3 buckets 
- Any request made to s3 bucket, authorize or denied all recored will be log in anohter s3 bucket
- That that can be analyzed  by any data analysis tool
- The target logging bucket should must be in same region

####  Warning:

-  Never allow your logging bucket to be monitored bucket
- It will create a logging loop and the bucket size will increase exponentially

## Amazon s3 - Pre Signed URL

- Generate pre-signed url using cli,aws sdk  or aws console
- URL Expiration:
	- AWS console - 1min up to 7200 min (12 hours)
	- CLI - default 3600 sec and max up to 168 * 60 sec (168 hours)

-  Users given a pre-signed URL inherit the permissions of the user that generated the URL for GET/PUT

## Amazon s3 - Access Point

![[Pasted image 20240905223855.png]]

- Access Points simplify security management for s3 buckets
- Each Access Point has:
	- its own dns name (Internet Origin or VPC origin)
	- an access point policy (similar to bucket policy) - manage security at scale	
	![[Pasted image 20240905225505.png]]


## Amazon s3 - Object Lambda

- Use AWS Lambda function to change the object before it is retrieved by the caller application
- Only one s3 bucket is needed, on top of which we create,s3 Access point and object lambda access point 
	![[Pasted image 20240905230409.png]]

----
## Links

[[aws]]
[[Amazon S3]]