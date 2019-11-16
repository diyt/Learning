# System Design

## [Consistent Hashing](https://www.acodersjourney.com/system-design-interview-consistent-hashing/)(Load Balancer)
  - Use a hash function to map servers to a ring (Use a SortedMap data structure to implement the ring)
  - Hash the same server multiple times to avoid skewed distribution
  - Use the same hash function on the incoming request and find the first vertual node on the ring clockwise
  - Adding/Removing a server just need to add/remove the vertual nodes for that server on the ring
