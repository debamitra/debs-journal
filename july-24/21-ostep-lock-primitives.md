Read the remaining pages of Chapter 28 - LOCKS

Learned a bunch of h/w primitives for locking and about spin locks.

But spinlocks continuouly uses up CPU. Can we build a lock that doesn’t waste cpu cycles spinning needlessly?

**yield()** is an operating system primitive that a thread can call when it wants to give up the CPU and let another thread run. Its basically a system call that un-schedules the calling thread and puts the thread's state from running into ready

Does not prevent starvation and also, the context switches is still inefficient for say if there are 99 other threads.



##### Questions 
1. How does CPU scheduling work in the context of threads and processes? How are they represented and how are they scheduled? Is a process considered as the main thread of execution and scheduled as a thread? How does this work now?

