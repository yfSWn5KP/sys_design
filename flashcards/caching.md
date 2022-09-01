---
recall: header
---

### What is the 'Locality of Reference Principle'?

Recently requested data is likely to be requested again.


### What are the 2 types of caching strategies?

1) Global, e.g. a single, master NGINX
1) Distributed, i.e. a CDN


### When should a Global Cache be used instead of a CDN?

* If the app is small, consider starting with a Global Cache that can be easily migrated to a CDN:
  * Serve static content from a simple NGINX config at `static.app.com`
  * When/if the app requires a CDN, simply cut the DNS over to it


### How do CDNs work?

* Each node maintains its own cache
* When content is requested, the node serves directly from the cache if available
* If the content is not yet cached, the node will request it from the back-end servers, cache the result, and return it to the client
* CDNs rely on having strategies for Invalidation & Eviction


### What is Caching Invalidation?

Invalidation strategies allow for the app to mark content as stale, requiring a refresh


### What are 3 Cache Invalidation/Writing Strategies?

1) Write-through
1) Write-around
1) Write-back


### How does Write-**through** Cache Invalidation Work?

* Data is written to both the database and the cache at the same time, with atomicity
* Pro: for read-intensive apps
  * Consistency guaranteed between the db and the cache
* Con: high-latency on the initial write


### How does Write-**around** Cache Invalidation Work?

* Data is written to the database and marked as invalid within the cache
* Pro: for infrequent-read apps
  * Can avoid unnecessary writes, since the write occurs later on the next read request
* Con: high-latency on the next read 


### How does Write-**back** Cache Invalidation Work?

* Data is written only to the cache; the database write happens later, asynchronously
* Pro: for write-intensive apps
  * Has low-latency *and* high-throughput
* Con: risk of data loss when the cache dies prematurely



### What is Caching Eviction?

Eviction strategies allow for the cache to clear memory


### What are 6 Cache Eviction Strategies?

First, Recent, Frequent, Random:
 
1) FIFO - First in First Out
1) LIFO - Last in First Out
1) LRU  - Least Recently Used
1) MRU  - Most Recently Used
1) LFU  - Least Frequently Used (min-heap request count)
1) RR   - Random Replacement


### What implementation/data-structure can be used to implement an LRU Cache?

A `Linked Hash Map` provides `O(1)` lookup with the ability to re-order keys, e.g. `map.move_to_end(key)`
