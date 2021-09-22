# Create Thread
In Java, threads can be created in two ways:
- By extending the Thread class.
- By implementing the Runnable interface.

### Q. How Threads are working behind the scene?
While creating the thread whether we create using Thread class or by using Runnable interface, we have to
override/implement the run() method. In this run method, we write our code which we have to execute on the
current thread.

When we call the start() method, internally jvm do some operating system calls to spawn a new thread and start
the thread by calling the run() method which start the execution of our code which we have written in the
run() method. Now jvm will manage our created thread.

### Lifecycle of the threads in Java

`New -> Runnable -> Running -> Terminated`

There are 4 states of a thread:
- **New**: When a new thread is created.
- **Runnable**: When the thread is ready to run.
- **Running**: When the thread is in running state i.e., CPU is executing the code.
- **Terminated**: When the thread is in dead state.

There is also 1 intermediate state called Waiting/Blocked state.
Thread enters this state when it required some extra resource, it can database connection or waiting for I/O etc.

### Creating thread by extending the Thread class:
Thread is an abstract class in Java which provides various methods related to Threads.
For ex: setName(), setPriority(), isAlive(), join(), getState() etc.
```java
class Thread1 extends Thread {

  @Override
  public void run() {
    System.out.println("Hello World from " + Thread.currentThread().getName());
  }
}
```

### Creating thread by implementing the Runnable interface:

This method is mostly preferred because we can only extend one class in Java. So if we extend Thread class
we cannot extend another class.

Runnable interface only provides the code that thread have to run. So we have to pass the instance of the class
which implement the Runnable interface to the constructor of the Thread class.
```java
class Thread2Runnable implements Runnable {

  @Override
  public void run() {
    System.out.println("Hello World from " + Thread.currentThread().getName());
  }
}

public class ThreadCreation {

    public static void main(String[] args) {
        Thread thread1 = new Thread1();
        thread1.start();

        Thread thread2 = new Thread(new Thread2Runnable());
        thread2.start();
    }
}
```

### Output
```bash
Hello World from Thread-0
Hello World from Thread-1
```