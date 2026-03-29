---
title: "part-2 Data Models & Query"
draft: false
---

Tags: #data-intensive #data-model

# Data Models & Query languages


Data models are perhaps the most important part of developing software,because they have such a profound effect not only on how the software is written, but also on how we tackle *real world problems*. 

Most applications are built by layering one data model on top of another. For each layer, the question is: how it is represented in terms of next lower layer?  for example: 

1. As an application developer, you look at the real world (in which there are people, organizations, goods, actions, money flows, etc) and model it in terms of *objects* or *data structures*, and *APIs* that manipulate those data structures.
2. When you want to store those data structures, you express them in terms of general-purpose data model, such as Json, XML documents, Database, or a graph model. 
3. The engineers, who built database software decided on a way of representing the Json/XML/Relational/graph data in terms of bytes in memory, on disk, or in a network. The representation may allow the data to be queries,searched,manipulated and processed in various ways.
4. On yet lower levels, hardware engineers figure out how to represent bytes in terms of electrical current, pulse of light, magnetic fields, and more.

In a complex application there may be more intermediary levels, such as APIs built upon APIs, but the basic idea is still the same: each layer hides the complexity of the layers below it by providing a clean data model.

- There are many kinds of data model, and every data model embodies assumptions about how it is going to be used.
- It can take a lot of effort to master just one data model.


### Relational Model Vs Document Model



