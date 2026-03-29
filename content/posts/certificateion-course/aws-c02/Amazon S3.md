---
title: "Amazon S3"
draft: false
---

# Amazon s3
[checkout](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)

Amazon Simple Storage Service (Amazon S3) is an object storage service that offers industry-leading scalability, data availability, security, and performance. 

- Amazon s3 is one of the main building blocks of AWS
- It's advertised 'infinitly scaling' storage
- Many website use s3 as there's backbone
- **Uses Cases**
	- Backup and stroage
	- Diaster recovery
	- Archieve
	- Hybrid Cloud hosting
	- Application hosting
	- Media hosting
	- Data lakes & big data analytics
	- Software delivery

## Amazon s3 - Buckets

- Amazon s3 allows people to store objects (files) in "buckets" (directories)
- Buckets must have globally unique name (across all regions all accounts)
- Buckets are defined at region level
- s3 looks like global service but buckets are created in a region.
- Naming convention
	- No underscore, No uppercase
	- 3-63 characters long
	- Not an IP
	- Must start with lowercase letter or number
	- Must not start with prefix xn--
	- Must not end with suffix --alias

## Amazon s3 - Objects

- Objects (files) have a key
- The *Key* is the **full** Path:
	- s3://my-bucket/**file.txt**	
	- s3://my-bucket/**my_folder/some_folder/file.txt**

- The key is composed with *prefix* + **object name**
	- s3://my-bucket/*my_folder/some_folder*/**file.txt**

-  There's no concept of "directories" in s3 buckets
- Keys are very long name that contain "/"

### Objects (Content.)

- Objects values are the content of the body.
	- Max. object size is 5TB (500GB)
	- if uploading more than 5GB size of file, must use "multi-part upload"

- Metadata ( list of text keys / value pairs - system or user metadata)
- Tags (Unicode key / value pair - up to 10) - useful of security / lifecycle
- Version Id (If "versioning" is enabled)

## Amazon s3 - Security

- **User-Based**
	- **IAM policies** - which API calls should be allowed for a specific user from IAM
	
- **Resource Based** 
	- **Bucket Policies -** bucket wide rules from the s3 console - allow cross account
	- **Object Access control List (ACL) -** finer grain (can be disabled)
	- **Bucket Access Control List (ACL) -** less common (can be disabled)

- **Encryption -** encrypt objects in Amazon s3 using encryptions keys

## Amazon s3 - Static Website Hosting

- s3 can host static websites and have them accessible on the Internet
- The website url will be (depending on the region)
	![[Pasted image 20240830123242.png]]

- If you get **403 forbidden** error , make sure the bucket have public access

## Amazon s3 - Versioning

-  You can version your file in amazon s3 
- It is enabled at the **bucket level**
- Same key overwrite will change the "version":1,2,3...
- It is best practice to version your bucket
	- Protect against unintended delete (ability to restore a version)
	- Easy roll back to prev version
	
- Note:
	- Any file that is not versioned prior before enabling versioning will have version "null"
	- Suspending versioning does not delete prev versions

## Amazon s3 - Replication

- **Cross-Region Replication (CRR):** Replicates objects to a bucket in a different AWS region. This helps improve data durability, availability, and compliance with geographical regulations.

- **Same-Region Replication (SRR):** Replicates objects within the same AWS region, useful for data duplication, backups, or to comply with regulatory requirements.

- **Replicate Existing Objects:** Allows you to replicate existing objects in a bucket (using S3 Batch Replication), not just newly added objects.

- **Replicate Specific Objects:** You can configure replication rules to replicate all objects or filter based on prefixes, tags, or object metadata.

- **Automatic Handling of Object Changes:** Handles changes to objects, such as updates or deletions, based on the replication configuration set for the bucket.

- **Supports Encrypted Objects:** Works with objects encrypted with AWS Key Management Service (KMS) or server-side encryption with Amazon S3-managed keys.

### Replication - Notes

- After you enable replication only new objects are replicated
- Optionally, you can replicate existing object using , **s3 Batch Replication**
- For Delete Operations:
	- Can replicate Delete Markers from source to target ( optional setting)
	- Deletions with a version ID are not replicated ( to avoid malicious deletes)
	
- There is "no" chaining of replication 
	- If bucket 1 has replication into bucket 2, which replication into bucket 3  
	- The objects that are created in bucket 1 are not replicated into bucket 3

## Amazon s3 - Storage Classes

1. Amazon s3 standard - General purpose
2. Standard-Infrequent Access 
3. One Zone Infrequent Access
4. Glacier Instant Retrieval
5. Glacier Flexible Retrival
6. Glacier Deep Archieve
7. Intelligent Tiering

- Can move between classes manually or using s3 lifecycle configurations

	![[Pasted image 20240901100221.png]]


----
## Links

[[aws]]

