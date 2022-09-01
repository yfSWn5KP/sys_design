---
recall: header
---

### What is Redundancy?

Redundancy duplicates a critical resource/operation to provide better reliability and/or performance.


### What are 4 types of Redundancy?

1) Hardware Redundancy
1) Information Redundancy
   1) e.g. error detection & correction methods
1) Time Redundancy
   1) perform the same operation multiple times
1) Software Redundancy
   1) e.g. N-versions of a program, developed independently from the same spec


### What is Replication?

Replication creates multiple, consistent copies of data to increase reliability, performance, fault-tolerance, & accessibility.


### What is Fault Tolerance?

Also called "Graceful Degradation," this provides guarantees such that the service remains operational even if one or multiple components fail.


### What % Availability should Fault Tolerance provide?

100% [citation](https://en.wikipedia.org/wiki/High_availability_software)


### What is Active vs. Passive Replication?

1) Active
   1) Each replica computes the result
1) Passive
   1) A single node computes the result and then broadcasts the result to the replicas


### What is Primary Master Replication?

a.k.a. "Master:Slave"
 
The node elected as master handles all input and broadcasts it to the replicas.
 
This is common in High-Availability Clusters.


### What is a High-Availability Cluster?

a.k.a. "Master:Master"
 
It is highly available because the *failover* process detects service degradation and restarts via a new instance to maintain availability.


### What % Availability should High-Availability provide?

99.999% (five 9s) [citation](https://en.wikipedia.org/wiki/High_availability_software)


### What are the 4 Prerequisites for High-Availability?

1) Controllable Health, via commands to:
   1) Check Health
   1) Start
   1) Stop
   1) Force Stop
1) Uses Shared Storage, e.g. NAS
1) Retains State on Non-Volatile Storage, accessible to a new instance
1) Incorruptible Data, e.g. during power loss
