---
title: "ELB - Elastic Load Blancer"
draft: false
---


# ELB - Elastic Load Balancer 

### Scalability 

-  Scaliablity means that an application / system can handle greater loads by adapting
-  There are two kinds of scalability :
		1. Vertical Scalability 
		2. Horizonal Scalability (= elasticity)
-  Scalability is linked but different to high availabilty.

**Scalability - Vertical Scalability**

- Vertical Scalability means scaling the size of the instance. 
- For example, your application is running on t2.micro Scaling that machine vertically means upgrading t2.micro into t2.large 
- VS is very common for non-distributed system like Database.
- RDS, elastic cache are services that can scale vertically.
- There's usually limit on how much you can vertically scale (hardware limit)

**Horizontal Scalability**

- Horizontal Scalability means increasing the number of instances / systems for your application 
- Horizontal scaling implites distributed systems.
- This is very common for web application / modern application 
- It's easy to scale thanks fo cloud offering such as Amazon EC2 

### High Availability

- High Availability usually goes hand in hand with horizontal scaling
- HA means running your application / system in at least 2 data centers (== Availability zone) 
- The goal of HA is to survive a data center loss.
- The HA can be passive (for RDS multi AZ  for example )
- The HA can be active (for horizontal scaling)
### High Availability  & Scalability for EC2

- Vertical Scaling increase instance size (=scale up / down)
	- From t2.nano - 0.5 G of Ram , 1 vCPU 
	 - To: u-12tb 1.metal - 12.3 TB of Ram , 448 vCPUs 
-  Horizontal scaling increase the number of instances (= scale out / in  )
	-  Auto Scaling group 
	 -  Load Balancer
-  High Availability: Run instances for same application in across multi  different AZ  
	-  Auto Scaling group multi AZ
	 -  Load Balancer multi AZ 


### Load Balancing

#### What is load Blancing

- Load balancer are server that forward traffic to multiple server( eg ,. EC2 instances) downstream  
     ![[Pasted image 20240731172442.png]]
#### Why use Load Balancer

- Spread load across multiple downstream instances
- Expose a single point of access (DNS) to your application
- Seamlessly handle failure of your downstream instances
- Do regular health checks of your instances
- Provide ssl termination (https) for your websites.
- Enforce stickiness with cookies
- High availability across AZ
- separate private traffic from public traffic

#### Why use the elastic load balancer

- An elastic load balancer is **managed load balancer**
	- AWS  guarantee that it will be working 
	- AWS takes care of maintenance, upgrades and high availability. 
	- AWS provides only few configuration knobs.
-  It cost less if you setup your own load balancer but you will have to put more effort to keep it working
-  It is integrated to various aws offerings	
	- EC2, EC2 auto scaling Groups, Amazon ECS 
	- AWS certificate manager (ACM), CloudWatch  

#### Health Checks

- Health Checks are crucial for load balancer
- They enable the load balancer to know if instances it forward traffic to are available to replay to requests
- The health check is done on a port and a route ( /health is common)
- If the request is not 200 (Ok) , then the instance is unhealthy.

   ![[Pasted image 20240731182304.png]]
#### Types of load balancer on AWS

- AWS has **4 kinds of managed load Balancer**
- Classic Load Balancer (vl  - old generation ) - 2009 - CLB
	- HTTP , HTTPS , TCP , SSL (secure TCP)
-  Application Load Balancer (v2 - new generation) - 2016 - ALB
	- HTTP , HTTPS , WebSocket 
- Network Load Balancer (v2- new generation ) - 2017 - NLB 
	- TCP , TLS (secure TCP ) , UDP 
-  GateWay Load Balancer (v2- new generation ) - 2020 - GWLB

- Some load balancer can be setup as internal(private) or external (public)

**--** Recommended  to use New Generation Load balancer as they provide more features

#### Load Balancer Security Groups

![[Pasted image 20240731184442.png]]



## Links

[[aws]]
