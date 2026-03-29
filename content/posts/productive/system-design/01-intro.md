---
title: "01-intro"
id: 01-intro
aliases: []
tags:
  - #system-design
  - excalidraw
  - productive
---

## System Design

System design is the process of defining the architecture,interface and data for system that satisfies
specific requirement. 
A good system design requires us to think about everything, from infrastructure all the way to how we store data.


## How to: System Design

There are several step that can be taken while system design:

- **Understand the problem** - Gather information of the problem you are solving and the requirement of the system.
- **Identify the scope of the system** - According to accumulated data on the problem, create scope of the system for ex, for whom the system you are designing, what system will do and what not.
- **Research and analyze the existing system.** - Research all or some available system and analyze, what kind of system or resources you will need.
- **Create a high level design.** - Don't leave anything unresearched,  
- **Refine the design** - Don't run away to recheck your created design.
- **Document the design**. - Create well detailed document for future reference.
- **Continuously monitor and improve the system** - If you find anything missing improve and keep updating system until you get satisfactory  result.

### Why system design is important?

System  design help us define a solution that  meets the business requirement.
Often it is essential to think from high level as these decisions are very difficult to correct later.

## Latency and throughput

**Latency**  - Latency refers to the amount of time a system take time to respond to request.
**Throughput**  -  Throughput refers to the amount of request a system can handle at the same time.

Generally, We should aim for maximal throughput with acceptable latency.

## Performance vs  Scalability

A service is **scalable** if it results in increased **performance** in a manner  proportional  to resources added.  
 - If you have a performance problem ,Your system is slow for single user. 
 - if you have a scalability  problem , your system is fast for single user but slow under heavy load.

## Cap Theorem

### Availability vs Consistency

- **Availability** - Means that a system is always ready to respond to requests. If you ask the system for information or to perform a task, it will respond quickly even if some of the parts is not working .

- **Consistency** - Means that every time you read data from the system, you get the most  recent and correct version of data.


- **Cap Theorem** - According to cap theorem , in a distributed system you can support only two of them following:- 

- Consistency
- Availability
- Partition tolerance - The system continue to operate despite arbitery partitioning  due to network failures.

#### AP - Availability and Partition tolerance

Waiting for a response from the partitioned node might result in a timeout error. CP is a good choice if your business needs require atomic reads and writes.

#### CP - Consistency and Partition tolerance

Responses return the most readily available version of the data available on any node, which might not be the latest. Writes might take some time to propagate when the partition is resolved.
AP is a good choice if the business needs to allow for eventual consistency or when the system needs to continue working despite external errors.


## Links

[[tags/system-design]]
[[tags/Being Productive|Being Productive]]




