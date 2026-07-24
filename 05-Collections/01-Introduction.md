# 📘 Chapter 05: Collections Framework (Part 1)

> *"The Java Collections Framework (JCF) is a unified architecture for storing, manipulating, and processing groups of objects efficiently. It provides ready-made data structures and algorithms, making Java development faster, cleaner, and more efficient."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what the Collections Framework is.
- Learn why Collections are needed.
- Differentiate Arrays and Collections.
- Understand the Collection Hierarchy.
- Learn Collection Interfaces.
- Understand List, Set, Queue, and Map.
- Learn how the Collections Framework works internally.

---

# 📚 Table of Contents

1. Introduction
2. Why Collections Framework?
3. Arrays vs Collections
4. What is the Collections Framework?
5. Collection Hierarchy
6. Collection Interfaces
7. List Interface
8. Set Interface
9. Queue Interface
10. Map Interface
11. Iterable Interface
12. Advantages
13. Internal Working
14. Real-World Applications

---

# 🤔 What is the Collections Framework?

The **Java Collections Framework (JCF)** is a set of **interfaces**, **classes**, and **algorithms** used to store and manipulate groups of objects.

Instead of creating your own data structures, Java provides ready-made implementations like:

- ArrayList
- LinkedList
- HashSet
- TreeSet
- HashMap
- PriorityQueue

---

# 💡 Why Do We Need Collections?

Suppose we need to store the names of students.

Without Collections

```java
String s1 = "Anshika";
String s2 = "Rahul";
String s3 = "Aman";
String s4 = "Priya";
```

Managing hundreds or thousands of values becomes difficult.

Collections solve this problem.

```java
ArrayList<String> students = new ArrayList<>();
```

Now we can add, remove, search, and sort data easily.

---

# 📊 Arrays vs Collections

| Arrays | Collections |
|---------|-------------|
| Fixed Size | Dynamic Size |
| Stores primitives and objects | Stores objects (primitives via wrapper classes) |
| Less flexible | Highly flexible |
| No built-in algorithms | Sorting, searching, etc. available |
| Faster for fixed-size data | Better for dynamic data |

---

# 📖 What is a Collection?

A **Collection** is an object that represents a group of objects.

Examples

- List of Students
- Employees
- Products
- Orders
- Customers

---

# 📖 Collection Framework Components

The Java Collections Framework consists of three major parts:

### 1. Interfaces

Examples

- Collection
- List
- Set
- Queue
- Map

---

### 2. Implementations (Classes)

Examples

- ArrayList
- LinkedList
- HashSet
- TreeSet
- HashMap

---

### 3. Algorithms

Examples

- Sorting
- Searching
- Shuffling
- Reversing
- Binary Search

Provided by the `Collections` utility class.

---

# 📦 Collection Hierarchy

```text
                    Iterable
                        │
                  Collection
        ┌──────────┼──────────┐
        │          │          │
      List        Set       Queue
       │           │           │
 ┌─────┼─────┐   ┌──┼──┐     ┌──┴────┐
 │     │     │   │  │  │     │       │
Array Linked Vector Hash Linked Tree Priority
List  List         Set HashSet Set   Queue

Map (Separate Hierarchy)
│
├── HashMap
├── LinkedHashMap
├── TreeMap
├── Hashtable
└── WeakHashMap
```

> **Important:** `Map` is **not** a child of the `Collection` interface.

---

# 📖 Iterable Interface

The **Iterable** interface is the root interface that allows objects to be traversed using the enhanced for-loop (`for-each`).

Example

```java
ArrayList<String> list = new ArrayList<>();

list.add("Java");
list.add("Python");

for(String language : list){

    System.out.println(language);

}
```

Output

```text
Java
Python
```

---

# 📖 Collection Interface

The **Collection** interface is the parent interface for:

- List
- Set
- Queue

It provides common methods such as:

```java
add()

remove()

contains()

size()

clear()

isEmpty()
```

Example

```java
Collection<String> names = new ArrayList<>();

names.add("Anshika");

System.out.println(names.size());
```

Output

```text
1
```

---

# 📖 List Interface

A **List** is an ordered collection.

Characteristics

- Maintains insertion order.
- Allows duplicate elements.
- Supports index-based access.

Implementations

- ArrayList
- LinkedList
- Vector
- Stack

Example

```java
List<String> list = new ArrayList<>();

list.add("Java");
list.add("Python");
list.add("Java");

System.out.println(list);
```

Output

```text
[Java, Python, Java]
```

---

# 📖 Set Interface

A **Set** stores **unique elements**.

Characteristics

- No duplicates.
- No index-based access.
- Faster searching in many implementations.

Implementations

- HashSet
- LinkedHashSet
- TreeSet

Example

```java
Set<Integer> set = new HashSet<>();

set.add(10);
set.add(20);
set.add(10);

System.out.println(set);
```

Possible Output

```text
[10, 20]
```

---

# 📖 Queue Interface

A **Queue** follows the **FIFO (First In First Out)** principle.

Implementations

- PriorityQueue
- ArrayDeque
- LinkedList

Example

```java
Queue<Integer> queue = new LinkedList<>();

queue.offer(10);
queue.offer(20);

System.out.println(queue.poll());
```

Output

```text
10
```

---

# 📖 Map Interface

A **Map** stores data as **key-value pairs**.

Characteristics

- Unique keys.
- Duplicate values allowed.
- Does **not** extend `Collection`.

Implementations

- HashMap
- LinkedHashMap
- TreeMap
- Hashtable

Example

```java
Map<Integer, String> map = new HashMap<>();

map.put(1, "Java");
map.put(2, "Python");

System.out.println(map);
```

Possible Output

```text
{1=Java, 2=Python}
```

---

# 📦 Internal Working

```text
Application

↓

Collection Interface

↓

List / Set / Queue / Map

↓

Implementation Class

↓

Objects Stored

↓

Operations

↓

Output
```

---

# ✅ Advantages

- Dynamic size.
- Reusable data structures.
- Built-in algorithms.
- Easy searching and sorting.
- Better code readability.
- Improved productivity.
- Generic type safety.

---

# ⚠️ Limitations

- Cannot directly store primitive data types.
- Wrapper classes may introduce slight memory overhead.
- Choosing the wrong collection can impact performance.

---

# 🌍 Real-World Applications

Collections are used in:

- Banking Systems
- Social Media Platforms
- Shopping Carts
- Hospital Management Systems
- Inventory Systems
- Employee Management
- Online Booking Systems
- Spring Boot Applications

---

# 🎯 Interview Tip

### Question

What is the difference between Collection and Collections?

### Answer

- **Collection** is an **interface** that represents a group of objects.
- **Collections** is a **utility class** that provides static methods like `sort()`, `reverse()`, `shuffle()`, and `binarySearch()`.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Generic Collections
- Collection Methods
- ArrayList Overview
- LinkedList Overview
- HashSet Overview
- HashMap Overview
- Time Complexity
- Best Practices