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
