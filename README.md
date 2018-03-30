## Threads and Synchronization

This lab illustrates the problem of synchronization when many threads are operating on a shared object.  The general issue is called "thread safety", and it is a major cause of errors in computer software.

## Assignment

To the problems on the lab sheet and record your answers here.

1. Record average run times.
2. Write your explanation of the results.  Use good English and proper grammar.  Also use good Markdown formatting.

## ThreadCount run times

These are the average runtime using 3 or more runs of the application.
The Counter class is the object being shared by the threads.
The threads use the counter to add and subtract values.

| Counter class           | Limit              | Runtime (sec)   |
|:------------------------|:-------------------|-----------------|
| Unsynchronized counter  |    10,000,000      |    0.015595     |
| Using ReentrantLock     |    10,000,000      |    0.762716     |
| Syncronized method      |    10,000,000      |    0.020533     |
| AtomicLong for total    |    10,000,000      |    0.306789     |

## 1. Using unsynchronized counter object

answer the questions (1.1 - 1.3)

1.1 Total should be zero , Total isn't be the same value.                                                                                                                              
1.2 0.015595                                                                                                                                                                                                                                      
1.3 Two of the threads has use the same value of limit and same counter , therefore sometimes when the addtask or subtask finishing working maybe the count value that came in the method is wrong value and the task will return the wrong value too.

## 2. Implications for Multi-threaded Applications

How might this affect real applications?  
`ANS` : The balance value will be wrong. Suppose that you are depositing then someone transfer money to you account and the threads working at the same time! It will happen like this program. 

## 3. Counter with ReentrantLock

answer questions 3.1 - 3.4

3.1 Total always be zero.                                                                                             
3.2/3.3 The result always be zero because, Reentrantlock lock the total for avoiding subTask and addTask work at the same time. Therefore ReentrantLock will lock subtask when addtask is working this is why run time is more than Unsynchronized Counter.                                                                             
3.4 we have unlock code in finally block, to make sure it run even if try block throws exception or not.

## 4. Counter with synchronized method

4.1 It always be zero.                                                                                                 
4.2 When the previous thread is executing a synchronized method is block the other thread.                                                                         
4.3 Synchronized methods enable a simple strategy for preventing thread interference and memory consistency errors.

## 5. Counter with AtomicLong
5.1 Java provides AtomicLong which can be used without any synchronization.                                                                          
5.2 you would use AtomicLong when you have guarantee that the value can be used in concurrent environment and don't need the wrapper class. Using AtomicLong because Long does not allow for thread interoperability.

## 6. Analysis of Results

6.1 Unsynchronized counter is the fastest, Using ReentrantLock is the slowest.                                                                                         
6.2 I think the best solution can be applied to the broadest range of problems is using AtomicCounter because it will work completely by itself without any synchronization.

## 7. Using Many Threads (optional)

