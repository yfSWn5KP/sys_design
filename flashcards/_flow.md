---
recall: header
---

### SysDesign Flow: What are the 7 Steps?

**Requirements**, **Envelope**, the **API**, to **DefineDataModels**, and **Sketch**, the **DeepDive**, for **Bottlenecks**.
 
1) Requirements Gathering
1) Back of the Envelope Measurements
1) System Interface (API Functions, etc.)
1) Define the Data Models
1) Sketch a High-Level Diagram
1) Dive Deep on a Couple Items
1) Prevent Bottlenecks/Single-Points-of-Failure via redundancy, etc.

### SysDesign Flow: What is the Goal of #1 Requirements Gathering?

Enumerate supported features.

### SysDesign Flow: What are some considerations for #2 Back of the Envelope Measurements?

- Quantity of Units
- Storage Requirements
- Network Latency

### SysDesign Flow: What is the Goal of #3 System Interface?

* Break into modular pieces/components
* Define function-signature for each component

### SysDesign Flow: What are some considerations for #4 Define the Data Models?

You want to develop a datastore system that supports both functional and non-functional requirements.
 
**Engines**, **Authorize**, **Rate Limits**, of the **Encrypted**, **Schema**, for **Data Flow**, through the **Partitions**
 
- Discuss different storage engines
- Define the schema
- Detecting and preventing abuse, e.g. rate limits
- What will need to be encrypted?
- How will the data flow through?
- How will it be partitioned?
- How will authorization work?

### SysDesign Flow: What are some considerations for #6 Dive Deep on a Couple Items?

This is about ensuring that the system operates efficiently.
 
- Propose to the interviewer the parts you'd like to discuss
- Examples
  - Read/Write replications
  - "hot"/P99 user scalability
  - Data storage optimization for query sorts/filters
  - Caching strategy
  - Balancing load

### SysDesign Flow: What are some considerations for #7 Prevent Bottlenecks/Single-Points-of-Failure?

This is about ensuring that the system remains healthy.
 
- Identify & resolve single points of failure
- Replication to avoid data loss
- Redundancy to avoid computational/service outage
- Monitor/alert for observability
