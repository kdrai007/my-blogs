---
title: "AWS- Beanstalk"
draft: false
---

**Date**  : 2024-09-21
**Links** : 

# Beanstalk

#### Overview

- Elastic Beanstalk is a developer centric view of deploying an application on AWS
- It uses all the component's we've seen before: EC2,ASG,ELB,RDS...
- Managed Service
	- Automatically handles capacity provisioning ,load balanceing, scaling, application health monitoring, instance configuration...
	- Just the application code is the responsbility of developer
- You still have full control over configuration
- Beanstalk is free but you pay for underlying instances

### AWS Beanstalk - Components

- **Application** : collection of Elastic Beanstalk components (enviroments, versions, configurations...)
- **Application version** : an iteration of your application code
- **Environment** : 
	- Collection of aws resources running on application version(only one application version at a time)
	- Tiers : Web Server Environment Tier & Worker Environment Tier
	- You can create multiple environments(dev,test,prodction...)	
	![[Pasted image 20240921174632.png]]

	![[Pasted image 20240921174751.png]]

### AWS Beanstalk - Web Server & Worker Tier

| Feature     | Web service Tier                     | Worker Tier                                 |
| ----------- | ------------------------------------ | ------------------------------------------- |
| Handles     | http/https requests(web traffic)     | Background tasks (async jobs)               |
| Purpose     | Serving web application and apis     | processing jobs from Queue                  |
| Scaling     | Based on traffic (incoming requests) | Based on SQS queue length ( number of jobs) |
| Example<br> | E-commerce site, api service         | Image resizing, report generations          |

### Beanstalk Deployment Options for Updates

- **All at once( deply all in one go) -** fastest, but instances aren't available to serve for a bit(downtime)
- **Rolling -** update a few instances at a time(bucket), and then move onto the next bucket once the first bucket is healthy
- **Rolling with additional batches -** like rolling, but spins up new instances to move the batch(so that old application is still available)
- **Immutable -** spins up new instances in a new ASG, deploys version to these instances, and then swaps all the instances when everything is healthy.
- **Blue Green -** Create a new environment and switch over when ready 
- **Traffic splitting -** canary testing - send small amount % of traffic to new deployment


### Elastic Beanstalk Deployment process 

- Describe dependencies (requirement.txt for python, package.json for nodejs)
- Package code with zip, and describe dependencies
	- python:*requirement.txt*
	- nodejs:*package.json*
- **Console -** Upload zip files (creates new app version),and then deploy
- Elastic beanstalk will deply the zip on each ec2 intances , resolve dependencies and start the appliationc


### Beanstalk Lifecycle policy

- Elastic beanstalk and store upto 1000 applicatoins versions
- If you don't remove old version you can't deploy any new version
- To phase out old application versions, use **lifecycle policy**
	- Based on time (old versions are removed)
	- Based on space (when you have to many versions)
- Versions that is already in use won't be deleted


### Elastic Beanstalk Extentions

- A zip file containing out code must be deployed to Elastic Beanstalk 
- All the paremeters set in the UI can be configured with code using files
- Requirements:
	- in the .ebextensions/ directory in the root of source code 
	- Yaml/Json format
	- .config extension (ex json.config)
	- Able to modify some default setting using: option_settings
	- Ability to add resources such as RDS,ElasticCache, DynamoDB,etc...

- Resources managed by .ebextensions get deleted if environment goes awa
