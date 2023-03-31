---
title: "Threads in java"
datePublished: Thu Mar 30 2023 17:43:28 GMT+0000 (Coordinated Universal Time)
cuid: clfvemqyt000709lbbwbe1h00
slug: threads-in-java
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/cckf4TsHAuw/upload/29ce9affd7a6aed238212165789fc4e3.jpeg

---

Java is a popular programming language that supports multithreading. A thread is a lightweight sub-process that can run simultaneously with other threads. In Java, threads are implemented using the java. lang.Thread class.

Java threads are used to improve the performance of applications that require concurrent processing. By dividing a task into smaller sub-tasks that can be executed in parallel, a program can complete the task more quickly than if it were executed sequentially.

Creating and Running Threads in Java

In Java, a thread can be created and run in two ways: by extending the Thread class or by implementing the Runnable interface.

1. Extending the Thread class:
    

To create a thread by extending the Thread class, you need to create a new class that extends Thread and override the run() method. The run() method is where you put the code that you want the thread to execute.

Here's an example:

```java
arduinoCopy codeclass MyThread extends Thread {
    public void run() {
        System.out.println("MyThread is running");
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start();
    }
}
```

In this example, we create a new class called MyThread that extends Thread. We override the run() method to print a message to the console. In the main method, we create a new instance of the MyThread class and call the start() method to start the thread.

1. Implementing the Runnable interface:
    

To create a thread by implementing the Runnable interface, you need to create a new class that implements Runnable and override the run() method. The run() method is where you put the code that you want the thread to execute.

Here's an example:

```java
typescriptCopy codeclass MyRunnable implements Runnable {
    public void run() {
        System.out.println("MyRunnable is running");
    }
}

public class Main {
    public static void main(String[] args) {
        MyRunnable runnable = new MyRunnable();
        Thread thread = new Thread(runnable);
        thread.start();
    }
}
```

In this example, we create a new class called MyRunnable that implements the Runnable interface. We override the run() method to print a message to the console. In the main method, we create a new instance of the MyRunnable class and pass it to the Thread constructor. We then call the start() method to start the thread.

Thread States in Java

In Java, threads have different states that represent their current status. The states are:

* New: A thread is in the new state when it has been created but has not yet started.
    
* Runnable: A thread is in the runnable state when it is ready to run, but the JVM has not yet scheduled it to run.
    
* Running: A thread is in the running state when it is currently executing.
    
* Blocked: A thread is in the blocked state when it is waiting for a monitor lock to be released.
    
* Waiting: A thread is in the waiting state when it is waiting for another thread to perform a specific action.
    
* Timed Waiting: A thread is in the timed waiting state when it is waiting for another thread to perform a specific action for a specified amount of time.
    
* Terminated: A thread is in the terminated state when it has completed its execution.
    

Thread Synchronization in Java

In Java, threads can access shared resources concurrently. This can lead to race conditions, where two or more threads try to access the same resource at the same time, resulting in unpredictable behavior.

To prevent race conditions, Java provides mechanisms for thread synchronization. Synchronization ensures that only one thread can access a shared resource at a time.

Java provides two ways to synchronize threads: synchronized methods and synchronized blocks ..

1. Synchronized Methods:
    

In Java, you can make a method synchronized by adding the synchronized keyword to its signature. A synchronized method ensures that only one thread can execute the method at a time.

Here's an example:

```java
csharpCopy codeclass Counter {
    private int count = 0;

    public synchronized void increment() {
        count++;
    }

    public synchronized int getCount() {
        return count;
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();

        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        });

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println(counter.getCount()); // Output: 2000
    }
}
```

In this example, we create a Counter class with a synchronized increment() method and a synchronized getCount() method. We then create two threads that call the increment() method on the same Counter object. We use the join() method to wait for both threads to complete before printing the final count.

1. Synchronized Blocks:
    

In addition to synchronized methods, Java also provides synchronized blocks. A synchronized block is a block of code that is executed atomically by a single thread.

Here's an example:

```java
csharpCopy codeclass Counter {
    private int count = 0;
    private Object lock = new Object();

    public void increment() {
        synchronized(lock) {
            count++;
        }
    }

    public int getCount() {
        synchronized(lock) {
            return count;
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Counter counter = new Counter();

        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                counter.increment();
            }
        });

        t1.start();
        t2.start();

        try {
            t1.join();
            t2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println(counter.getCount()); // Output: 2000
    }
}
```

In this example, we create a Counter class with a private lock object. We then use synchronized blocks to ensure that only one thread can access the count variable at a time.

Conclusion:

Java threads are a powerful tool for concurrent programming. They allow you to execute multiple tasks simultaneously, which can improve the performance of your applications. However, threading can be complex and error-prone, especially when dealing with shared resources. It's important to use synchronization mechanisms to ensure that your threads are executing correctly and safely.