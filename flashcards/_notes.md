---
recall: header
---

### What is one thing that knowing "units per second" informs?

Units per second allows you to back into the bandwidth calculation of size/second in/out


### How does the length of a string correlate to the base of the encoding scheme?
For example, a string with 10 characters, which is encoded in base64, has how many possible values?
 
`base_n` <sup>`string_len`</sup> == `num_values`
 
e.g. 64<sup>10</sup> == `num_values`


### What are Functional vs. Non-Functional Requirements?

A functional requirement describes *what* the service/product does, e.g. "the URL shortener should redirect users to the target link."
 
A non-functional requirement describes *how* the service behaves, e.g. "the URL shortener should be highly available so that redirects never fail."


### What is Service Oriented Architecture (SOA) a synonym of?

SOA is a synonym for Microservices Architecture.


### What is N-Tier Architecture?

Also referred to as Multi-Tier Architecture, this is a design pattern where physical resources are "stacked," and each tier only communicates with its immediate neighbor.
 
(Note that a `tier` strictly refers to a physical, infra resource; whereas a `layer` is an intangible, logical resource)
 
It is typically implemented as 3 Tiers:
 
1) Presentation UI Tier
  e.g. web client
1) Application Logic Tier
  e.g. application server
1) Data Tier
  e.g. database server
 
The Application Server acts as a middleman between the Client and the Database.
