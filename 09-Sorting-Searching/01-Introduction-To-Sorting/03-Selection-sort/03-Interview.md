# 📘 Chapter 03: Selection Sort (Part 3)

## Comparison, Interview Questions, MCQs & Practice Problems

> *"Selection Sort is easy to understand and performs fewer swaps than Bubble Sort. Although it is not suitable for large datasets, it is an important algorithm for learning sorting concepts and interview preparation."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Selection Sort with other sorting algorithms.
- Understand where Selection Sort should be used.
- Revise the complete Selection Sort chapter.
- Prepare for coding interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Selection Sort vs Bubble Sort
2. Selection Sort vs Insertion Sort
3. Complete Complexity Comparison
4. Advantages & Disadvantages
5. Real-World Applications
6. Common Mistakes
7. Best Practices
8. Interview Questions
9. MCQs
10. Quick Revision
11. Practice Problems
12. Related Topics
13. References
14. Chapter Summary

---

# 📊 Selection Sort vs Bubble Sort

| Feature | Selection Sort | Bubble Sort |
|----------|----------------|-------------|
| Method | Select Minimum Element | Swap Adjacent Elements |
| Stable | ❌ No | ✅ Yes |
| In-place | ✅ Yes | ✅ Yes |
| Adaptive | ❌ No | ✅ Yes (Optimized) |
| Swaps | Very Few | Many |
| Best Case | O(n²) | O(n) |
| Average Case | O(n²) | O(n²) |
| Worst Case | O(n²) | O(n²) |

---

# 📊 Selection Sort vs Insertion Sort

| Feature | Selection Sort | Insertion Sort |
|----------|----------------|----------------|
| Stable | ❌ No | ✅ Yes |
| Adaptive | ❌ No | ✅ Yes |
| In-place | ✅ Yes | ✅ Yes |
| Best Case | O(n²) | O(n) |
| Average Case | O(n²) | O(n²) |
| Worst Case | O(n²) | O(n²) |
| Suitable for Nearly Sorted Data | ❌ | ✅ |

Insertion Sort performs much better on nearly sorted arrays.

---

# 📊 Selection Sort vs Merge Sort

| Feature | Selection Sort | Merge Sort |
|----------|----------------|------------|
| Best Case | O(n²) | O(n log n) |
| Average Case | O(n²) | O(n log n) |
| Worst Case | O(n²) | O(n log n) |
| Stable | ❌ | ✅ |
| In-place | ✅ | ❌ |
| Extra Memory | O(1) | O(n) |

Merge Sort is preferred for large datasets.

---

# 📊 Complete Complexity Summary

| Property | Selection Sort |
|-----------|----------------|
| Best Case | O(n²) |
| Average Case | O(n²) |
| Worst Case | O(n²) |
| Space Complexity | O(1) |
| Stable | ❌ No |
| In-place | ✅ Yes |
| Adaptive | ❌ No |
| Comparisons | O(n²) |
| Maximum Swaps | O(n) |

---

# 🌍 Real-World Applications

Selection Sort is useful for:

- Learning Sorting Algorithms
- Academic Projects
- Small Arrays
- Embedded Systems
- Situations where swapping is expensive
- Memory-constrained environments

---

# ⚠️ Common Mistakes

## ❌ Swapping During Every Comparison

Wrong

```java
if(arr[j] < arr[minIndex]){
    swap();
}
```

Correct

```java
Find minimum first

↓

Swap once
```

---

## ❌ Assuming Best Case is O(n)

Selection Sort always scans the remaining array.

Best Case is still

```text
O(n²)
```

---

## ❌ Forgetting to Update `minIndex`

Wrong

```java
if(arr[j] < arr[minIndex]){

}
```

Correct

```java
if(arr[j] < arr[minIndex]){

    minIndex = j;

}
```

---

## ❌ Assuming Selection Sort is Stable

Selection Sort is **Unstable** because swapping may change the order of duplicate elements.

---

# 💡 Best Practices

- Swap only once after each pass.
- Track the minimum element using its index.
- Use Selection Sort only for small datasets.
- Prefer Merge Sort or Quick Sort for large datasets.
- Remember that Selection Sort minimizes swaps but not comparisons.

---

# 🧩 Interview Questions

## Beginner

1. What is Selection Sort?
2. Why is it called Selection Sort?
3. Is Selection Sort Stable?
4. Is Selection Sort In-place?
5. What is its Time Complexity?

---

## Intermediate

6. Why is Selection Sort Unstable?
7. Why does Selection Sort perform fewer swaps?
8. Difference between Bubble Sort and Selection Sort.
9. Difference between Selection Sort and Insertion Sort.
10. Why isn't Selection Sort Adaptive?

---

## Advanced

11. Can Selection Sort be made Stable?
12. Why is Selection Sort preferred when swap operations are expensive?
13. Explain Selection Sort using an example.
14. Can Selection Sort be used for Linked Lists?
15. Why is Selection Sort not suitable for large datasets?

---

# 🎓 MCQs

### Q1. Selection Sort selects:

- A. Largest Element
- B. Random Element
- C. Smallest Element ✅
- D. Adjacent Element

---

### Q2. Selection Sort performs:

- A. Multiple Swaps per Pass
- B. One Swap per Pass ✅
- C. No Swaps
- D. Recursive Swaps

---

### Q3. Selection Sort is:

- A. Stable
- B. Adaptive
- C. In-place ✅
- D. Non-comparison Based

---

### Q4. Best Case Time Complexity is:

- A. O(n)
- B. O(log n)
- C. O(n²) ✅
- D. O(n log n)

---

### Q5. Which statement is correct?

- A. Selection Sort is Stable.
- B. Selection Sort is Adaptive.
- C. Selection Sort minimizes swaps. ✅
- D. Selection Sort uses extra arrays.

---

# 📝 Quick Revision

## Selection Sort Flow

```text
Start

↓

Assume First Element as Minimum

↓

Traverse Remaining Elements

↓

Update Minimum Index

↓

Swap Once

↓

Repeat

↓

Sorted Array
```

---

## Complexity

```text
Best

O(n²)

↓

Average

O(n²)

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

Comparison Based

✅
```

---

## Key Feature

```text
One Pass

↓

One Minimum Element Selected

↓

One Swap

↓

One Position Fixed
```

---

# 🧪 Practice Problems

## Beginner

- Implement Selection Sort.
- Sort an array in descending order.
- Print the array after every pass.
- Count the number of swaps.

---

## Intermediate

- Find the minimum element in each pass.
- Compare Bubble Sort and Selection Sort experimentally.
- Implement Selection Sort for strings.

---

## Advanced

- Make Selection Sort Stable.
- Implement Recursive Selection Sort.
- Sort custom objects using Selection Sort.
- Visualize Selection Sort step by step.

---

# 🔗 Related Topics

- Introduction to Sorting
- Bubble Sort
- Insertion Sort
- Merge Sort
- Quick Sort
- Arrays.sort()
- Collections.sort()
- Comparable Interface
- Comparator Interface

---

# 📚 References

- Oracle Java Documentation
- Introduction to Algorithms (CLRS)
- Data Structures and Algorithms in Java
- GeeksforGeeks
- LeetCode Explore

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 03: Selection Sort**.

### ✔️ Concepts Covered

- Selection Sort Introduction
- Algorithm
- Dry Run
- Java Implementation
- Stable vs Unstable
- In-place Sorting
- Time & Space Complexity
- Complexity Analysis
- Comparison with Other Algorithms
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Selection Sort repeatedly selects the **minimum element**.
- ✅ It performs only **one swap per pass**.
- ✅ Selection Sort is **In-place** but **Unstable**.
- ✅ Best, Average, and Worst Case Time Complexity are **O(n²)**.
- ✅ It minimizes swaps but not comparisons.
- ✅ Best suited for small datasets and educational purposes.

---

# 🚀 Next Chapter

➡️ **04-Insertion-Sort.md**

### Topics Covered

- What is Insertion Sort?
- Working Principle
- Dry Run
- Java Implementation
- Optimized Working
- Time & Space Complexity
- Stable vs Unstable
- Comparison with Bubble & Selection Sort
- Interview Questions
- Practice Problems