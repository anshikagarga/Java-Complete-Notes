# 📘 Chapter 09: Searching (Part 3)

> *"Searching is one of the most frequently asked topics in Java interviews. Understanding when to use Linear Search, Binary Search, and Java's built-in searching methods is essential for writing efficient and optimized code."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Revise Searching Concepts
- Solve Interview Questions
- Practice MCQs
- Solve Coding Problems
- Understand Best Practices
- Revise Searching Algorithms

---

# 📚 Table of Contents

1. Interview Questions
2. MCQs
3. Coding Practice
4. Best Practices
5. Common Mistakes
6. Quick Revision
7. Real-World Applications
8. References
9. Chapter Summary

---

# 🎤 Interview Questions

## Beginner Level

### Q1. What is Searching?

**Answer**

Searching is the process of finding a particular element in a collection such as an array, list, or object collection.

Example

```text
Array

10 20 30 40 50

Search

40

Result

Found
```

---

### Q2. What are the two main searching algorithms?

**Answer**

- Linear Search
- Binary Search

---

### Q3. What is Linear Search?

**Answer**

Linear Search checks each element one by one until the required element is found or the collection ends.

Time Complexity

```text
Best Case : O(1)

Average Case : O(n)

Worst Case : O(n)
```

---

### Q4. What is Binary Search?

**Answer**

Binary Search repeatedly divides the sorted data into two halves until the element is found.

Requirement

```text
Data must be sorted.
```

Time Complexity

```text
Best Case : O(1)

Average Case : O(log n)

Worst Case : O(log n)
```

---

### Q5. Which search algorithm is faster?

**Answer**

Binary Search is much faster than Linear Search for large sorted datasets because it eliminates half of the search space in each iteration.

---

# 🎤 Intermediate Questions

### Q6. Why must Binary Search use sorted data?

**Answer**

Binary Search decides whether to search the left or right half by comparing the middle element with the target.

If the data is not sorted, this decision becomes incorrect and the algorithm fails.

---

### Q7. What is the time complexity of Binary Search?

| Case | Complexity |
|------|------------|
| Best | O(1) |
| Average | O(log n) |
| Worst | O(log n) |

---

### Q8. Difference between Arrays.binarySearch() and Collections.binarySearch()?

| Arrays.binarySearch() | Collections.binarySearch() |
|-----------------------|----------------------------|
| Works on Arrays | Works on Lists |
| Package: java.util.Arrays | Package: java.util.Collections |
| Requires Sorted Array | Requires Sorted List |

---

### Q9. What happens if the element is not found?

**Answer**

`Arrays.binarySearch()` and `Collections.binarySearch()` return a **negative value**, indicating that the element does not exist in the collection.

---

### Q10. Can Binary Search work on objects?

**Answer**

Yes.

Objects can be searched using:

- Comparable
- Comparator

provided the objects are already sorted.

---

# 🎤 Advanced Questions

### Q11. Difference between Iterative and Recursive Binary Search?

| Iterative | Recursive |
|-----------|-----------|
| Uses loops | Uses recursion |
| Better memory usage | Uses call stack |
| Generally preferred | Easier to understand |

---

### Q12. Which search should be used for unsorted data?

**Answer**

Linear Search.

Binary Search should never be used on unsorted data.

---

### Q13. Why calculate mid as `low + (high - low) / 2`?

**Answer**

This avoids integer overflow that may occur with:

```java
(low + high) / 2
```

Preferred

```java
int mid = low + (high - low) / 2;
```

---

### Q14. Which search algorithm is used in Java Collections?

**Answer**

Java provides

```java
Arrays.binarySearch()

Collections.binarySearch()
```

Both use the Binary Search algorithm internally.

---

### Q15. Which searching algorithm should you choose?

**Answer**

| Situation | Best Choice |
|-----------|-------------|
| Small Data | Linear Search |
| Unsorted Data | Linear Search |
| Large Sorted Data | Binary Search |
| Frequently Searched Data | Binary Search |

---

# 💡 Best Practices

✔ Use Linear Search for small datasets.

✔ Always sort data before Binary Search.

✔ Prefer Java's built-in methods instead of writing Binary Search manually when appropriate.

✔ Check the return value before accessing an index.

✔ Use the same Comparator for sorting and searching objects.

✔ Calculate the middle index safely using:

```java
low + (high - low) / 2
```

---

# ⚠️ Common Mistakes

## ❌ Binary Search on Unsorted Data

Wrong

```text
40 20 10 50 30
```

Correct

```text
10 20 30 40 50
```

---

## ❌ Ignoring Negative Return Values

Wrong

```java
int index = Arrays.binarySearch(arr,100);

System.out.println(arr[index]);
```

Correct

```java
if(index >= 0){

    System.out.println("Found");

}

else{

    System.out.println("Not Found");

}
```

---

## ❌ Wrong Middle Calculation

Wrong

```java
int mid = (low + high) / 2;
```

Correct

```java
int mid = low + (high - low) / 2;
```

---

## ❌ Using Different Comparators

Wrong

```java
Collections.sort(

students,

Comparator.comparing(Student::getId)

);

Collections.binarySearch(

students,

student,

Comparator.comparing(Student::getMarks)

);
```

Correct

Use the same Comparator for both sorting and searching.

---

# 📝 Quick Revision

## Linear Search

```java
for(int i = 0; i < arr.length; i++){

    if(arr[i] == key){

        return i;

    }

}

return -1;
```

---

## Binary Search

```java
while(low <= high){

    int mid = low + (high - low) / 2;

}
```

---

## Arrays.binarySearch()

```java
Arrays.binarySearch(

arr,

key

);
```

---

## Collections.binarySearch()

```java
Collections.binarySearch(

list,

key

);
```

---

## Search Objects

```java
Collections.binarySearch(

students,

target,

Comparator.comparing(

Student::getId

)

);
```

---

# 🎓 MCQs

### Q1. Which searching algorithm checks elements one by one?

- A. Binary Search
- B. Linear Search ✅
- C. Merge Search
- D. Quick Search

---

### Q2. Binary Search requires

- A. Random Data
- B. Sorted Data ✅
- C. Duplicate Data
- D. Tree Structure

---

### Q3. Worst-case complexity of Linear Search?

- A. O(1)
- B. O(log n)
- C. O(n) ✅
- D. O(n²)

---

### Q4. Worst-case complexity of Binary Search?

- A. O(1)
- B. O(log n) ✅
- C. O(n)
- D. O(n²)

---

### Q5. Which package contains Arrays.binarySearch()?

- A. java.io
- B. java.util.Arrays ✅
- C. java.lang
- D. java.sql

---

### Q6. Which package contains Collections.binarySearch()?

- A. java.util.Collections ✅
- B. java.lang
- C. java.sql
- D. java.io

---

### Q7. Binary Search repeatedly divides the array into

- A. Three Parts
- B. Two Halves ✅
- C. Four Parts
- D. Five Parts

---

### Q8. Which value indicates that the element was not found?

- A. 0
- B. -1
- C. Any Negative Value ✅
- D. 1

---

### Q9. Which search is better for large sorted datasets?

- A. Linear Search
- B. Binary Search ✅
- C. Sequential Search
- D. DFS

---

### Q10. Which algorithm is easier to implement?

- A. Binary Search
- B. Linear Search ✅
- C. Hash Search
- D. Tree Search

---

# 💻 Practice Problems

## Beginner

1. Implement Linear Search.
2. Implement Binary Search.
3. Search an element in an integer array.
4. Search an element in a string array.
5. Search an element in an `ArrayList`.

---

## Intermediate

6. Implement Recursive Binary Search.
7. Search a student by ID.
8. Search an employee by salary.
9. Use `Arrays.binarySearch()` on a sorted array.
10. Use `Collections.binarySearch()` on a sorted list.

---

## Advanced

11. Search objects using Comparator.
12. Search products by ID.
13. Search employees using Binary Search.
14. Build a Contact Search System.
15. Develop a Product Search Module for an E-Commerce application.

---

# 🌍 Real-World Applications

Searching is widely used in:

- Search Engines
- Banking Systems
- Student Management Systems
- Employee Databases
- Hospital Management Systems
- Airline Reservation Systems
- Library Management Systems
- Inventory Management
- E-Commerce Websites
- Spring Boot REST APIs

---

# 📚 References

- Oracle Java Documentation
- OpenJDK Documentation
- Effective Java – Joshua Bloch
- Java: The Complete Reference
- Head First Java
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **09-Searching.md**

### ✔️ Concepts Covered

- Introduction to Searching
- Linear Search
- Binary Search
- Iterative Binary Search
- Recursive Binary Search
- Arrays.binarySearch()
- Collections.binarySearch()
- Searching Objects
- Searching using Comparator
- Time Complexity Analysis
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Searching is used to locate elements efficiently in collections.
- ✅ Linear Search works on both sorted and unsorted data with **O(n)** complexity.
- ✅ Binary Search works only on sorted data with **O(log n)** complexity.
- ✅ Java provides `Arrays.binarySearch()` for arrays and `Collections.binarySearch()` for lists.
- ✅ Always use the same Comparator while sorting and searching objects.
- ✅ Binary Search is one of the most frequently asked algorithms in Java interviews.

---

# 🚀 Next Chapter

➡️ **10-Interview-Programs.md**

### Topics Covered

- Most Asked Java Coding Interview Programs
- Array-Based Programs
- String-Based Programs
- Number Programs
- Searching & Sorting Programs
- Object-Based Programs
- Frequently Asked Coding Questions
- Interview Tips
- MCQs
- Practice Problems