---
recall: header
---

### What are the 5 Characteristics of a Distributed System?
S.M.E.A.R.
 
1) Scalable
1) Maintainable
1) Efficient
1) Available
1) Reliable


### What are the 2 types of Scalability?

1) Horizontal Scalability, e.g. NoSQL
1) Vertical Scalability, e.g. SQL


### What is 'Reliability' of a Distributed System?

A reliable system continues delivering service even if one or multiple of its components (software or hardware) fail.


### What is 'Availability' of a Distributed System?

Availability is a measure of how long a system is able to deliver service against the full range of possible real-world conditions that can occur.
 
It considers logistics such as maintainability, repair time, & spares.
 
It is measured in terms of % over time, e.g. [five 9s of availability](https://en.wikipedia.org/wiki/High_availability#Percentage_calculation).


### What is the difference between 'Reliability' & 'Availability' of a Distributed System?

If a system is reliable then it is available, but an available system may *not* be reliable.
 
Availability is an empirical measure that may not capture the full range of future possibility.
 
For example, a system may have been highly available over the past 2 years, but it may actually have low reliability due to a security vulnerability that is exploited in year 3.


### How do you measure the 'Efficiency' of a Distributed System?

Efficiency is measured in terms of "unit costs," for example:
 
* Throughput in Number of units
* Latency in Seconds to transmit each unit
* Storage in Size of each unit


### What considerations are important for 'Maintainability' of a Distributed System?

* Detectability of degradation, e.g. PagerDuty alerting on error metrics.
* Diagnose-ability: how difficult is it to introspect, debug, & fix?
* Update-ability: how difficult is it to Modify or Upgrade?
