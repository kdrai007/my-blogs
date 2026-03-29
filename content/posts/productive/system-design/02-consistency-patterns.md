---
title: "02-consistency-patterns"
id: 02-consistency-patterns
aliases: []
tags: []
---

# Consistency patterns

Consistency patterns refers to the ways in which data is stored and managed in a distributed system, and how the data is made available to the users and application. There are three main components of consistency patterns 

1. Strong consistency
2. Weak consistency
3. Eventual consistency

Before we Learn more about consistency patterns we need to learn about, Exactly what is distributed system. 

#### Distributed System

Distributed systems are those where for every major or important components actions there's different networked system and they cordinate among them using by passing messages to each other. 

for ex, Suppose there's social media website where users can create account,chat and share contents between them. So,to handle these functionalities there's different servers for handling these functions like,  user's account and for storing details  on database

### Strong Consistency

After an update made to the data, it will immediately visible to any subsequent read operations. The data is replicated in synchronous manner, ensuring them all copy of the data is updated at the same time.

example,For strong consistency based systems are like Financial system where **Data Integrity** is very important. So, systems are designed in a way that all the data is stored in same place and updates to the data is reflected to all other locations. This consitency systems ensures that all components are working on same and accurate data   

### Weak Consistency

In a weakly consistent system,Updates to the data may not be immediately  propagated. This can lead to inconsistencies and conflicts between different version of data, but its also allows for **high availability** and **Low latency**. 

Example for Weak consistent system will be like where there's no need for instantly updated data across all servers. Suppose, gaming platform where users can play online multiplayers games 

### Eventual Consistency

Eventual Consistency is a form of weak consistency. After update made to the data, it will eventually visible to any subsequent operations. The data is replicated in asynchronous manner, ensuring that all copies of data will be eventually updated.



