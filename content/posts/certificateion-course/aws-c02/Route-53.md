---
title: "Route-53"
draft: false
---


## Route 53

[checkout](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/Welcome.html)

-  A highly scalable , fully managed authoriative  DNS
	- Authoriative = the customer (you) can update the DNS records 
-  Route 53 is also a domain registrar
- Ability to check health of your resources
- The only AWS service which provides 100% availablity SLA
- 53 is reference to traditional DNS port

### Route 53 - Records

- How you want to route traffic to a domain
- Each records contain : 
	 -  **Domain/sub-domain** name - e.g , example.com 
	 - **Record Type -** e.g , A or AAAA
	 - **Value -** e.g, 12.74.23.198
	 - **Routing policy -** how route 53 responds to queries 
	 - **TTl** - amout of time the records cached in DNS Resolvers
	 
-  Route 53 supports the following DNS record types :
	- (Must know) A / AAAA / CNAME / NS
	- (Advanced) CAA / DS / MX / NAPTR / PTR / SOA / TXT / SPF / SRV

####  Route  53 - Records types

- **A -** Maps a hostname to ipv4
- **AAAA -** Maps a hostname to ipv6
- **CNAME -** Maps a hostname to another hostname 
	- The target is the domain name whch have A  or AAAA record
	- Can't create a CNAME record for the top node of a DNS namespace ( Zone Apex)
	- Example : you can't create for example.com ,but you can create for www.example.com
	
- **NS -** Name Servers for the Hosted Zone 
	- Control how traffic is routed for a domain 


#### Route 53 - Records TTL ( Time To Live)

-  **High TTL** e.g, 24 Hour 
	- Less traffic on route 53 
	- possibly outdated records
	
- **Low TTl** e,g, 60 sec
	-  High traffic on route 53
	- updated records
	- Easy to change records

- Expect for alias records, TTL is mandatory for all each DNS record


#### CNAME vs Alias

- AWS resources (Load balancer, cloudFront . . .) expose an AWS hostname :
	-  *...aws.amazon418.com* and you want *app.example.com*
	
-  CNAME : 
	- Points a hostname to any other hostname (app.domain.com => app.example.com) 
	- **Only for Non Root Domain** ( aka app.domain.com)
-  Alias :
	-  Points a hostname to aws resource (app.domain.com => app.example.com)
	- **Works for Root and None Root Domain** (aka domain.com)
	- Free of charge
	- Native health check
#### Route 53 - Alias Records

- Maps a hostname to aws resource
- An extension to Dns functionality
- Automatically recognizes chagnes in the resource 's Ip Address
- Unlike CNAME , it can be used for the top node of a DNS namespace (Zone Apex) e.g example.com
- Alias record is always type A/ AAAA for aws resources (ipv4 / ipv6)
- *Can't set TTL* 

#### Route 53 - Alias Records Target 

- *You can not set as Alias record for an EC2 DNS name*

 ![[Pasted image 20240814170034.png]]
### Route 53 - Hosted Zone

- A container for record that route traffic to domain and their subdomain
- **Public Hosted Zones -** contains records that specify how to route traffic on the internet (public domain names) 
	application1.publicDomain.com
	![[Pasted image 20240813170418.png]]

-  **Private Hosted Zones -** contains records that specify how to route traffic within one or more VPC (private domain name)
	application.privateDomain.internal
	![[Pasted image 20240813170520.png]]

### DNS Terminologies

- **Domain Registrar** : Amazon route 53 , goDaddy....
- **DNS Records** : A, AAAA, CNAME, NS, ... 
- **Zone File :** contains DNS records
- **Name Server** : resolves Dns Query ( Authoritative or Non-Authoritative)
- **Top Level Domain (TLD)** : .com , .in , .org , .dev ...   

	![[Pasted image 20240812205339.png]]

### How DNS Works

![[Pasted image 20240813114314.png]]


----

[[aws]]


