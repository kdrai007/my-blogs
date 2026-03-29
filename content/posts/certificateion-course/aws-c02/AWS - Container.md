---
title: "AWS - Container"
draft: false
---

# Containers
[checkout](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-container-image.html)
## Docker

- Docker is software development platform to deploy apps
- Apps are packaged in **containers** that can be run on any OS
- Apps run the same regardless of where they run 
	- Any Machine
	- No compatibility issue
	- Predictable behavior
	- Less work
	- Easier to maintain and deploy
	- Work with any language, any OS, any technology
	
- Use cases : Microservices architecture , lift and shift apps from on-premises to aws cloud ... 

### Where are Docker images stored?

- Docker images are stored in docker repositories 
1. Docker Hub `https://hub.docker.com`
2. Amazon ECR (Amazon Elastic container repository)
	- Private Repo
	- Public Repo 

### Docker  vs Virtual Machines

- Docker is "sort of " Virtualization technology , but not exactly
- Resources are shared with the host => many container on one server

- process :- 
	![[Pasted image 20240912095410.png]]

## Docker Containers Management on AWS

- Amazon Elastic Container Service (Amazon ECS) 
	- Amazon's own container platform

-  Amazon Elastic Kubernetes Service (Amazon EKS) 
	- Amazon's managed kubernetes ( open source)
	
- AWS Fargate 
	-  Amazon's own serverless container platform
	- Works with ECS and EKS
	
- Amazon ECS  
	- Store container images
	

----
## Links

[[aws]]