# 📘 Chapter 02: Arrays.sort() (Part 3)

## Interview Questions, MCQs, Practice Problems & Chapter Summary

> *"Arrays.sort() is one of the most frequently asked Java interview topics. Every Java developer should understand not only how to use it, but also how it works internally."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Revise Arrays.sort()
- Solve Interview Questions
- Practice MCQs
- Solve Coding Problems
- Understand Best Practices
- Revise Time Complexity

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

### Q1. What is Arrays.sort()?

**Answer**

`Arrays.sort()` is a static method of the `java.util.Arrays` class that sorts an array in ascending order.

---

### Q2. Which package contains Arrays.sort()?

**Answer**

```java
java.util
```

---

### Q3. Can Arrays.sort() sort String arrays?

**Answer**

Yes.

Example

```java
String[] names = {

    "Java",

    "Python",

    "C"

};

Arrays.sort(names);
```

---

### Q4. Does Arrays.sort() modify the original array?

**Answer**

Yes.

It sorts the original array itself.

---

### Q5. Can Arrays.sort() sort partially?

**Answer**

Yes.

Example

```java
Arrays.sort(arr, 2, 6);
```

---

# 🎤 Intermediate Questions

### Q6. Which algorithm is used internally?

**Answer**

| Array Type | Algorithm |
|------------|-----------|
| Primitive Arrays | Dual-Pivot QuickSort |
| Object Arrays | TimSort |

---

### Q7. Difference between Arrays.sort() and Collections.sort()

| Arrays.sort() | Collections.sort() |
|---------------|--------------------|
| Works on arrays | Works on List |
| Static method | Static method of Collections class |
| java.util.Arrays | java.util.Collections |

---

### Q8. Why can't reverseOrder() work with int[]?

**Answer**

Because `Collections.reverseOrder()` requires objects.

Correct

```java
Integer[] arr = {10,20,30};

Arrays.sort(arr, Collections.reverseOrder());
```

Wrong

```java
int[] arr = {10,20,30};
```

Primitive types cannot be used with Comparators.

---

### Q9. Is Arrays.sort() stable?

**Answer**

- Primitive Arrays → ❌ No
- Object Arrays (TimSort) → ✅ Yes

---

### Q10. Time Complexity of Arrays.sort()?

Primitive Arrays

```
Average : O(n log n)

Worst : O(n²)
```

Object Arrays

```
Average : O(n log n)

Worst : O(n log n)
```

---

# 💡 Best Practices

✔ Use Arrays.sort() instead of writing sorting algorithms manually.

✔ Use Integer[] when custom sorting is required.

✔ Use Arrays.binarySearch() after sorting.

✔ Import java.util.Arrays.

✔ Use Arrays.toString() for printing arrays.

---

# ⚠️ Common Mistakes

## ❌ Printing Array Directly

Wrong

```java
System.out.println(arr);
```

Output

```text
[I@36baf30c
```

Correct

```java
System.out.println(Arrays.toString(arr));
```

---

## ❌ Using reverseOrder() with int[]

Wrong

```java
int[] arr = {4,2,1};

Arrays.sort(arr, Collections.reverseOrder());
```

Correct

```java
Integer[] arr = {4,2,1};

Arrays.sort(arr, Collections.reverseOrder());
```

---

## ❌ Forgetting Import

Wrong

```java
Arrays.sort(arr);
```

Correct

```java
import java.util.Arrays;
```

---

# 📝 Quick Revision

## Sort Integer Array

```java
Arrays.sort(arr);
```

---

## Sort String Array

```java
Arrays.sort(names);
```

---

## Partial Sorting

```java
Arrays.sort(arr,1,5);
```

---

## Descending Order

```java
Arrays.sort(arr,

Collections.reverseOrder());
```

---

## Print Array

```java
System.out.println(

Arrays.toString(arr)

);
```

---

# 🎓 MCQs

### Q1. Arrays.sort() belongs to?

- A. Collections
- B. Arrays ✅
- C. ArrayList
- D. List

---

### Q2. Package of Arrays?

- A. java.lang
- B. java.io
- C. java.util ✅
- D. java.sql

---

### Q3. Arrays.sort() returns

- A. New Array
- B. Boolean
- C. void ✅
- D. Object

---

### Q4. Which algorithm is used for Object Arrays?

- A. Merge Sort
- B. TimSort ✅
- C. Bubble Sort
- D. Heap Sort

---

### Q5. Which method prints an array?

- A. print()
- B. Arrays.toString() ✅
- C. display()
- D. show()

---

### Q6. Which algorithm is used for Primitive Arrays?

- A. Merge Sort
- B. Bubble Sort
- C. Dual-Pivot QuickSort ✅
- D. TimSort

---

### Q7. reverseOrder() works with

- A. int[]
- B. char[]
- C. Integer[] ✅
- D. float[]

---

### Q8. Arrays.sort() is

- A. Instance Method
- B. Constructor
- C. Static Method ✅
- D. Abstract Method

---

### Q9. Arrays.sort() sorts by default in

- A. Descending
- B. Random
- C. Ascending ✅
- D. None

---

### Q10. Arrays.sort() modifies

- A. New Array
- B. Original Array ✅
- C. Copy
- D. None

---

# 💻 Practice Problems

## Beginner

1. Sort an integer array.
2. Sort a character array.
3. Sort a string array.
4. Sort a double array.
5. Print the sorted array.

---

## Intermediate

6. Sort only part of an array.
7. Sort an Integer array in descending order.
8. Find the largest element after sorting.
9. Find the smallest element after sorting.
10. Remove duplicates after sorting.

---

## Advanced

11. Sort employee IDs.
12. Sort product prices.
13. Sort marks of students.
14. Sort names ignoring case.
15. Sort a custom object using a Comparator (covered in later chapters).

---

# 🌍 Real-World Applications

`Arrays.sort()` is used in:

- Banking Systems
- Student Management
- Employee Management
- E-commerce Applications
- Data Analytics
- Inventory Systems
- Search Optimization
- Competitive Programming

---

# 📚 References

- Oracle Java Documentation
- OpenJDK Source Code
- Effective Java – Joshua Bloch
- Java: The Complete Reference
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **02-Arrays.sort().md**

### ✔️ Concepts Covered

- Arrays.sort()
- Sorting Primitive Arrays
- Sorting Object Arrays
- Partial Sorting
- Descending Order
- Internal Algorithms
- Time Complexity
- Best Practices
- Common Mistakes
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ `Arrays.sort()` is the standard way to sort arrays in Java.
- ✅ It sorts primitive arrays in ascending order using **Dual-Pivot QuickSort**.
- ✅ It sorts object arrays using **TimSort**, which is stable.
- ✅ Use `Collections.reverseOrder()` with object arrays like `Integer[]` for descending order.
- ✅ Use `Arrays.toString()` to print arrays in a readable format.
- ✅ Prefer built-in sorting methods over manually implementing sorting algorithms in production code.

---

# 🚀 Next Chapter

➡️ **03-Collections.sort().md**

### Topics Covered

- Introduction to Collections.sort()
- Sorting Lists
- Sorting ArrayList
- Sorting LinkedList
- Ascending & Descending Order
- Collections.reverseOrder()
- Time Complexity
- Interview Questions
- MCQs
- Practice Problems