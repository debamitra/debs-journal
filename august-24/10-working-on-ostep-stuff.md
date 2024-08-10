### OSTEP - Chapter 29

Finish learning about concurrent hash tables. Its implementation is quite simple , basically an array of concurrent lists where each item is a list and is called a bucket. A lock is used per bucket, so it scales really well and is super fast.

Interestingly Linux initially used a very simple concurrency model for its kernel code ,where it applied one single lock on its data structures (entire data structure). Later on to utilize multiproccesors, it was further optimized  by replaceing one lock with many. Solaris built a completely new OS with concurrency build in to the design.

- Looking into implementing  B-tree with simple locking strategy like a single lock. Willeasure its performance asthe number of concurrent threads increases.
- Then will follow up with implementing a more interesting locking strategy for B-Tree and measure its performance, comparing it to previous single locking strategy.
