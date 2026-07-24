# 📘 Chapter 04: Multithreading (Part 3)

## Synchronization, Race Condition, Deadlock, Interview Questions & Chapter Summary

> *"Multithreading improves performance, but when multiple threads access shared data simultaneously, it can lead to inconsistent results. Synchronization helps ensure data integrity and thread safety."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Race Conditions.
- Learn Synchronization.
- Use the `synchronized` keyword.
- Understand synchronized methods and blocks.
- Learn Inter-thread Communication.
- Understand Deadlock and its prevention.
- Solve interview questions and MCQs.

---

# 📚 Table of Contents

1. Race Condition
2. Synchronization
3. synchronized Method
4. synchronized Block
5. Inter-thread Communication
6. Deadlock
7. Deadlock Prevention
8. Common Mistakes
9. Best Practices
10. Interview Questions
11. MCQs
12. Quick Revision
13. Practice Problems
14. Related Topics
15. References
16. Chapter Summary

---

# 📖 What is a Race Condition?

A **Race Condition** occurs when **two or more threads access and modify shared data at the same time**, causing unpredictable or incorrect results.

Example

Suppose two threads are updating the same bank account balance.

```text
Balance = ₹1000

↓

Thread A Withdraws ₹500

↓

Thread B Withdraws ₹700

↓

Final Balance ?

Incorrect Result Possible
```

Without proper synchronization, both threads may read the same balance before either update is completed.

---

# 📖 Example of Race Condition

```java
class Counter{

    int count = 0;

    public void increment(){

        count++;

    }

}

public class Demo{

    public static void main(String[] args) throws InterruptedException{

        Counter counter = new Counter();

        Thread t1 = new Thread(() -> {

            for(int i = 0; i < 1000; i++){

                counter.increment();

            }

        });

        Thread t2 = new Thread(() -> {

            for(int i = 0; i < 1000; i++){

                counter.increment();

            }

        });

        t1.start();
        t2.start();

        t1.join();
        t2.join();

        System.out.println(counter.count);

    }

}
```

Expected Output

```text
2000
```

Possible Output

```text
1987
1992
1999
2000
```

The output is unpredictable because of a race condition.

---

# 📖 What is Synchronization?

**Synchronization** is a mechanism that allows **only one thread at a time** to access a shared resource.

It prevents:

- Race Conditions
- Data inconsistency
- Unexpected behavior

---

# 📖 synchronized Method

The easiest way to synchronize access to shared data is by declaring the method as `synchronized`.

```java
class Counter{

    int count = 0;

    public synchronized void increment(){

        count++;

    }

}
```

Now only one thread can execute `increment()` on the same object at a time.

---

# 📖 synchronized Block

Instead of synchronizing the whole method, you can synchronize only the critical section.

Syntax

```java
synchronized(object){

    // Critical Section

}
```

Example

```java
class Counter{

    int count = 0;

    public void increment(){

        synchronized(this){

            count++;

        }

    }

}
```

This often improves performance by reducing the amount of synchronized code.

---

# 📊 synchronized Method vs synchronized Block

| synchronized Method | synchronized Block |
|----------------------|--------------------|
| Locks the entire method | Locks only a specific block |
| Easier to write | More flexible |
| Can reduce concurrency | Better performance in many cases |
| Good for simple cases | Preferred for complex logic |

---

# 📖 Inter-thread Communication

Java allows threads to communicate using methods inherited from `Object`.

| Method | Purpose |
|---------|---------|
| `wait()` | Releases the lock and waits |
| `notify()` | Wakes up one waiting thread |
| `notifyAll()` | Wakes up all waiting threads |

These methods must be called **inside a synchronized context**.

---

## wait()

Example

```java
synchronized(obj){

    obj.wait();

}
```

The current thread:

- Releases the monitor (lock).
- Moves to the waiting state.
- Resumes only after being notified.

---

## notify()

```java
synchronized(obj){

    obj.notify();

}
```

Wakes up **one** waiting thread.

---

## notifyAll()

```java
synchronized(obj){

    obj.notifyAll();

}
```

Wakes up **all** waiting threads.

---

# 📖 Deadlock

A **Deadlock** occurs when two or more threads wait indefinitely for each other to release resources.

---

## Deadlock Example

```text
Thread A

↓

Locks Resource 1

↓

Waiting for Resource 2

-------------------------

Thread B

↓

Locks Resource 2

↓

Waiting for Resource 1

-------------------------

No Thread Can Continue
```

Both threads are blocked forever.

---

# 📖 Deadlock Prevention

Follow these practices:

- Acquire locks in the same order.
- Minimize the number of locks.
- Avoid nested locks when possible.
- Use lock timeouts (`java.util.concurrent.locks.Lock`) when appropriate.
- Keep synchronized sections as small as possible.

---

# 📦 Internal Working

When two threads enter a synchronized method:

```text
Thread A

↓

Acquires Lock

↓

Executes Critical Section

↓

Releases Lock

↓

Thread B Acquires Lock

↓

Executes

↓

Releases Lock
```

Only one thread owns the monitor at a time.

---

# ⚠️ Common Mistakes

## ❌ Forgetting Synchronization

Wrong

```java
count++;
```

Multiple threads may update the variable simultaneously.

Correct

```java
public synchronized void increment(){

    count++;

}
```

---

## ❌ Synchronizing on the Wrong Object

Wrong

```java
synchronized(new Object()){

    count++;

}
```

Each call uses a new lock object, so synchronization is ineffective.

Correct

```java
synchronized(this){

    count++;

}
```

Or synchronize on a shared lock object.

---

## ❌ Calling wait() Outside synchronized

Wrong

```java
obj.wait();
```

Output

```text
IllegalMonitorStateException
```

Correct

```java
synchronized(obj){

    obj.wait();

}
```

---

## ❌ Ignoring Deadlock Risks

Nested locks taken in different orders can easily create deadlocks.

---

# 💡 Best Practices

- Synchronize only the critical section.
- Avoid unnecessary locking.
- Keep synchronized blocks small.
- Prefer higher-level concurrency utilities (`ExecutorService`, `ConcurrentHashMap`, `BlockingQueue`, etc.) for complex applications.
- Avoid busy waiting.
- Use immutable objects when possible.
- Test multithreaded code thoroughly.

---

# 🌍 Real-World Applications

Synchronization is widely used in:

- Banking Systems
- ATM Software
- E-Commerce Applications
- Inventory Management
- Airline Reservation Systems
- Hospital Management Systems
- Online Ticket Booking
- Payment Gateways
- Multiplayer Games
- Cloud Servers

---

# 🧩 Interview Questions

## Beginner

1. What is Multithreading?
2. What is a Thread?
3. What is Synchronization?
4. What is a Race Condition?
5. Why is synchronization needed?

---

## Intermediate

6. Difference between Process and Thread.
7. Difference between `start()` and `run()`.
8. Difference between `sleep()` and `wait()`.
9. Difference between synchronized method and synchronized block.
10. Explain the Thread Life Cycle.

---

## Advanced

11. What is Deadlock?
12. How can Deadlock be prevented?
13. Explain `wait()`, `notify()`, and `notifyAll()`.
14. What is Thread Safety?
15. Why is `Runnable` generally preferred over extending `Thread`?

---

# 🎓 MCQs

### Q1. Which keyword is used for synchronization?

- A. `thread`
- B. `sync`
- C. `synchronized` ✅
- D. `lock`

---

### Q2. Which method starts a new thread?

- A. `run()`
- B. `execute()`
- C. `start()` ✅
- D. `begin()`

---

### Q3. Which method pauses the current thread for a specified time?

- A. `wait()`
- B. `sleep()` ✅
- C. `join()`
- D. `yield()`

---

### Q4. Which method waits for another thread to complete?

- A. `sleep()`
- B. `join()` ✅
- C. `yield()`
- D. `notify()`

---

### Q5. A race condition occurs when:

- A. Only one thread accesses data.
- B. Multiple threads access shared data without proper synchronization. ✅
- C. Threads are executed sequentially.
- D. The JVM crashes.

---

# 📝 Quick Revision

## Create a Thread

```java
Thread t = new Thread();

t.start();
```

---

## Synchronization

```java
public synchronized void increment(){

    count++;

}
```

---

## synchronized Block

```java
synchronized(this){

    count++;

}
```

---

## Thread Communication

```java
wait();

notify();

notifyAll();
```

---

## Deadlock

```text
Thread A → Waiting for B

Thread B → Waiting for A

↓

Deadlock
```

---

# 🧪 Practice Problems

## Beginner

- Create two threads that print numbers.
- Demonstrate the use of `join()`.
- Print the current thread name.

---

## Intermediate

- Create a synchronized counter.
- Demonstrate a race condition.
- Use `wait()` and `notify()` to coordinate two threads.

---

## Advanced

- Implement a Producer-Consumer problem.
- Create a Thread Pool using `ExecutorService`.
- Build a multithreaded file downloader.
- Simulate a banking system with synchronized account transfers.

---

# 🔗 Related Topics

- Exception Handling
- Collections Framework
- Generics
- Lambda Expressions
- Executor Framework
- Fork/Join Framework
- Concurrent Collections
- Java Memory Model (JMM)

---

# 📚 References

- Oracle Java Documentation
- Effective Java by Joshua Bloch
- Java Concurrency in Practice
- OpenJDK Documentation
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 04: Multithreading**.

### ✔️ Concepts Covered

- Multithreading Basics
- Process vs Thread
- Thread Life Cycle
- Thread Creation
- `Thread` Class
- `Runnable` Interface
- Thread Methods (`start()`, `sleep()`, `join()`, `yield()`)
- Daemon Threads
- Synchronization
- Race Conditions
- `synchronized` Methods and Blocks
- Inter-thread Communication (`wait()`, `notify()`, `notifyAll()`)
- Deadlock
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ A **Thread** is the smallest unit of execution inside a process.
- ✅ Use `start()` to create a new thread; calling `run()` directly does not create one.
- ✅ `Runnable` is generally preferred over extending `Thread` because it offers greater flexibility.
- ✅ Synchronization prevents race conditions by allowing only one thread at a time to access critical sections.
- ✅ `wait()`, `notify()`, and `notifyAll()` enable communication between threads and must be used within synchronized code.
- ✅ Keep synchronized blocks as small as possible to improve concurrency.
- ✅ Prefer modern concurrency utilities from `java.util.concurrent` for scalable multithreaded applications.

---

# 🚀 Next Chapter

➡️ **05-collections.md**

### Topics Covered

- Introduction to Collections Framework
- Collection Interface
- List Interface
- ArrayList
- LinkedList
- Vector
- Stack
- Queue
- PriorityQueue
- Deque
- Set Interface
- HashSet
- LinkedHashSet
- TreeSet
- Map Interface
- HashMap
- LinkedHashMap
- TreeMap
- Iterator & ListIterator
- Collections Utility Class
- Generics with Collections
- Comparable vs Comparator
- Interview Questions
- MCQs
- Practice Problems