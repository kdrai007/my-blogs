---
title: "LB -  Load balancer"
draft: false
---

## Application Load Balancer 

[checkout](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction.html)

- Application load balancers is layer 7 (HTTP)
- Load balancing to multiple HTTP applications across machines (target groups)
- Load balancing to multiple application on the same machine (ex containers)
-  Support HTTP/2 and WebSocket
- Routing Tables to different Target groups:
	-  Routing based on path in URL (example.com / ==users== &  example.com / ==auth==)	
	- Routing based on hostname in URL (==user==.example.com & ==auth==.example.com) 
	- Routing based on query strings, headers  (example.com/ users?i==d=1234&order=false==)
-  ALB are a great fit for micro services and container based applications (example : Docker & Amazon ECS)
-  Has a port mapping feature to redirect to dynamic port in ECS

### HTTP based traffic

![[Pasted image 20240801144129.png]]

### Target Groups

- 

## Network Load Balancer

[checkout](https://docs.aws.amazon.com/elasticloadbalancing/latest/network/introduction.html)

- Network load balancer (Layer 4 ) allow to:
	- Forward TCP & UDP traffic to your instance
	- handle millions of request per second 
	- Less latency ~ 100 ms (vs 400 ms for ALB) 
- NLB has one static IP per AZ, and supports assigning Elastic IP (helpful for whitelisting specfic IP) 
- NLB are used for extreme performance , TCP or UDP traffic 
- Not included in free Tier in AWS

    ![[Pasted image 20240802010227.png]]
	  
 **--  Target Groups** 

-  EC2 instances 
- Ip Addresses - must be private Ips
- Application load balancer
- Health checks supports for TCP , HTTP and HTTPS protocols

    ![[Pasted image 20240802010638.png]]


## Gateway Load Balancer

- Deply scale , and manage a fleet of 3rd party network virtual appliances in AWS
- Example: Firewalls , Intrusion Detection system and prevention sysetem , Deep Packet Inspection , palyload manipulation ....
- Operates at Layer 3 (Network Layer) - IP packets 
- Combines the following functions 
	- Transparent network gateway - Single entry / exit for all traffic 
	- Load Balancer - distributes traffic to your virtual appliances
- Use the **GENEVE** protocol on port 6081

     ![[Pasted image 20240802012451.png]]

**-- Target Groups**

- EC2 Instances
- IP Addresses - must be private IPs








## Links

----
[[aws]]
[[ELB - Elastic Load Blancer]]