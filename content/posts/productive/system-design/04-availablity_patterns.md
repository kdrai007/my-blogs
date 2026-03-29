---
title: "04-availablity_patterns"
draft: false
---

Tags: #system-design #AP

# Availability Patterns

Availability is measured as a percentage of uptime,and defines the propertion of time that a system is functional and working. 

* AP help design systems that remain operational even if there's failover, Here are some patterns:-

- Failover - Switch to standby system when primary system fails
- Replication  - Maintain multiple copies of data in case of failure or any unexpected loss of data.
- Load balancing
- Auto-scaling
- Circuit breaker - Prevent Cascading failtures by stoping calls to failing services.
- Chaos engineering - Intentionally introduce failures to check if everything working correctly

## Availability in numbers

Availability is often quantified by uptime (or downtime) as a percentage of time the service is available.  

- Availability is generally measures in numbers of `9s`  
- A service have `99.99%` availability is described as haveing fours 9s.

**99.99% Availability - Four 9s**

```markdown 

Duration           | Acceptable downtime
-------------      | -------------
Downtime per year  | 52min 9.8s
Downtime per month | 4m 21s
Downtime per week  | 1m 0.5s
Downtime per day   | 8.6s

```

### Availability in parallel vs in sequence

The service consists of multiple components prone to failure, A system overall availability depends on whether the components are in sequence or in parallel.

#### In Sequence

Overall availability  decreases when two components with availability < 100% are in sequence

```txt
Availability(total)= availability(foo) * availability(bar)
```

If both `foo` and `bar` avaiability is `99.9%` there total availability will be `99.8%` in sequence.

#### In Parallel(Redundent Systems)

Overall availability increases when two components with availability < 100% are in parallel.

```txt
Availability(total) = 1- ( 1- availability(foo)) * ( 1-availability(bar))
```

**Sequence** -> Decreases availability due to dependence.
**Parallel** -> Increases availability due to redudency.













