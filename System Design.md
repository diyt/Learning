# System Design

### [Consistent Hashing](https://www.acodersjourney.com/system-design-interview-consistent-hashing/)(Load Balancer)
  - Use a hash function to map servers to a ring (Use a SortedMap data structure to implement the ring)
  - Hash the same server multiple times to avoid skewed distribution
  - Use the same hash function on the incoming request and find the first vertual node on the ring clockwise
  - Adding/Removing a server just need to add/remove the vertual nodes for that server on the ring
  
### Cache
  - [Cache techniques](https://www.computerweekly.com/feature/Write-through-write-around-write-back-Cache-explained)
    - write-through(write to cache-DB, write then read frequently)
    - write-around(write to DB, result in cache miss)
    - write-back(write to cache and complete)
  - [Cache locations](https://dzone.com/articles/process-caching-vs-distributed):
    - Local Cache: Fast, Inconsistent issue, cache take app host resoureces and cannot scale independently
    - Distributed Cache: Slower(network latency and object serialization), Consistent, Can scale independently

### TinyURL
  - Optimal solution: request -> LB -> App Servers each with own counter, managed by ZooKeeper -> DB(perfer NoSQL). Add cache to optimize performance.
  - Basic calculate:
    - Write traffic: 40TPS -> 100M TPM, Size: 2KB per entry, Total: 200GB per month -> 2.4TB per year
  - SQL or NoSQL: high throughput, no complex schema requirement, no update -  prefer NoSQL
  - 1. Generate a random number and **base62**(randomNumber) to construct the key. Put key-longURL-createDate-ExpireDate in the DB
    - Need to check the newly generated key to see if it already exist or not. If exist, need to generate a new key
    - When checking whether the random nubmer exists in DB, there might be race condition when there are multiple workers
  - 2. **MD5**(longURL) and take the first 7 characters to be the shortURL
    - Will generate same shortURL for different long URLs. Need to check existence before insert to DB
  - 3. **Counter based approach(best)**: Maintain a counter and do base62(counter) to generate the shortURL
    - Guarantee no duplicate because the counter values will always be different
    - Problems: Counter can become SPOF. Multiple servers in different regions cannot easily communicate to the same counter. Maintain multiple counters of different ranges are hard, what if counters run out of range, etc.
    - Solution: Use Zookeepter to manage multiple application servers, each has their own counter of different ranges. ZooKeeper is responsible for monitoring active nodes and assign counters to them. If add a new server or the counter ran out of range, ZooKeeper will assign a new counter range to it.
  
