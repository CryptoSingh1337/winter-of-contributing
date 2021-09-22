# Threads

### Q. What is Thread?
Thread is basically a small unit of process which is derived from its parent.
These are generally lightweight and operating system can switch more fastly as compared to processes and
this switching between threads or processes is called context switching.
 
### Q. Why we need Threads?
When we need that our application must be multitasking then we can think of using multithreading
Suppose we have an application which runs on single thread i.e., UI and business logic will be processed on the
same thread. But what if this single thread stuck somewhere or taking a long time to process. During this whole
case, our application will be hanged and we humans don't like this things.
So using threads we can solve this problem like we can create a separate thread for the application UI and other
thread for business logic (fetching large amount of data from the database) and processing it.

Properties of Threads:
- They have their own local stack in which all the local variables are stored.
- They shared a memory space which is common to all the threads called Heap.
- We can create thousands of threads (depends on the OS, hardware etc.) to divide the whole program to do the
complete the job.
 
Problems with Threads:
- Threads can save you application from the hell and it can also produce some weird behaviour.
- They can fall in the race condition.
- They can be trapped in Deadlocks.
- The multi-threaded code is generally difficult to test and debug and can be complex also.
 
Java provides extensive support for multithreading.

Thread class belongs to the java.lang package which is imported by default i.e., why we don't write the import
statement.


### Example:
```java
public class Threads {

    public static void main(String[] args) {
        Thread t = new Thread() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName());
            }
        };

        t.start(); // calling the thread to start
    }
}
```
### Output:
```bash 
Thread - 0
```