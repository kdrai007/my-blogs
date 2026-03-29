---
title: "Amzon - ECS"
draft: false
---

tag: #aws #aws-copilot  #aws-ECR

# ECS - Elastic Container Service
[checkout](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/create-container-image.html)

- Amazon Elastic Container Service (ECS) is a fully managed container orchestration service that helps you to more efficiently deploy, manage, and scale containerized applications.
## ECS  - Launch Type

### EC2 Launch Type

- Launch docker container on AWS = Launch **ECS tasks** on ECS clusters
- Ec2 Launch Type : you must provision and maintain the  infrastructure ( the EC2 Instances)
- Each EC2 instance must run the ECS agent to register in the ECS cluster
- Aws takes care of starting / stopping containers

### Fargate Launch Type

- Launch docker container in AWS
- You do not provision the infrastructure (no EC2 instance to manage)
- It's all serverless
- You just create task definitions
- To scale , juse increase number of tasks . Simple - no more ec2 instance

## ECS - Iam Roles 

- EC2 Instance profile ( EC2 launch type only):
	- Used by the ECS agent
	- Makes API call to ECS service 
	- Send container logs to CloudWatch logs
	- Pull docker images from ECR
	- Reference sensitive data in Secrets Manager or SSM Parameter Store

- ECS task Role :
	- Allows each task to have a specific role
	- Use different role for the different ECS service you run  
	- Task role is defined in the task definition

### ECS - Load Balancer Integrations

- **Application Load Balancer** supported and works for most of the cases
- **Network Load Balancer** recommended only for high throughput / high performance cases , or to pair it with aws Private link 
- **Classic Load Balancer** you can use but (not recommended , no advance feature - no fargate)

### ECS - Data Volumes (EFS)

- Mount EFS file system in ECS tasks 
- Work with both EC2 and fargate launch type
- Tasks running in any AZ will share the same data in EFS file system
- Fargate+EFS = serverless

- Use Case : persistent shared storage in Multi-AZ for your containers

### ECS - Service Auto Scaling

- Automatically increase/decrease the desired number of ECS tasks
- Amazon ecs auto scaling uses **AWS Application Auto Scaling**
	- ECS service Average CPU utilization 
	- ECS service Average Memory utilization - Scale on RAM
	- ALB request count per target - metric coming from ALB

- **Target Tracking -** Scale based on target value for a specfic cloudwatch metric 
- **Step Scaling -** scale based on specifed cloudwatch alarm 
- **Scheduled  Scaling -** scale based on specifed data/time (preditable change)

- ECS Service auto scaling (task level) != EC2 auto scaling(ec2 instance level)
- Fragate auto scaling is much easier to setup(serverless)

#### EC2 Launch type - Auto Scaling Ec2 Instances

- Accomodate ECS service scaling by adding underlying Ec2 instances
- **Auto Scaling Group Scaling**
	- Scale your ASG based on CPU utilization
	- Add EC2 instances over time 

- **ECS Cluster Capacity Provider**
	- Used to automatically provision and scale the infrastructure for your ECS tasks
	- Capacity provider paired with an Auto Scaling Group
	- Add Ec2 instance when you're missing capacity(CPU,RAM...)

### ECS - Rolling Update

- When updating from v1 to v2 we can control how many tasks can be started and stopped, and in which order
	![[Pasted image 20240916145712.png]]

### ECS - Task Definitions

- Task definitions are metadata in Json from to tell ECS how to run Docker container 
- It contains crucial information, such as: 
	- Image name
	- port binding for Container and host
	- Memory and Cpu required
	- Environemnt variables
	- Networking information
	- Iam Role
	- Logging configuration (ex CloudWatch)
	
- Can define up to 10 containers in task definitions

#### ECS - Load Balancing(EC2 launch type)

- We get a Dynamic Host Port Mapping if you define only the container port in the task definition
- The ALB finds the right port for your Ec2 instance

	![[Pasted image 20240917005240.png]]
	
- **Must allow any port in ec2's security group to allow any port from ALB's security group**
#### ECS - Load Balancing(Fargate launch type)

- Each task the **Unique Private IP**
- Only define the container port ( host port is not applicable)

	![[Pasted image 20240917203225.png]]

#### ECS - One IAM roles per task Definitions
 ![[Pasted image 20240917203631.png]]

#### ECS - Environment Variables

- ENV :-
	- HardCoded e.g, URLs
	- SSM Parameter Store - sensitive variables (e.g, API keys, shared configs) 
	- Secrets Manager - sensitive variables (e.g, passwords)

- Environment Files(bulk) - S3


#### ECS - Data Volumes (Bind Mounts)

- Share data between multiple containers in the same task definitions
- Work for both EC2 and fargate tasks
- EC2 tasks - Using Ec2 instance storage
	- Data are tied to the lifecycle of  the ec2 instance

- Fargate tasks - using ephermeral storage
	- Data are tied to the containers using them
	- 20 GiB to 200 Gib (default 20 Gib)		
	
	![[Pasted image 20240917205941.png]]	

### ECS - Tasks Placements

- When a task of type EC2 launched, ECS must determine where to place it, with the constraints of CPU memory, and available ports
- Similarly, when a service scales in Ecs needs to determine which tasks to terminate.
- To assist it with this, you can define a **task placement strategy** and **task placemnts constraints** 

- Note- only for ec2 not for fargate launch type

#### ECS - Task placement process

- When amazon ECS places tasks , it uses the following process to select container instances :
	1.  Identify the instances that satisfy the cpu,memory and port requirements in the task definitions
	2. Identify the instances that satisfy the task placement constraints
	3. Identify the instances that satisfy the task placement strategies 
	4. Select the instaces for task placement

#### ECS - Task placement strategies

- Binpack
	- Places tasks based on the least available amount of CPU or memory
	- This minimizes the number of instances in use

- Random
	- Place the task randomly
	
- Spread 
	 - Places the tasks evenly based on the specified value
	 - Example: instanceId,attribute:ecs-availability-zone

#### ECS - Task placement Constraints

- distincetInstance: place each task on a different container instance

```json
"placementConstraints":[
	{
		type: "distinctInstance"
	}
]
```

- memberOf: places tasks on instance that satisfy an expression
	- Uses the Cluster Query Language(advanced)	
	
```json
"placementConstraints":[
	{
		expression:"attribute:ecs.instance-type =~t2.*",
		type: "distinctInstance"
	}
]
```

## Amazon ECR

- ECR - Elastic Container Registery
- Store and manages docker images on AWS
- Private and Public Repository
- Full integrated with ECS, backed by s3 
- Access is controlled through IAM ( permission errors=>policy)
- Supports image vulnerability scanning,versioning,image tags,image lifecycle...

## AWS Copilot

![[Pasted image 20240919172741.png]]


-----
## Links

[[aws]]
[[AWS - Container]]