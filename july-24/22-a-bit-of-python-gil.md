#### Python and GIL

I have been trying to wrap my head about locking primitives at the hardware and OS level. Basically learning about  how spinlocks work using atomic operations like compareAndSwap or testAndSet to secure critical sections. And using queuing strategy to optimize for less cpu cycles wastage.

I watched a video about python GIL and summarized the below points :
1. In python, how do you utilize all cpu cores to get your programs to run/complete faster ie.parallel programming?
2. Three ways to deal with multitasking in python
    1. **Asyncio** - good for I/O bound tasks, if you have lot of requests simply waiting for I/O it allows other tasks to run in the meantime. (Single threaded)
    2. **Threads** - not much you can do with threads. Why? Python uses a GIL or lock around the entire interpreter. So only one thread can execute in the interpreter at a time. 
       - Note : In Python 3.12 we can disable GIL by setting PYTHON_GIL=0 , but I guess there are some overhead costs to ensure thread safety post that. Also it’s still being tested to make sure things don’t break. https://peps.python.org/pep-0703/
           
    3. **Multiprocessing** - for cpu/compute bound tasks which can be broken into sub tasks that can execute independently.
  
3. *To be continued*
