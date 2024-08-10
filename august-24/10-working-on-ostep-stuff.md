### OSTEP - Chapter 29

Finished learning about concurrent hash tables. Its implementation is quite simple , basically an array of concurrent lists where each item is a list and is called a bucket. A lock is used per bucket, so it scales really well and is super fast.

Interestingly Linux initially used a very simple concurrency model for its kernel code ,where it applied one single lock on its data structures (entire data structure). Later on to utilize multiproccesors, it was further optimized  by replaceing one lock with many. Solaris built a completely new OS with concurrency build in to the design.

- [ ] Looking into implementing  B-tree with simple locking strategy like a single lock. Will measure its performance as the number of concurrent threads increases. (ostep homework)
- [ ] Then will follow up with implementing a more interesting locking strategy for B-Tree and measure its performance, comparing it to previous single locking strategy. (more ostep homework..)

- Found this [video](https://www.youtube.com/watch?v=pH-WsPCZWC8) to watch, to understand B-tree indexes basics.
- Reading this [paper](https://15721.courses.cs.cmu.edu/spring2016/papers/a16-graefe.pdf) on different locking strategies on B-trees , about halfway through, will continue tomorrow  


### C Libraries - Source files

I have been writing small c programs and running them in VSCode for a while. I use gcc to compile them and then run them from the terminal. Now I want to read code for the library files that gcc is using. How do I find out where the source files are?

The apple open source website has them [here](https://opensource.apple.com/releases/)

I downloaded *libpthread* library as I wanted to check the code for the mutex lock and unlock methods from pthread.h.
