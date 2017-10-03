# multithreading


#sem_init

The sem_init() function is used to initialise the unnamed semaphore referred to by sem. The value of the initialised semaphore is value. Following a successful call to sem_init(), the semaphore may be used in subsequent calls to sem_wait(), sem_trywait(), sem_post(), and sem_destroy(). This semaphore remains usable until the semaphore is destroyed. 

If the pshared argument has a non-zero value, then the semaphore is shared between processes; in this case, any process that can access the semaphore sem can use sem for performing sem_wait(), sem_trywait(), sem_post(), and sem_destroy() operations.

Only sem itself may be used for performing synchronisation. The result of referring to copies of sem in calls to sem_wait(), sem_trywait(), sem_post(), and sem_destroy(), is undefined.

If the pshared argument is zero, then the semaphore is shared between threads of the process; any thread in this process can use sem for performing sem_wait(), sem_trywait(), sem_post(), and sem_destroy() operations. The use of the semaphore by threads other than those created in the same process is undefined. 

# sem_wait

sem_wait() decrements (locks) the semaphore pointed to by sem.  If
the semaphore's value is greater than zero, then the decrement
proceeds, and the function returns, immediately.  If the semaphore
currently has the value zero, then the call blocks until either it
becomes possible to perform the decrement (i.e., the semaphore value
rises above zero), or a signal handler interrupts the call.

sem_trywait() is the same as sem_wait(), except that if the decrement
cannot be immediately performed, then call returns an error (errno
set to EAGAIN) instead of blocking.

# sem_post

sem_post() increments (unlocks) the semaphore pointed to by sem.  If
the semaphore's value consequently becomes greater than zero, then
another process or thread blocked in a sem_wait(3) call will be woken
up and proceed to lock the semaphore.
