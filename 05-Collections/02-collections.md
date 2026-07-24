# 📘 Chapter 05: Collections Framework (Part 2)

## Generic Collections, Collection Methods, ArrayList, LinkedList, HashSet & HashMap

> *"The real power of the Java Collections Framework comes from Generics, built-in methods, and efficient implementations like ArrayList, HashSet, and HashMap."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Generics in Collections.
- Learn commonly used Collection methods.
- Understand ArrayList.
- Understand LinkedList.
- Understand HashSet.
- Understand HashMap.
- Compare major Collection classes.
- Learn their time complexities.

---

# 📚 Table of Contents

1. Generic Collections
2. Common Collection Methods
3. ArrayList
4. LinkedList
5. HashSet
6. HashMap
7. Comparison
8. Time Complexity
9. Internal Working
10. Best Practices

---

# 📖 Generic Collections

Before Java 5, Collections stored objects of any type.

Example

```java
ArrayList list = new ArrayList();

list.add("Java");

list.add(100);
```

Problem

Different object types can be stored together, requiring explicit casting and increasing the chance of runtime errors.

---

## Solution → Generics

```java
ArrayList<String> list = new ArrayList<>();

list.add("Java");

// list.add(100); ❌ Compile-time Error
```

Benefits

- Type Safety
- No Explicit Casting
- Better Readability
- Compile-Time Error Detection

---

# 📖 Common Collection Methods

The `Collection` interface provides several useful methods.

| Method | Description |
|---------|-------------|
| `add()` | Adds an element |
| `remove()` | Removes an element |
| `contains()` | Checks whether an element exists |
| `size()` | Returns the number of elements |
| `isEmpty()` | Checks if the collection is empty |
| `clear()` | Removes all elements |
| `iterator()` | Returns an Iterator |

---

## Example

```java
ArrayList<String> list = new ArrayList<>();

list.add("Java");
list.add("Python");

System.out.println(list.size());

System.out.println(list.contains("Java"));

list.remove("Python");

System.out.println(list);
```

Output

```text
2

true

[Java]
```

---

# 📖 ArrayList

`ArrayList` is the most commonly used implementation of the `List` interface.

Characteristics

- Dynamic Array
- Maintains insertion order
- Allows duplicates
- Fast random access
- Slower insertions/deletions in the middle

---

## Example

```java
ArrayList<String> languages = new ArrayList<>();

languages.add("Java");
languages.add("Python");
languages.add("C++");

System.out.println(languages);
```

Output

```text
[Java, Python, C++]
```

---

## Internal Working

```text
Array

↓

[Java][Python][C++][ ]

↓

Capacity Full

↓

Create Larger Array

↓

Copy Elements

↓

Add New Element
```

---

# 📖 LinkedList

A `LinkedList` stores elements as nodes connected using references.

Characteristics

- Dynamic
- Doubly Linked List implementation
- Efficient insertion and deletion
- Slower random access than ArrayList

---

## Example

```java
LinkedList<String> cities = new LinkedList<>();

cities.add("Delhi");
cities.add("Mumbai");

System.out.println(cities);
```

Output

```text
[Delhi, Mumbai]
```

---

## Internal Working

```text
NULL

↓

[Delhi]

↓

[Mumbai]

↓

[Bengaluru]

↓

NULL
```

Each node stores:

- Previous Reference
- Data
- Next Reference

---

# 📖 ArrayList vs LinkedList

| Feature | ArrayList | LinkedList |
|---------|-----------|------------|
| Data Structure | Dynamic Array | Doubly Linked List |
| Random Access | Fast | Slow |
| Insert/Delete | Slower in middle | Faster in middle |
| Memory Usage | Lower | Higher |
| Best For | Frequent reading | Frequent insertion/deletion |

---

# 📖 HashSet

`HashSet` implements the `Set` interface.

Characteristics

- No duplicate elements
- No guaranteed order
- Uses hashing
- Allows one `null` element

---

## Example

```java
HashSet<Integer> numbers = new HashSet<>();

numbers.add(10);
numbers.add(20);
numbers.add(10);

System.out.println(numbers);
```

Possible Output

```text
[20, 10]
```

---

## Internal Working

```text
Hash Function

↓

Hash Code

↓

Bucket

↓

Store Element
```

---

# 📖 HashMap

`HashMap` stores data as key-value pairs.

Characteristics

- Unique Keys
- Duplicate Values Allowed
- One `null` key
- Multiple `null` values
- Fast lookup using hashing

---

## Example

```java
HashMap<Integer, String> students = new HashMap<>();

students.put(1, "Anshika");
students.put(2, "Rahul");

System.out.println(students);
```

Possible Output

```text
{1=Anshika, 2=Rahul}
```

---

## Internal Working

```text
Key

↓

hashCode()

↓

Bucket Index

↓

Store Key-Value Pair
```

---

# 📊 Major Collection Classes Comparison

| Feature | ArrayList | LinkedList | HashSet | HashMap |
|---------|-----------|------------|----------|----------|
| Duplicates | ✅ Yes | ✅ Yes | ❌ No | Keys ❌, Values ✅ |
| Ordered | ✅ Yes | ✅ Yes | ❌ No | ❌ No |
| Index-Based | ✅ Yes | ✅ Yes | ❌ No | ❌ No |
| Null Allowed | ✅ Yes | ✅ Yes | One `null` | One `null` key |
| Fast Search | Medium | Medium | Fast | Fast |

---

# 📊 Time Complexity

| Operation | ArrayList | LinkedList | HashSet | HashMap |
|-----------|-----------|------------|----------|----------|
| Add | O(1)* | O(1) | O(1)* | O(1)* |
| Search | O(n) | O(n) | O(1)* | O(1)* |
| Remove | O(n) | O(1)** | O(1)* | O(1)* |
| Get by Index | O(1) | O(n) | ❌ | ❌ |

### Notes

- `*` = Average case (worst case can degrade, e.g., due to hash collisions or resizing).
- `**` = O(1) when removing a known node (or first/last element); finding an element by value still requires traversal.

---

# 📦 Internal Working of Collections

```text
Application

↓

Collection Interface

↓

Implementation Class

↓

Data Structure

↓

Store Objects

↓

Retrieve Objects

↓

Modify Objects

↓

Output
```

---

# ⚠️ Common Mistakes

## ❌ Using Raw Collections

Wrong

```java
ArrayList list = new ArrayList();
```

Correct

```java
ArrayList<String> list = new ArrayList<>();
```

---

## ❌ Using ArrayList for Frequent Insertions

If your application performs many insertions/deletions in the middle of the list,

Prefer

```java
LinkedList
```

---

## ❌ Expecting Order from HashSet

Wrong Assumption

```java
HashSet

↓

10

↓

20

↓

30
```

`HashSet` does **not** guarantee insertion order.

Use

```java
LinkedHashSet
```

if insertion order matters.

---

## ❌ Expecting Sorted Order from HashMap

`HashMap` does **not** sort keys.

Use

```java
TreeMap
```

for sorted keys.

---

# 💡 Best Practices

- Use Generics with every Collection.
- Program to interfaces (`List`, `Set`, `Map`) rather than concrete implementations when possible.
- Choose the right implementation based on access patterns.
- Avoid unnecessary object creation.
- Prefer enhanced `for` loops or `Iterator` when appropriate.
- Avoid modifying a collection while iterating unless using the iterator's own methods or concurrent collections.

---

# 🌍 Real-World Applications

Collections are widely used in:

- Banking Systems
- Employee Management
- E-Commerce Platforms
- Hospital Management
- Airline Reservation Systems
- Online Food Delivery
- Social Media Platforms
- Spring Boot Applications

---

# 🎯 Interview Tip

### Question

Which is better: ArrayList or LinkedList?

### Answer

It depends on the use case:

- Use **ArrayList** when frequent reading or random access is required.
- Use **LinkedList** when frequent insertions and deletions are required.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Iterator
- ListIterator
- Comparable
- Comparator
- Collections Utility Class
- Interview Questions
- MCQs
- Practice Problems
- Chapter Summary