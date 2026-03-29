---
title: "05-background-jobs"
draft: false
---

Tags: #system-design #background-jobs #bj

# Background jobs

Background jobs in system refers to the jobs that are being executed in background, Independently of the main execution flow of the system. These tasks are initiated by system itself, rather than the user or another external agent.

Background jobs can be used for variety of purposes like:- 

- Performing maintenance tasks: such as cleaning old data, generating reports, or backing up to the database.
- Processing large amount of data: such as, data import, data export or data transformation
- Sending notifications: sending push messages to users, or sending emails
- Performing long-running computations: like machine learning or data analysis.

Types of background jobs:-

1. Event driven
2. Schedule driven

## Event driven

Event driven tasks are intitiated by triggering  an event, examples :- 

- A Ui or another job places message in a queue. The message contains data about an action that has taken place, such as the user subscribe for pro plan. The background task listen for queue and detacts arrival of new message. It reads the messages and uses the data as an input to the background jobs. This pattern is known as asynchronous message-based communication.  
- A Ui or any another jobs saves or updates the a value in storage. The background jobs inspect or read the message and use it as the input in the background job.  
- A UI or another job make request to an endpoint, such as an API URIs, or an API exposed as a web service. It passes the data that is required to complete the backgrond jobs as part of the request. The endpoint or webservice invokes the background task, which uses the data as its input. 

## Schedule driven

Schedule driven invocation uses a timer to start the background task. example,

- A timer that is running locally within the application or as a part of the application's operating system invokes a background task on a regular basis.
- A timer that is running in a differnt application, such as Azure logic Apps, sends a requests to API or webservice on a regular basis . The Api or web-service invokes the background task. 
- A seperate process or timer is causes to invoke application's background task once after specific time deley, or at a specific time.

Typical example of schedule driven  background jobs include batch processing routines(such as updating product list for users based on their recent behaviour). 



