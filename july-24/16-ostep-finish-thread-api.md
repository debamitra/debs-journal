
**Condition variables** These are used when one thread may be waiting for another to complete before it can do some task or continue. In this case some kind of signaling is needed.

int pthread_cond_wait(pthread_cond_t *cond, pthread_mutex_t *mutex);
int pthread_cond_signal)pthread_cond_t);

Thread 1 acquires mutex lock
Thread 1 waits on a condition variable (releases the lock and goes to sleep)

Thread 2 acquires mutex lock
// does stuff
Thread 2 signals condition variable (this wakes up the Thread waiting on it)
Release lock

1. I dont understand why signaling the waiting thread has to be done before releasing the mutex/lock. What happens if its after? Anyway the waiting thread depends on the condition variable to change to wake up and reacquire lock. Lets say it releases the lock. Would the waiting thread be effected? unless its signaled it wont right?

Sample Code 
```c
pthread_mutex_lock(&lock);  // Acquire the mutex

while (ready == 0) {
    pthread_cond_wait(&cond, &lock);  // Wait for the condition to be signaled
    // Automatically releases the mutex and puts Thread A to sleep
    // Automatically reacquires the mutex when woken up
}

// Proceed with the critical section
printf("Thread A: Condition met, continuing...\n");

pthread_mutex_unlock(&lock);  // Unlock the mutex

///////

pthread_mutex_lock(&lock); 
ready = 1;  // Modify the condition variable
pthread_mutex_unlock(&lock); 
pthread_cond_signal(&cond);

```
Thread A - acquires mutex, checks ready
ready == 0 is true, prepares to call pthread_cond_wait
releases mutex, not yet started fully waiting on the condition variable

Meanwhile
Thread B - acquires mutex
Sets ready = 1 and releases mutex
Signals the condition variable 

Thread A may not have started fully waiting yet so it misses the signal


To fix this ,
Signalling by Thread B must be done before releasing the mutex

How does this fix the issue?
Since condition is shared data  that one thread waits on and another signals , so it needs to be only accessed by one thread at a time.



