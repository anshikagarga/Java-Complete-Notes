# 📘 Chapter 06: Quick Sort (Part 3)

## Comparison, Interview Questions, MCQs & Practice Problems

> *"Quick Sort is one of the fastest sorting algorithms in practice. Although its worst-case complexity is **O(n²)**, its average performance, in-place nature, and cache efficiency make it the preferred choice for sorting arrays in many real-world applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Quick Sort with other sorting algorithms.
- Understand where Quick Sort should be used.
- Revise the complete Quick Sort chapter.
- Prepare for coding interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Quick Sort vs Merge Sort
2. Quick Sort vs Heap Sort
3. Quick Sort vs Insertion Sort
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

# 📊 Quick Sort vs Merge Sort

| Feature | Quick Sort | Merge Sort |
|----------|------------|------------|
| Technique | Divide & Conquer | Divide & Conquer |
| Stable | ❌ No | ✅ Yes |
| In-place | ✅ Yes | ❌ No |
| Best Case | O(n log n) | O(n log n) |
| Average Case | O(n log n) | O(n log n) |
| Worst Case | O(n²) | O(n log n) |
| Extra Space | O(log n) | O(n) |

### Which is Better?

**Quick Sort**

- Faster for arrays
- Better cache performance
- Uses less memory

**Merge Sort**

- Stable sorting
- Better for Linked Lists
- Guaranteed O(n log n)

---

# 📊 Quick Sort vs Heap Sort

| Feature | Quick Sort | Heap Sort |
|----------|------------|-----------|
| Stable | ❌ No | ❌ No |
| In-place | ✅ Yes | ✅ Yes |
| Best Case | O(n log n) | O(n log n) |
| Average Case | O(n log n) | O(n log n) |
| Worst Case | O(n²) | O(n log n) |
| Cache Performance | Excellent | Poor |

Heap Sort guarantees O(n log n), but Quick Sort is generally faster in practice.

---

# 📊 Quick Sort vs Insertion Sort

| Feature | Quick Sort | Insertion Sort |
|----------|------------|----------------|
| Best Case | O(n log n) | O(n) |
| Average Case | O(n log n) | O(n²) |
| Worst Case | O(n²) | O(n²) |
| Stable | ❌ No | ✅ Yes |
| Adaptive | ❌ No | ✅ Yes |
| Large Arrays | ✅ Excellent | ❌ Poor |
| Nearly Sorted Arrays | ❌ Good | ✅ Excellent |

---

# 📊 Complete Complexity Summary

| Property | Quick Sort |
|-----------|------------|
| Best Case | O(n log n) |
| Average Case | O(n log n) |
| Worst Case | O(n²) |
| Space Complexity | O(log n) Average |
| Stable | ❌ No |
| In-place | ✅ Yes |
| Adaptive | ❌ No |
| Recursive | ✅ Yes |

---

# 🌍 Real-World Applications

Quick Sort is widely used in:

- Database Systems
- Search Engines
- Operating Systems
- Competitive Programming
- Standard Library Implementations
- Large In-Memory Arrays
- Analytics Applications
- Game Development

---

# 🌟 Why is Quick Sort So Popular?

Quick Sort is preferred because:

- Very fast average performance.
- Requires little extra memory.
- Excellent CPU cache utilization.
- Easy to optimize.
- Performs well for large datasets stored in memory.

---

# ⚠️ Common Mistakes

## ❌ Wrong Base Condition

Wrong

```java
if(low == high)
```

Correct

```java
if(low < high)
```

---

## ❌ Incorrect Pivot Placement

Always return the correct pivot index after partitioning.

Wrong

```java
return high;
```

Correct

```java
return i + 1;
```

---

## ❌ Wrong Recursive Calls

Wrong

```java
quickSort(low, pivot);
```

Correct

```java
quickSort(low, pivotIndex - 1);

quickSort(pivotIndex + 1, high);
```

---

## ❌ Ignoring Worst Case

Choosing the first or last element as pivot on an already sorted array can lead to:

```text
O(n²)
```

Use:

- Random Pivot
- Median of Three

to reduce the chances of worst-case performance.

---

# 💡 Best Practices

- Learn Lomuto and Hoare partition schemes.
- Prefer randomized pivot selection.
- Draw recursion trees while practicing.
- Understand partitioning before memorizing code.
- Use Quick Sort for arrays stored in memory.
- Use Merge Sort when stability is required.

---

# 🧩 Interview Questions

## Beginner

1. What is Quick Sort?
2. Why is Quick Sort called a Divide and Conquer algorithm?
3. What is a Pivot?
4. Is Quick Sort Stable?
5. Is Quick Sort In-place?

---

## Intermediate

6. Explain the Partition Algorithm.
7. Difference between Lomuto and Hoare Partition.
8. Difference between Merge Sort and Quick Sort.
9. Why is Quick Sort faster in practice?
10. What causes the worst case?

---

## Advanced

11. How does Randomized Quick Sort improve performance?
12. Explain Median of Three Pivot Selection.
13. Why is Quick Sort cache-friendly?
14. Can Quick Sort be made Stable?
15. Explain the recursion tree for Quick Sort.

---

# 🎓 MCQs

### Q1. Quick Sort follows which technique?

- A. Greedy
- B. Divide and Conquer ✅
- C. Dynamic Programming
- D. Backtracking

---

### Q2. Quick Sort is:

- A. Stable
- B. In-place ✅
- C. Non-comparison Based
- D. Adaptive

---

### Q3. Average Case Time Complexity?

- A. O(n²)
- B. O(log n)
- C. O(n log n) ✅
- D. O(n)

---

### Q4. Worst Case occurs when:

- A. Pivot always divides equally
- B. Pivot is always smallest or largest ✅
- C. Array is random
- D. Array contains duplicates

---

### Q5. Which Pivot Selection helps reduce the Worst Case?

- A. Random Pivot ✅
- B. Fixed First Element
- C. Fixed Last Element
- D. None

---

# 📝 Quick Revision

## Flow

```text
Choose Pivot

↓

Partition

↓

Pivot at Correct Position

↓

Sort Left

↓

Sort Right

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

O(n²)
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

Divide & Conquer

✅
```

---

## Core Idea

```text
Choose Pivot

↓

Partition Around Pivot

↓

Recursively Sort Left

↓

Recursively Sort Right

↓

Sorted Array
```

---

# 🧪 Practice Problems

## Beginner

- Implement Quick Sort using Lomuto Partition.
- Implement Quick Sort using Hoare Partition.
- Sort an array in descending order.
- Print the array after every partition.

---

## Intermediate

- Randomized Quick Sort.
- Find the kth smallest element using Quick Select.
- Sort strings using Quick Sort.
- Count recursive calls.

---

## Advanced

- Dual Pivot Quick Sort.
- Three-Way Quick Sort (Dutch National Flag).
- Iterative Quick Sort using Stack.
- Parallel Quick Sort.
- Stable Quick Sort implementation.

---

# 🔗 Related Topics

- Divide and Conquer
- Merge Sort
- Heap Sort
- Insertion Sort
- Binary Search
- Recursion
- Arrays.sort()
- Collections.sort()
- Comparable Interface
- Comparator Interface

---

# 📚 References

- Oracle Java Documentation
- Introduction to Algorithms (CLRS)
- Algorithms by Robert Sedgewick
- GeeksforGeeks
- LeetCode Explore

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 06: Quick Sort**.

### ✔️ Concepts Covered

- Introduction to Quick Sort
- Pivot Selection
- Partition Algorithms
- Lomuto Partition
- Hoare Partition
- Dry Run
- Java Implementation
- Recursion
- Stable vs Unstable
- Time & Space Complexity
- Comparisons
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Quick Sort follows the **Divide and Conquer** approach.
- ✅ It partitions the array around a **Pivot** element.
- ✅ Average Time Complexity is **O(n log n)**.
- ✅ Worst Case Time Complexity is **O(n²)**.
- ✅ It is **In-place** but **not Stable**.
- ✅ Choosing a good pivot is crucial for performance.
- ✅ Quick Sort is one of the fastest algorithms for sorting arrays in real-world applications.

---

# 🚀 Next Chapter

➡️ **07-Heap-Sort.md**

### Topics Covered

- What is Heap Sort?
- Binary Heap
- Max Heap & Min Heap
- Heapify Algorithm
- Heap Construction
- Dry Run
- Java Implementation
- Time & Space Complexity
- Interview Questions
- Practice Problems