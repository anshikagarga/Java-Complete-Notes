# 📘 Chapter 04: Multithreading (Part 1)

> *"Multithreading is one of the most important concepts in Java. It allows a program to execute multiple tasks concurrently, improving responsiveness and better utilizing CPU resources."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what Multithreading is.
- Learn the difference between Process and Thread.
- Understand why Multithreading is needed.
- Learn the Thread Life Cycle.
- Create Threads using the Thread class.
- Create Threads using the Runnable interface.
- Understand the JVM's thread model.

---

# 📚 Table of Contents

1. Introduction to Multithreading
2. Why Multithreading?
3. Process vs Thread
4. Single Thread vs Multithreading
5. Thread Life Cycle
6. Creating Threads
7. Thread Class
8. Runnable Interface
9. Internal Working
10. Real-World Applications

---

# 🤔 What is Multithreading?

**Multithreading** is the ability of a program to execute **multiple threads simultaneously** within a single process.

A **Thread** is the smallest unit of execution inside a process.

Example

Imagine a web browser.

While:

- Loading a webpage
- Playing music
- Downloading a file

all these tasks happen together.

Each task runs in a separate thread.

---

# 💡 Why Do We Need Multithreading?

Without Multithreading

```text
Download File

↓

Play Music

↓

Open Browser

↓

Print Document
```

Each task waits for the previous one to finish.

---

With Multithreading

```text
Download File

↓

Play Music

↓

Open Browser

↓

Print Document

(All Running Concurrently)
```

This improves responsiveness and resource utilization.

---

# 📖 What is a Process?

A **Process** is an independent program in execution.

Examples

- Chrome
- VS Code
- Spotify
- IntelliJ IDEA

Each process has its own memory space.

---

# 📖 What is a Thread?

A **Thread** is the smallest execution unit inside a process.

Example

Chrome Browser

```text
Chrome Process

│

├── UI Thread

├── Rendering Thread

├── Download Thread

├── Audio Thread

└── Network Thread
```

All threads share the process memory.

---

# 📊 Process vs Thread

| Process | Thread |
|---------|--------|
| Independent program | Smallest execution unit |
| Separate memory | Shared memory |
| Heavyweight | Lightweight |
| Slow creation | Fast creation |
| Costly context switching | Faster context switching |
| More resource usage | Less resource usage |

---

# 📖 Single Thread vs Multithreading

## Single Thread

```text
Task A

↓

Task B

↓

Task C
```

One task at a time.

---

## Multithreading

```text
Task A

↘

Task B

↗

Task C
```

Tasks execute concurrently.

---

# 📦 Thread Life Cycle

```text
New

↓

Runnable

↓

Running

↓

Waiting / Blocked / Timed Waiting

↓

Runnable

↓

Running

↓

Terminated
```

---

## States Explained

### 1. New

A thread object is created but `start()` has not been called.

```java
Thread t = new Thread();
```

---

### 2. Runnable

The thread is ready to run and waiting for CPU scheduling.

```java
t.start();
```

---

### 3. Running

The scheduler assigns CPU time, and the thread executes the `run()` method.

---

### 4. Waiting / Blocked / Timed Waiting

The thread temporarily stops execution because it is:

- Waiting for another thread
- Sleeping
- Waiting for a lock
- Waiting for I/O

---

### 5. Terminated

The thread finishes execution or exits because of an uncaught exception.

---

# 📖 Creating a Thread (Method 1)

## Extending the Thread Class

```java
class MyThread extends Thread{

    @Override
    public void run(){

        System.out.println("Thread is Running");

    }

}

public class Demo{

    public static void main(String[] args){

        MyThread t = new MyThread();

        t.start();

    }

}
```

Output

```text
Thread is Running
```

---

# ❌ Don't Call run() Directly

Wrong

```java
t.run();
```

This behaves like a normal method call and does **not** create a new thread.

Correct

```java
t.start();
```

`start()` creates a new thread and then invokes `run()` internally.

---

# 📖 Creating a Thread (Method 2)

## Implementing Runnable

```java
class MyTask implements Runnable{

    @Override
    public void run(){

        System.out.println("Runnable Thread");

    }

}

public class Demo{

    public static void main(String[] args){

        Thread t = new Thread(new MyTask());

        t.start();

    }

}
```

Output

```text
Runnable Thread
```

---

# 🤔 Thread Class vs Runnable Interface

| Thread Class | Runnable Interface |
|--------------|-------------------|
| Extend `Thread` | Implement `Runnable` |
| Cannot extend another class | Can still extend another class |
| Less flexible | More flexible |
| Suitable for simple examples | Recommended in real projects |

---

# 📦 Internal Working

When you execute

```java
t.start();
```

Flow

```text
Create Thread Object

↓

Call start()

↓

JVM Creates New Thread

↓

Scheduler Places Thread in Runnable State

↓

CPU Executes run()

↓

Thread Completes

↓

Terminated
```

---

# ⚡ Time Complexity

Creating a thread is generally considered an **O(1)** operation from an algorithmic perspective, although the actual execution cost depends on the operating system and JVM implementation.

---

# 🌍 Real-World Applications

Multithreading is used in:

- Web Servers
- Spring Boot Applications
- Gaming
- Banking Systems
- Chat Applications
- Video Streaming
- File Download Managers
- Database Servers
- Android Applications
- Real-Time Systems

---

# 🎯 Interview Tip

### Question

What is the difference between `start()` and `run()`?

### Answer

- `start()` creates a **new thread** and then internally calls `run()`.
- `run()` is just a normal method. Calling it directly does **not** create a new thread.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Thread Methods (`sleep()`, `join()`, `yield()`)
- Thread Priority
- `isAlive()`
- `currentThread()`
- Thread Naming
- Daemon Threads
- Best Practices