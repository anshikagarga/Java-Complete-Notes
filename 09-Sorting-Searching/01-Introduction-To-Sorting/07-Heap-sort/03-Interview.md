# 📘 Chapter 07: Heap Sort (Part 3)

## Comparison, Interview Questions, MCQs & Practice Problems

> *"Heap Sort guarantees **O(n log n)** time complexity in all cases while sorting the array in-place. Although it is not as fast as Quick Sort in practice, it is a reliable choice when worst-case performance matters."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Heap Sort with other sorting algorithms.
- Understand where Heap Sort should be used.
- Revise the complete Heap Sort chapter.
- Prepare for coding interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Heap Sort vs Quick Sort
2. Heap Sort vs Merge Sort
3. Heap Sort vs Selection Sort
4. Complete Complexity Comparison
5. Advantages & Disadvantages
6. Real-World Applications
7. Common Mistakes
8. Best Practices
9. Interview Questions
10. MCQs
11. Quick Revision
12. Practice Problems
13. Related Topics
14. References
15. Chapter Summary

---

# 📊 Heap Sort vs Quick Sort

| Feature | Heap Sort | Quick Sort |
|----------|-----------|------------|
| Technique | Binary Heap | Divide & Conquer |
| Stable | ❌ No | ❌ No |
| In-place | ✅ Yes | ✅ Yes |
| Best Case | O(n log n) | O(n log n) |
| Average Case | O(n log n) | O(n log n) |
| Worst Case | O(n log n) | O(n²) |
| Cache Performance | Poor | Excellent |
| Practical Speed | Moderate | Very Fast |

### Which is Better?

**Heap Sort**

- Guaranteed O(n log n)
- Better worst-case performance
- Suitable for memory-constrained systems

**Quick Sort**

- Faster in practice
- Better CPU cache utilization
- Preferred for array sorting

---

# 📊 Heap Sort vs Merge Sort

| Feature | Heap Sort | Merge Sort |
|----------|-----------|------------|
| Stable | ❌ No | ✅ Yes |
| In-place | ✅ Yes | ❌ No |
| Extra Space | O(1) | O(n) |
| Worst Case | O(n log n) | O(n log n) |
| Linked List Performance | Poor | Excellent |
| External Sorting | ❌ No | ✅ Yes |

Merge Sort is preferred when **stability** is required.

Heap Sort is preferred when **extra memory is limited**.

---

# 📊 Heap Sort vs Selection Sort

| Feature | Heap Sort | Selection Sort |
|----------|-----------|----------------|
| Best Case | O(n log n) | O(n²) |
| Average Case | O(n log n) | O(n²) |
| Worst Case | O(n log n) | O(n²) |
| Stable | ❌ No | ❌ No |
| In-place | ✅ Yes | ✅ Yes |
| Large Datasets | ✅ Excellent | ❌ Poor |

Heap Sort is significantly faster for large datasets.

---

# 📊 Complete Complexity Summary

| Property | Heap Sort |
|-----------|-----------|
| Best Case | O(n log n) |
| Average Case | O(n log n) |
| Worst Case | O(n log n) |
| Space Complexity | O(1) |
| Stable | ❌ No |
| In-place | ✅ Yes |
| Adaptive | ❌ No |
| Comparison Based | ✅ Yes |

---

# 🌍 Real-World Applications

Heap Sort is widely used in:

- Operating Systems
- CPU Scheduling
- Priority Queues
- Event Simulation
- Graph Algorithms
- Embedded Systems
- Real-Time Systems
- Memory-Constrained Applications

---

# 🌟 Where is Heap Sort Used?

Heap Sort is preferred when:

- Guaranteed worst-case performance is required.
- Extra memory is limited.
- Implementing Priority Queues.
- Working with scheduling algorithms.
- Solving graph problems such as Dijkstra's and Prim's algorithms (using heaps).

---

# ⚠️ Common Mistakes

## ❌ Wrong Heap Construction

Wrong

```java
for(int i = 0; i < n; i++)
```

Correct

```java
for(int i = n / 2 - 1; i >= 0; i--)
```

---

## ❌ Wrong Child Formula

Wrong

```java
left = 2 * i;
```

Correct

```java
left = 2 * i + 1;
```

Wrong

```java
right = 2 * i;
```

Correct

```java
right = 2 * i + 2;
```

---

## ❌ Forgetting to Reduce Heap Size

Wrong

```java
heapify(arr, n, 0);
```

Correct

```java
heapify(arr, i, 0);
```

---

## ❌ Ignoring Heapify After Swap

Wrong

```java
swap(root, last);
```

Correct

```java
swap(root, last);

heapify(arr, i, 0);
```

---

# 💡 Best Practices

- Practice Heapify separately before Heap Sort.
- Memorize parent and child index formulas.
- Draw the Heap as a tree during learning.
- Use Heap Sort when guaranteed worst-case performance is required.
- Use Priority Queue (`java.util.PriorityQueue`) when dynamic insertion and deletion are needed instead of implementing Heap manually.

---

# 🧩 Interview Questions

## Beginner

1. What is Heap Sort?
2. What is a Binary Heap?
3. What is the difference between Max Heap and Min Heap?
4. Why is Max Heap used for ascending order sorting?
5. What is Heapify?

---

## Intermediate

6. Why does Heap Construction take O(n)?
7. Why is Heap Sort not Stable?
8. Difference between Heap Sort and Quick Sort.
9. Difference between Heap Sort and Merge Sort.
10. Explain Heapify with an example.

---

## Advanced

11. Why is Heap Sort In-place?
12. Can Heap Sort be made Stable?
13. Why is Heap Sort slower than Quick Sort in practice?
14. Explain array representation of a Heap.
15. Why are Heaps used in Priority Queues?

---

# 🎓 MCQs

### Q1. Heap Sort uses which data structure?

- A. Stack
- B. Queue
- C. Binary Heap ✅
- D. Linked List

---

### Q2. Heap Sort is:

- A. Stable
- B. In-place ✅
- C. Adaptive
- D. Non-comparison Based

---

### Q3. Worst Case Time Complexity?

- A. O(n²)
- B. O(log n)
- C. O(n log n) ✅
- D. O(n)

---

### Q4. Which Heap is used for ascending order sorting?

- A. Min Heap
- B. Max Heap ✅
- C. Fibonacci Heap
- D. Binomial Heap

---

### Q5. Heap Construction starts from:

- A. Root Node
- B. First Leaf Node
- C. Last Non-Leaf Node ✅
- D. Last Element

---

# 📝 Quick Revision

## Flow

```text
Build Max Heap

↓

Swap Root with Last

↓

Reduce Heap Size

↓

Heapify

↓

Repeat

↓

Sorted Array
```

---

## Complexity

```text
Best

O(n log n)

↓

Average

O(n log n)

↓

Worst

O(n log n)
```

---

## Properties

```text
Stable

❌

In-place

✅

Adaptive

❌

Comparison Based

✅
```

---

## Core Idea

```text
Build Max Heap

↓

Largest Element at Root

↓

Move Largest to End

↓

Restore Heap

↓

Repeat

↓

Sorted Array
```

---

# 🧪 Practice Problems

## Beginner

- Implement Heap Sort.
- Build a Max Heap from an array.
- Convert a Max Heap into a Min Heap.
- Print the Heap after every Heapify operation.

---

## Intermediate

- Find the kth Largest Element using a Heap.
- Merge K Sorted Arrays using a Heap.
- Implement Priority Queue using a Binary Heap.
- Find the Top K Frequent Elements.

---

## Advanced

- Heap Sort using a Min Heap.
- Implement an Iterative Heapify.
- Design a Custom Heap.
- Median of a Data Stream.
- Sliding Window Maximum using a Heap.

---

# 🔗 Related Topics

- Binary Tree
- Complete Binary Tree
- Priority Queue
- Quick Sort
- Merge Sort
- Selection Sort
- Arrays.sort()
- Collections.sort()
- Comparable Interface
- Comparator Interface

---

# 📚 References

- Oracle Java Documentation
- Introduction to Algorithms (CLRS)
- Algorithms by Robert Sedgewick
- Data Structures and Algorithms in Java
- GeeksforGeeks
- LeetCode Explore

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 07: Heap Sort**.

### ✔️ Concepts Covered

- Introduction to Heap Sort
- Binary Heap
- Max Heap & Min Heap
- Heapify
- Heap Construction
- Dry Run
- Java Implementation
- Time & Space Complexity
- Heap Sort Comparisons
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Heap Sort uses a **Binary Heap** data structure.
- ✅ A **Max Heap** is used for ascending order sorting.
- ✅ Heapify restores the Heap property after every swap.
- ✅ Heap Sort guarantees **O(n log n)** time complexity in all cases.
- ✅ It is **In-place** but **not Stable**.
- ✅ Heap Sort is an excellent choice when worst-case performance guarantees are important and extra memory is limited.
- ✅ Understanding Heap Sort also helps in mastering **Priority Queues** and many graph algorithms.

---

# 🚀 Next Chapter

➡️ **08-Collections-Sort.md**

### Topics Covered

- What is `Collections.sort()`?
- How `Collections.sort()` Works Internally
- Sorting Lists
- Ascending & Descending Sorting
- Sorting Custom Objects
- Comparable Interface
- Comparator Interface
- Lambda Expressions
- Java 8+ Sorting Techniques
- Interview Questions
- Practice Problems