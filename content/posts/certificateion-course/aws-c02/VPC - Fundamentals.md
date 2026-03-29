---
title: "VPC - Fundamentals"
draft: false
---

# VPC
[checkout](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)

With Amazon Virtual Private Cloud (Amazon VPC), you can launch AWS resources in a logically isolated virtual network that you've defined.

- **VPC** : private network to deploy your resources (regional resource)
- **Subnets** allows you to partition your network insdie your VPC (Availbility zone resource)
- A **public subnet** is subnet that is accessible through public internet
- A **private subnets** is subnet that is not accessible through internet
- To define access through internet and between subnets, we use **Route Tables**

	![[Pasted image 20240826130440.png]]
	
## Internet Gateways & NAT Gateways

- **Internet Gateways** helps our VPC instances connect with the internet
- Public Subnets have route to the internet gateways 

- **NAT Gateways** (Aws managed) & **NAT Instances** (self-managed) allow your instances in private subnets to access the internat while remaining private

	![[Pasted image 20240826134131.png]]

## Network ACL & Security Groups

- **NACL** (Network ACL) 
	-  A firewall which controls traffic from and to subnet
	- Can have Allow and Deny rules
	- Are attached at the **subnet** level
	- Rules only includes IP addresses

- **Security Groups** 
	- A firewall that controls traffic to and from an ENI / EC2 Instance 
	- Can have only ALLOW rules
	- Rules include Ip addresses and other security groups

## VPC Flow Logs

- Capture information about ip traffic going into your interfaces:
	-  VPC flow logs
	- Subnet flow logs
	- ENI(Elastic Network Interface) flow logs

- Heps in monitor & troubleshoot connectivity issues . Example
	- Subnets to Internet
	- Subnets to subnets
	- Internet to Subnets

- Captures network information  from AWS managed interfaces too like , ELB, Elasticache , RDS , Aurora etc
- VPC flow logs data can go to s3 , CloudWatch logs, kinesis Data firehose 

## VPC Peering

- Connect two network, privately using AWS's network
- Make them behave as if they are in same network 
- Must not have overlapping CIDR (ip address range)
- VPC Peering connection is **not transitive** ( Must be established for each VPC that need to communicate with one other )

	 ![[Pasted image 20240826143757.png]]

## VPC Endpoints

- Endpoints allows you to connect to AWS services using a **private network** instead of the public www network
- This gives enhanced security and lower latency to acces AWS services
-  VPC Endpoint Gateways : s3 & dynamoDb
- VPC Endpoint interface: the rest
- Only Used inside your VPC

	![[Pasted image 20240826144654.png]]

## Site to Site  VPN & Direct Connect

- **Site to Site VPN**
	- connect an on-premise vpn to AWS
	- The connection is automatically encrypted
	- Goes over the public internet
- **Direct Connect**(DX)
	- Establish physical connection between on-premise and AWS
	- The connection is private secure and fast
	- Goes over the private network
	- Takes at-least month to establish
----
## Links

[[aws]]
[[EC2]]