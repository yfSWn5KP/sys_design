---
recall: header
---

### What is Data Partitioning?

Partitioning splits a single, vertical database resource (table and/or server) into multiple resources.
 
This provides better performance, availability, and balancing.


### What are 3 types of Data Partitioning?

1) Horizontal
1) Vertical
1) Directory


### How does **Horizontal** Data Partitioning work?

* Horizontal Partitioning is also known as
  * Range-based
  * Sharding
* Resources are split across ranges
  * e.g. letters A-E, etc.


### What is one downside/con with **Horizontal** Data Partitioning?

* Con: can easily become unbalanced
  * Careful choice of range can help alleviate this


### How does **Vertical** Data Partitioning work?

* Vertical Partitioning splits resources based on their functional use
  * e.g. use separate resources for user_info, user_photos, etc.


### What are the Pros:Cons of **Vertical** Data Partitioning?

* Pro: straightforward implementation
* Con: as the app grows, it may become necessary to "partition the partitions"
  * i.e. the original partitions may bloat


### How does **Directory** Data Partitioning work?

* Abstract the database partition away from the application
* Create a Directory Service
* The app provides the partitioning tuple, and the D.S. responds with the partition's location


### What are the Pros:Cons of **Directory** Data Partitioning?

* Pro: partitioning can evolve without refactoring the app
* Con: the D.S. is a potential bottleneck/point-of-failure


### What are 4 Partitioning Schemes/Methods?

1) Hash-based
1) Round-Robin
1) List/Enum-based
1) Composite


### How does **Hash-based** Partitioning work?

* Convert the Partition Tuple to a `part_int` and derive its `partition_id`
  * `partition_id` == `part_int` % `num_partitions`


### What are the Pros:Cons of **Hash-based** Data Partitioning?

* Pro:
  * Uniformly balanced, [assuming even distribution](https://en.wikipedia.org/wiki/SUHA_(computer_science))
  * Deterministic Partitioning
* Con:
  * `num_partitions` is fixed
    * Downtime is required to modify `num_partitions`
    * Consistent Hashing can remedy this problem
  * Must specify the Tuple in advance


### How does **Round-Robin** Partitioning work?

* Circularly iterate through each partition when writing data
* This can be implemented using an `incremental_id`
  * `partition_id` == `incremental_id` % `num_partitions`


### What are the Pros:Cons of **Round-Robin** Data Partitioning?

* Pro:
  * No key required for hashing
* Con:
  * Non-Deterministic Partitioning


### What is the Read-difference between Round-Robin and Hash-based Partitioning?

* Hash-based Partitions are deterministic in that a given key/tuple always points to the same partition
  * This speeds up reads because only *1 partition* is queried
* Round-Robin Partitions are non-deterministic
  * This slows down reads because *all partitions* must be queried


### What is the Write-difference between Round-Robin and Hash-based Partitioning?

* Hash-based Partitions require the specification of a key tuple
* Round-Robin Partitions require no config


### How does List/Enum-based Partitioning work?

* Assign each partition a list of values it is responsible for
* Lookup the relevant partition via enum_key


### How does Composite Partitioning work?

* "Create your own" scheme by combining other schemes
* e.g. do a list-based lookup followed by a round-robin lookup


### What are 3 Problems with Partitioning?

1) Joins
2) Referential Integrity
3) Rebalancing


### What is the problem with Joins when Partitioning?

* Joins are impractical because it would require compiling multiple query results
* This is commonly addressed by Denormalizing the relevant data
  * However, Denormalization now introduces the problem of Consistency, i.e. keeping duplicated data in-sync


### What is the problem with Referential integrity when Partitioning?

* Most RDBMS do not support foreign keys when using partitions
* The result is that relational integrity must be maintained by the application


### What is the problem with Rebalancing when Partitioning?

* Rebalancing occurs when the need arises to modify our partitioning scheme, potentially due to:
  * Bloating data on a partition(s)
  * Non-uniform range, list, etc.
* The result is moving data between partitions and/or creating new partitions
  * Zero-downtime rebalancing is difficult
* Directory-based partitioning makes this problem slightly easier, but it does introduce complexity & act as a bottleneck
