# 📘 Chapter 05: Collections Framework (Part 3)

## Iterator, Comparable, Comparator, Collections Utility Class, Interview Questions & Chapter Summary

> *"The Collections Framework is not just about storing data. It also provides powerful tools for traversing, sorting, searching, and organizing data efficiently."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Iterator and ListIterator.
- Learn the Collections Utility Class.
- Understand Comparable and Comparator.
- Learn sorting techniques.
- Answer interview questions confidently.
- Solve MCQs and practice problems.

---

# 📚 Table of Contents

1. Iterator
2. ListIterator
3. Collections Utility Class
4. Comparable
5. Comparator
6. Comparable vs Comparator
7. Internal Working
8. Best Practices
9. Interview Questions
10. MCQs
11. Quick Revision
12. Practice Problems
13. Related Topics
14. References
15. Chapter Summary

---

# 📖 Iterator

An **Iterator** is used to traverse elements of a collection one by one.

Methods

| Method | Description |
|---------|-------------|
| `hasNext()` | Checks if another element exists |
| `next()` | Returns the next element |
| `remove()` | Removes the current element safely |

---

## Example

```java
ArrayList<String> languages = new ArrayList<>();

languages.add("Java");
languages.add("Python");
languages.add("C++");

Iterator<String> itr = languages.iterator();

while(itr.hasNext()){

    System.out.println(itr.next());

}
```

Output

```text
Java
Python
C++
```

---

# 📖 ListIterator

`ListIterator` is available only for **List** implementations.

Features

- Forward Traversal
- Backward Traversal
- Add Elements
- Remove Elements
- Update Elements

---

## Example

```java
ArrayList<String> list = new ArrayList<>();

list.add("Java");
list.add("Python");

ListIterator<String> itr = list.listIterator();

while(itr.hasNext()){

    System.out.println(itr.next());

}
```

---

## Moving Backward

```java
while(itr.hasPrevious()){

    System.out.println(itr.previous());

}
```

Output

```text
Python
Java
```

---

# 📖 Iterator vs ListIterator

| Feature | Iterator | ListIterator |
|---------|----------|--------------|
| Forward Traversal | ✅ | ✅ |
| Backward Traversal | ❌ | ✅ |
| Add Elements | ❌ | ✅ |
| Update Elements | ❌ | ✅ (`set()`) |
| Works With | All Collections | Only Lists |

---

# 📖 Collections Utility Class

The `Collections` class provides static utility methods for common collection operations.

Common Methods

| Method | Purpose |
|---------|----------|
| `sort()` | Sorts a list |
| `reverse()` | Reverses a list |
| `shuffle()` | Randomly shuffles elements |
| `swap()` | Swaps two elements |
| `binarySearch()` | Performs binary search on a sorted list |
| `max()` | Returns the maximum element |
| `min()` | Returns the minimum element |
| `frequency()` | Counts occurrences of an element |

---

## Example

```java
ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(30);
numbers.add(10);
numbers.add(20);

Collections.sort(numbers);

System.out.println(numbers);
```

Output

```text
[10, 20, 30]
```

---

## Reverse

```java
Collections.reverse(numbers);
```

Output

```text
[30, 20, 10]
```

---

## Shuffle

```java
Collections.shuffle(numbers);
```

Possible Output

```text
[20, 30, 10]
```

---

# 📖 Comparable Interface

The **Comparable** interface is used to define the **default (natural) ordering** of objects.

Method

```java
compareTo()
```

---

## Example

```java
class Student implements Comparable<Student>{

    int marks;

    Student(int marks){

        this.marks = marks;

    }

    @Override
    public int compareTo(Student s){

        return this.marks - s.marks;

    }

}
```

Sorting

```java
Collections.sort(studentList);
```

---

# 📖 Comparator Interface

A **Comparator** is used when you need **custom sorting** without modifying the class.

Method

```java
compare()
```

---

## Example

```java
Comparator<Student> comparator = (s1, s2) -> s2.marks - s1.marks;

Collections.sort(studentList, comparator);
```

This sorts students in descending order of marks.

---

# 📊 Comparable vs Comparator

| Comparable | Comparator |
|------------|------------|
| Package: `java.lang` | Package: `java.util` |
| Natural ordering | Custom ordering |
| Uses `compareTo()` | Uses `compare()` |
| Class must implement it | Separate comparator object |
| One default sorting logic | Multiple sorting strategies possible |

---

# 📖 Internal Working of Sorting

```text
List

↓

Collections.sort()

↓

Comparable / Comparator

↓

Comparison Logic

↓

Sorted List
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting Comparable

Wrong

```java
Collections.sort(studentList);
```

If `Student` doesn't implement `Comparable`, a `ClassCastException` is thrown at runtime.

---

## ❌ Wrong compareTo()

Wrong

```java
return 1;
```

Correct

```java
return this.marks - s.marks;
```

Or better, to avoid integer overflow:

```java
return Integer.compare(this.marks, s.marks);
```

---

## ❌ Modifying Collection During For-Each

Wrong

```java
for(String name : list){

    list.remove(name);

}
```

This may throw a `ConcurrentModificationException`.

Correct

```java
Iterator<String> itr = list.iterator();

while(itr.hasNext()){

    if(itr.next().equals("Java")){

        itr.remove();

    }

}
```

---

# 💡 Best Practices

- Use **Comparable** for a class's natural ordering.
- Use **Comparator** for multiple custom sorting rules.
- Prefer `Integer.compare()`, `Long.compare()`, etc., over subtraction for comparisons.
- Use `Iterator` when removing elements during traversal.
- Use the `Collections` utility methods instead of writing common algorithms from scratch.
- Program to interfaces (`List`, `Set`, `Map`) whenever possible.

---

# 🌍 Real-World Applications

Collections Framework is used in:

- Banking Systems
- Student Management Systems
- Inventory Systems
- Social Media Platforms
- Spring Boot Applications
- Airline Reservation Systems
- E-Commerce Platforms
- Hospital Management Systems

---

# 🧩 Interview Questions

## Beginner

1. What is the Java Collections Framework?
2. Difference between Array and ArrayList.
3. Difference between List and Set.
4. Difference between HashSet and TreeSet.
5. Difference between HashMap and Hashtable.

---

## Intermediate

6. Difference between Comparable and Comparator.
7. Difference between Iterator and ListIterator.
8. What is the Collections Utility Class?
9. Difference between Collection and Collections.
10. Explain Generics in Collections.

---

## Advanced

11. How does HashMap work internally?
12. How does HashSet avoid duplicates?
13. Why is ArrayList faster than LinkedList for random access?
14. What is the average time complexity of HashMap operations?
15. What is a ConcurrentModificationException, and when can it occur?

---

# 🎓 MCQs

### Q1. Which interface is implemented by `ArrayList`?

- A. Set
- B. Queue
- C. List ✅
- D. Map

---

### Q2. Which interface is used for natural sorting?

- A. Comparator
- B. Comparable ✅
- C. Collection
- D. Iterable

---

### Q3. Which class provides `sort()` and `reverse()` methods?

- A. Collection
- B. Arrays
- C. Collections ✅
- D. Iterator

---

### Q4. Which collection does **not** allow duplicate elements?

- A. ArrayList
- B. LinkedList
- C. HashSet ✅
- D. Vector

---

### Q5. Which interface allows backward traversal?

- A. Iterator
- B. Enumeration
- C. ListIterator ✅
- D. Comparable

---

# 📝 Quick Revision

## Collection Hierarchy

```text
Iterable

↓

Collection

↓

List / Set / Queue

↓

ArrayList
LinkedList
HashSet
TreeSet

Map (Separate Hierarchy)
```

---

## Comparable

```java
class Student implements Comparable<Student>{

    @Override
    public int compareTo(Student s){

        return Integer.compare(this.marks, s.marks);

    }

}
```

---

## Comparator

```java
Comparator<Student> comp =
    (s1, s2) -> Integer.compare(s2.marks, s1.marks);
```

---

## Iterator

```java
Iterator<String> itr = list.iterator();

while(itr.hasNext()){

    System.out.println(itr.next());

}
```

---

## Collections Utility Class

```java
Collections.sort(list);

Collections.reverse(list);

Collections.shuffle(list);

Collections.max(list);

Collections.min(list);
```

---

# 🧪 Practice Problems

## Beginner

- Store student names using `ArrayList`.
- Remove duplicate values using `HashSet`.
- Store employee details using `HashMap`.

---

## Intermediate

- Sort a list of integers in ascending and descending order.
- Sort a list of `Student` objects using `Comparable`.
- Sort employees by salary using `Comparator`.

---

## Advanced

- Build a Student Management System using Collections.
- Create a Library Management System using `HashMap`.
- Implement an Inventory System using `TreeMap`.
- Design an Employee Directory using `ArrayList` and `Comparator`.

---

# 🔗 Related Topics

- Generics
- Exception Handling
- Multithreading
- File Handling
- Streams API
- Lambda Expressions

---

# 📚 References

- Oracle Java Documentation
- Effective Java by Joshua Bloch
- Java: The Complete Reference
- OpenJDK Documentation
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 05: Collections Framework**.

### ✔️ Concepts Covered

- Java Collections Framework
- Collection Hierarchy
- List, Set, Queue & Map
- ArrayList
- LinkedList
- HashSet
- HashMap
- Iterator
- ListIterator
- Collections Utility Class
- Comparable
- Comparator
- Sorting
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Collections provide dynamic and reusable data structures.
- ✅ Use **ArrayList** for fast random access.
- ✅ Use **LinkedList** for frequent insertions and deletions.
- ✅ Use **HashSet** to store unique elements.
- ✅ Use **HashMap** to store key-value pairs with fast average-case lookup.
- ✅ Use **Comparable** for natural ordering and **Comparator** for custom sorting.
- ✅ Use the **Collections** utility class for common operations like sorting, reversing, and searching.

---

# 🚀 Next Chapter

➡️ **06-Streams-and-Java-8.md**

### Topics Covered

- Introduction to Java 8
- Features of Java 8
- Lambda Expressions
- Functional Interfaces
- Method References
- Stream API
- Stream Operations (Intermediate & Terminal)
- Optional Class
- Date & Time API (java.time)
- Default & Static Methods in Interfaces
- Predicate, Function, Consumer & Supplier
- Parallel Streams
- Interview Questions
- MCQs
- Practice Problems