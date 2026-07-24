# 📘 Chapter 04: Multithreading (Part 2)

## Thread Methods, Thread Priority, Daemon Threads & Thread Information

> *"Creating a thread is only the beginning. Java provides several built-in methods to control, coordinate, and monitor thread execution, enabling developers to build responsive and efficient applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand important Thread methods.
- Learn how `sleep()`, `join()`, and `yield()` work.
- Understand Thread Priority.
- Learn about Daemon Threads.
- Get information about the current thread.
- Name threads and check their state.
- Follow Multithreading best practices.

---

# 📚 Table of Contents

1. Important Thread Methods
2. sleep()
3. join()
4. yield()
5. currentThread()
6. getName() & setName()
7. isAlive()
8. Thread Priority
9. Daemon Threads
10. Internal Working
11. Common Mistakes
12. Best Practices

---

# 📖 Important Thread Methods

Some frequently used methods of the `Thread` class are:

| Method | Purpose |
|---------|---------|
| `start()` | Starts a new thread |
| `run()` | Contains thread logic |
| `sleep()` | Pauses the current thread |
| `join()` | Waits for another thread to finish |
| `yield()` | Hints that the current thread is willing to give other runnable threads a chance |
| `currentThread()` | Returns the currently executing thread |
| `getName()` | Returns thread name |
| `setName()` | Changes thread name |
| `isAlive()` | Checks whether a thread is still running |
| `setPriority()` | Sets thread priority |
| `getPriority()` | Returns thread priority |
| `setDaemon()` | Marks a thread as a daemon thread |

---

# 📖 sleep() Method

The `sleep()` method pauses the **current thread** for a specified time.

Syntax

```java
Thread.sleep(milliseconds);
```

Example

```java
public class Demo{

    public static void main(String[] args) throws InterruptedException{

        System.out.println("Start");

        Thread.sleep(2000);

        System.out.println("End");

    }

}
```

Output

```text
Start

(Waits for about 2 seconds)

End
```

> ⚠️ `sleep()` throws `InterruptedException`, so it must be handled or declared with `throws`.

---

# 📖 join() Method

The `join()` method causes the current thread to wait until another thread finishes.

Example

```java
class MyThread extends Thread{

    @Override
    public void run(){

        for(int i = 1; i <= 3; i++){

            System.out.println(i);

        }

    }

}

public class Demo{

    public static void main(String[] args) throws InterruptedException{

        MyThread t = new MyThread();

        t.start();

        t.join();

        System.out.println("Main Thread Finished");

    }

}
```

Possible Output

```text
1
2
3
Main Thread Finished
```

Without `join()`, the main thread may continue without waiting.

---

# 📖 yield() Method

The `yield()` method gives a hint to the thread scheduler that the current thread is willing to pause and allow other runnable threads to execute.

Example

```java
class MyThread extends Thread{

    @Override
    public void run(){

        for(int i = 1; i <= 5; i++){

            System.out.println(i);

            Thread.yield();

        }

    }

}
```

> ⚠️ **Important:** `yield()` is only a **hint** to the scheduler. The JVM or operating system may ignore it.

---

# 📖 currentThread()

Returns the currently executing thread.

Example

```java
public class Demo{

    public static void main(String[] args){

        Thread t = Thread.currentThread();

        System.out.println(t);

    }

}
```

Possible Output

```text
Thread[main,5,main]
```

---

# 📖 getName() and setName()

Every thread has a name.

Example

```java
Thread t = Thread.currentThread();

System.out.println(t.getName());

t.setName("MainThread");

System.out.println(t.getName());
```

Output

```text
main

MainThread
```

---

# 📖 isAlive()

Checks whether a thread has been started and has not yet terminated.

Example

```java
class MyThread extends Thread{

    @Override
    public void run(){

        System.out.println("Running");

    }

}

public class Demo{

    public static void main(String[] args){

        MyThread t = new MyThread();

        System.out.println(t.isAlive());

        t.start();

        System.out.println(t.isAlive());

    }

}
```

Possible Output

```text
false

true
```

> The exact output depends on timing because the thread may finish quickly.

---

# 📖 Thread Priority

Each thread has a priority value between **1 and 10**.

| Constant | Value |
|----------|------:|
| `Thread.MIN_PRIORITY` | 1 |
| `Thread.NORM_PRIORITY` | 5 |
| `Thread.MAX_PRIORITY` | 10 |

Example

```java
Thread t = new Thread();

t.setPriority(Thread.MAX_PRIORITY);

System.out.println(t.getPriority());
```

Output

```text
10
```

> ⚠️ Thread priority is only a scheduling hint. The JVM and operating system may choose not to honor it.

---

# 📖 Daemon Thread

A **Daemon Thread** is a background thread that provides services to user threads.

Examples

- Garbage Collector
- Background Cleanup
- Monitoring Threads

When all **user threads** finish, the JVM exits—even if daemon threads are still running.

Example

```java
class MyThread extends Thread{

    @Override
    public void run(){

        while(true){

            System.out.println("Daemon Running");

        }

    }

}

public class Demo{

    public static void main(String[] args){

        MyThread t = new MyThread();

        t.setDaemon(true);

        t.start();

        System.out.println("Main Finished");

    }

}
```

> `setDaemon(true)` **must** be called **before** `start()`.

---

# 📦 Internal Working

When

```java
t.start();
```

is executed:

```text
Create Thread

↓

Runnable

↓

Scheduler Chooses Thread

↓

Running

↓

sleep() / join() / Waiting

↓

Runnable

↓

Running

↓

Terminated
```

---

# ⚠️ Common Mistakes

## ❌ Calling sleep() on an Object

Wrong

```java
t.sleep(1000);
```

Although this compiles because `sleep()` is static, it is misleading.

Correct

```java
Thread.sleep(1000);
```

---

## ❌ Calling setDaemon() After start()

Wrong

```java
t.start();

t.setDaemon(true);
```

Output

```text
IllegalThreadStateException
```

Correct

```java
t.setDaemon(true);

t.start();
```

---

## ❌ Assuming Priority Guarantees Execution Order

Wrong assumption

```text
Priority 10

↓

Always Executes First
```

This is **not guaranteed**.

Priority is only a scheduling hint.

---

## ❌ Calling run() Instead of start()

Wrong

```java
t.run();
```

Correct

```java
t.start();
```

---

# 💡 Best Practices

- Prefer implementing `Runnable` (or `Callable`) for task logic instead of extending `Thread`.
- Use `join()` only when synchronization is actually required.
- Avoid relying on thread priority for program correctness.
- Use daemon threads only for background services.
- Always handle `InterruptedException` properly.
- Give meaningful names to threads for easier debugging.

---

# 🌍 Real-World Applications

These thread methods are used in:

- Web Servers
- Spring Boot Applications
- Background File Processing
- Scheduled Tasks
- Multiplayer Games
- Banking Systems
- Chat Applications
- Download Managers
- Android Apps
- Monitoring Services

---

# 🎯 Interview Tip

### Question

What is the difference between `sleep()` and `join()`?

### Answer

| `sleep()` | `join()` |
|-----------|-----------|
| Pauses the **current thread** for a specified duration. | Makes the **current thread wait** until another thread finishes. |
| Time-based waiting. | Thread-completion-based waiting. |
| Static method of `Thread`. | Instance method of `Thread`. |

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Synchronization
- Race Condition
- `synchronized` Keyword
- Inter-thread Communication
- Deadlock
- Interview Questions
- MCQs
- Practice Problems
- Chapter Summary