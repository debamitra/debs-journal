Read about TestAndSet and SpinLocks today. Not a lot but its something.

TestAndSet and CompareAndSwap are two hardware primitives that support atomic locking.

**Spinlock** is a simple locking mechanism that works by calling one of the primitives above and based on it acquires a lock, then continues to spin in a while loop while lock is held. Otherwise moves into critical section after acquiring the lock.

Remaining concepts to read and understand tomorrw -
- [ ] Load-Linked and Store-Conditional

- [ ] Test and Set then Yield

- [ ] Lock with Queues

- [ ] Futex

- [ ] Two phase locks


- [ ] Review Spinlocks
  
