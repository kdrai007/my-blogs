---
title: "AWS - CloudFront"
draft: false
---

## CloudFront
[checkout](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.htmlhttps://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

- CloudFront is a Content Delivery Network(CDN)
- Improved read performance, content is cached at the edge
- Improves User Experience
- 216 points of presence globally ( edge locations)
- DDos protection, integration with shield, Aws Web Application Firewall

### Cloudfront - Origin

- S3 Bucket :
	- For distrubuting files and caching them at the edge
	- Enhanced security with CloudFront Origin Access Control(OAC)
	- OAC is replacing Origin Access Identity (OAI)
	- Cloudfont can be used as Ingress ( to upload files to s3)

- Custom Origin (HTTP) : 
	 - ALB
	 - EC2
	 - S3 Static Site 
	 - Any backend your choice

### CloudFront vs s3 Cross Region Replication

- CloudFront :
	- Global Edge Network
	- Files are cached for a TTL ( for a day)
	- Greate for static content that must be available everywhere

- S3 Cross Region Replication  : 
	-  Must be setup for each region you want Replication to happen
	-  Files are updated in Real-time 
	- Read-only
	- Great for dynamic content that's needto available at low-latency in few regions

## CloudFront Caching

- The cache lives at each cloudfront edge location
- Cloudfront identifies each object in the cache using **Cache key** 
- You want to maximize the ratio of Cache Hit for minimizing requests to the origin
- You can invalidate part of the cache using **CreateInvalidation API**

### What is Cloudfront Cache Key

- A unique identifier for every object in the cache 
- By default , consists of hostname + Resource portion of the URL
- If you have an application that serves the content varies on user's location,language...
- You can add others things like (HTTP Headers, cookies, query string ) to the cache key using **CloufFront Caching policy**
	![[Pasted image 20240909003144.png]]

#### Cloudfront policy - Cache Policy

- Cache based on:
	- HTTP headers :  None - Whitelist
	- Cookies: None  - Whitelist - Include all-Except - All 
	- Query String: None  - Whitelist - Include all-Except - All 

- Control the TTL ( 0 seconds to 1 year) , can be set the origin using **Cache-Control** header, and **Expires**  header..
- Create your own policy or use predefined Managed policy
- **All HTTP Headers, cookies, Query String that you include in the cache key are autmatically included in origin request**

#### CloudFront Policies - Origin Request Policy 

- Specify values that you want to include in origin  request without  including them in the cache key (no duplicated cache content)
- You can include :
	- **HTTP Headers :**  None - Whitelist - All viewer header options
	- **Cookies:** None - Whitelist - All
	- **Query String :** None - Whitelist - All

- Ability to add Cloudfront Http Headers  and Custom Headers to an origin requests that were not included in the viewer request
- Create  your own policy or use predefined Managed policy

### CloudFront - Cache Invalidations

- In Case you update the back-end origin , cloudFront doesn't know about it and only users get refreshed content after TTL has expired
- However, you can force entire or partial cache refresh ( bypass TTL) by performing **CloudFront Invalidation**
- You can invalidate entire files (* ) or special part of it ( /files/* )  

### CloudFront Cache Behaviors

- Configure different setting for  given URL Path pattern
- For ex, One specific cache behavior for path images/* .jpg files on your origin web server
- Route to different kind of origins/origin based on the content type or path pattern 
	- /images/*
	- /api/*
	- /* (default cache behavior)
-  Default cache behavior always last to be **processed and is always /***
	![[Pasted image 20240910143557.png]]

### CloudFront - ALB or EC2 as an Origin

![[Pasted image 20240910234113.png]]

### CloudFront - Geo Restriction

- You can restrict who can access your distribution :
	- AllowList - Allow user' s access of your content based on their countries approval status 
	- BlackList - Block user' s access of your content based on their countries  approval status 
-  The "country" is dicided using a 3rd party Geo ip-database
- Use Case : Copyright laws to control access to content

### CloudFront - Signed Url / Signed cookies

- You want distribute paid content to premium users around the world
- We can use Cloudfront signed url/signed cookies : we attach policy with :- 
	- Included URL expiration
	 - Included IP ranges to access the data from
	 - Trusted Signers (choose which aws account can create signed urls)

- How long a url should be valid for?
	- Shared Content (movie,music) - make it short (few minutes) 
	- Private Content (private to the user) - you can make it last for years

- Signed Url = access to one file 
- Signed Cookie = access to multiple files

#### CloudFront - Signed Url Process

- Two types of signers :
	- Either a trusted key group(recommended)
		- Can leverages APIS to create and rotate keys (and IAM for API Security)
	- An Aws account that contains a cloudfront key pair	
		- Need to manage keys **using root account and AWS console** (Not Recommended)

- In your cloudFront distribution you can create more and one **Trust Key Groups**
- You generate your own public / private key
	- The private key is used by your applications (e,g. EC2) to sign urls
	- The public key is used by cloudfront to verify URLs

### CloudFront - Origin Groups

- To increase high-availability and do failover
- Origin group : one primary and one secondary origin 
- if primary origin failed , the second one is used

### CloudFront - Field Level Encryption

- Protect user's sensitive information through application stack
- Adds an extra layer of security along with HTTPS
- Sensitive information is encrypted at the edge close to user
- Uses asymmetric encryption
-  Usage :
	- Specify set of fields in POST request that you want to be encrypted (up to 10 fields)

### CloudFront - Real Time Logs

- Get real-time requests received by cloudFront sent to **Kinesis Data streams**
- Monitor , analyze and take action based on content delivery performance 
- Allow you to choose :
	- **Sampling Rate -**  Percentage of request for which you want to receive 
	- Specific fields and specific cache behavior (path patterns)

	![[Pasted image 20240912023808.png]]

----
## Links

[[aws]]
