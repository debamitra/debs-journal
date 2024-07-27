Went through these two articles - [Hardware Memory Models](https://research.swtch.com/hwmm) and [Programming Language Memory Models](https://research.swtch.com/plmm)

Some stuff I understood:
- Compiler optimizations causing re-ordering of code or caching of register contents - caused complications in multi-threaded environments as valid outcome guarantee didnt hold anymore like they did in Single threaded memory model.
- *solutions* - memory models using total store order concept (queues to manage ordering) (x86) or coherence (ARM) 
- *more solutions* - synchronization operations and barriers (data-race-free and sequential ordering model)


#### OSTEP..
##### Futexes
A futex is associated with a specific physical memory location and a per-futex in-kernel queue.

Its a synchronization primitive used in linux. It uses a hybrid approach of one spin first to check if a lock can be held and then puts thread to sleep to wait until lock is available.
Its optimized to use a single integer variable to hold status of lock as well as all the waiters , who are waiting on the lock.
