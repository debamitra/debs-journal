
### Basic concepts learned today (Chapter 25)
1. **Threads** - multiple points of execution within a process. They share the process' address space but have their own stack.
   
2. **Why threads?**
   - for parallelism, so that an activity can be broken up and executed parallely to finish faster (relevant in systems with mutiple cpus)
   - to avoid blocking a program's progress due to slow I/O ( other threads of activity can run while one is waiting for I/O)
  
3. **Problem** - race condidtions can be created because threads can access and modify shared data . Why? Because of scheduling, threads can be switched at any time.

#### Race condition example
Lets say we want to update a shared memory location with two threads, each thread will increment the data by 1.

Updating is not atomic, it involves 3 instructions -
  1. Read the value from memory into a register (e.g., EAX). 
  2. Increment the value.
  3. Write the updated value back to memory.
After any instruction, context switch can happen inbetween an update.
Here one possible flow of execution:
  - Thread 1 starts updating:
    - Reads the memory value(lets say 50) into EAX.
    - Increments EAX by 1.
  - Context Switch occurs before Thread 1 can write back to memory.(Stores register values etc into context and switches to Thread 2 context)
  - Thread 2 Starts
    - Reads the (old) memory value(50) into its EAX
    - Increments its EAX by 1.
    - Writes the updated value back to memory. (51)
  - Thread 1 Resumes:
    - Continues from where it left off.
    - Writes its EAX value (incremented earlier) back to memory. (51)
   
Even though both Thread 1 and Thread 2 increment the memory value of 50, instead of 52, we still see it as 51.

4. **Critical Section** - becasue multiple threads running a piece of code can cause race condition, this code is called critical section. Critical section code should not be executed by more than 1 thread at a time. (Prevents context switches inbetween)

5. **Mutual Exclusion** is a property that guarentees that if one thread is running in critical section, no other thread should be able to run in it. This makes the critical section atomic.

6. How to solve - synchronization primitives to support atomicty

7. Another problem for threads - One thread may be waiting for another thread  to complete before it can continue. E.g a thread goes to sleep while waiting for I/O to complete, and when I/O is completed, the thread needs to be woken up again
