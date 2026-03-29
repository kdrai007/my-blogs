---
title: "Auto Scaling Group"
draft: false
---

## Auto Scaling Group

**Definition -**   
An Amazon EC2 Auto Scaling group (ASG) contains a collection of EC2 instances that share similar characteristics and are treated as a logical grouping for the purposes of fleet management and dynamic scaling.

- In real-life , the load on your application  & website can change
- In the cloud , you can create and get rid of server very easily

- The goal of Auto Scaling Group (ASG) is to :
	- Scale out (increase ec2 instance ) to meet the required need. 
	- Scale in (remove ec2 instance) to match the decrease load. 
	- Ensure we have min and max instances are running
	- re-create an EC2 instance if in case any instance is terminated 	
	- Automatically register new Instance to load balancer

#### Auto Scaling - CloudWatch Alarms & Scaling

- It is possible to scale ASG based on CloudWatch Alarms
- An alarm monitors a metric (such as ==Average CPU== , or a ==Custom metric==) 
- Metrics such as Avergae CPU are computed for the overall ASG instances
- Based on Alaram : 
	- We can create scale-out policies.
	- We can create scale-in policies.
   ![[Pasted image 20240804150351.png]]

----
## Links

[[LB -  Load balancer]]

[[ELB - Elastic Load Blancer]]