# 📘 Chapter 01: Introduction to Sorting (Part 2)

## Stable Sorting, In-place Sorting, Classification & Complexity

> *"Not all sorting algorithms are the same. Some preserve the order of duplicate elements, some require extra memory, while others are optimized for speed. Understanding these differences helps you choose the right algorithm for the right problem."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Stable and Unstable Sorting.
- Learn In-place and Out-of-place Sorting.
- Differentiate Comparison-based and Non-comparison Sorting.
- Understand Time Complexity.
- Understand Space Complexity.
- Learn how to choose the appropriate sorting algorithm.

---

# 📚 Table of Contents

1. Stable Sorting
2. Unstable Sorting
3. In-place Sorting
4. Out-of-place Sorting
5. Comparison-based Sorting
6. Non-comparison Sorting
7. Time Complexity
8. Space Complexity
9. Sorting Classification
10. Real-World Examples
11. Common Mistakes
12. Best Practices

---

# 📖 What is Stable Sorting?

A sorting algorithm is called **Stable** if it preserves the relative order of elements having the same value.

---

## Example

Before Sorting

```text
Marks

85(A)

70

85(B)

90
```

After Stable Sorting

```text
70

85(A)

85(B)

90
```

Notice that **85(A)** remains before **85(B)**.

Their original order is preserved.

---

# 📖 What is Unstable Sorting?

An unstable sorting algorithm does **not** guarantee the original order of duplicate elements.

Example

Before Sorting

```text
85(A)

70

85(B)

90
```

Possible Output

```text
70

85(B)

85(A)

90
```

The duplicate elements changed their order.

---

# 📊 Stable vs Unstable Sorting

| Feature | Stable | Unstable |
|----------|---------|----------|
| Duplicate Order Preserved | ✅ Yes | ❌ No |
| Preferred For Records | ✅ Yes | Sometimes |
| Example | Merge Sort | Quick Sort |

---

# 📖 In-place Sorting

An **In-place Sorting Algorithm** sorts the data **without requiring significant extra memory**.

Only a small amount of additional space is used.

Examples

- Bubble Sort
- Selection Sort
- Insertion Sort
- Heap Sort
- Quick Sort

---

## Memory Diagram

```text
Original Array

↓

Sorting Happens

↓

Same Array Gets Modified
```

No extra array is created.

---

# 📖 Out-of-place Sorting

An **Out-of-place Sorting Algorithm** uses additional memory while sorting.

Example

Merge Sort

```text
Original Array

↓

Temporary Array

↓

Sorted Array
```

Extra memory improves efficiency for certain algorithms.

---

# 📊 In-place vs Out-of-place

| Feature | In-place | Out-of-place |
|----------|----------|--------------|
| Extra Memory | Very Less | Additional Memory |
| Faster Memory Usage | ✅ Yes | ❌ No |
| Examples | Bubble, Quick | Merge, Counting |

---

# 📖 Comparison-based Sorting

These algorithms compare elements to determine their correct position.

Example

```text
40 > 20

Yes

↓

Swap
```

Examples

- Bubble Sort
- Selection Sort
- Insertion Sort
- Merge Sort
- Heap Sort
- Quick Sort

---

# 📖 Non-comparison Sorting

These algorithms do not compare elements directly.

Instead, they use mathematical properties such as digits, ranges, or frequencies.

Examples

- Counting Sort
- Radix Sort
- Bucket Sort

---

# 📊 Comparison-based vs Non-comparison

| Feature | Comparison | Non-comparison |
|----------|------------|----------------|
| Uses Comparisons | ✅ Yes | ❌ No |
| Can Sort Any Comparable Data | ✅ Yes | Limited |
| Examples | Quick, Merge | Counting, Radix |

---

# 📖 Time Complexity

Time Complexity tells us how the running time changes as the input size increases.

Suppose

```text
10 Elements
```

takes

```text
1 ms
```

then

```text
100000 Elements
```

will take much more time.

We use **Big O Notation** to describe this growth.

Common complexities:

| Complexity | Performance |
|------------|-------------|
| O(1) | Excellent |
| O(log n) | Very Fast |
| O(n) | Good |
| O(n log n) | Efficient |
| O(n²) | Slow for Large Data |

---

# 📖 Space Complexity

Space Complexity measures the additional memory required by an algorithm.

Example

Bubble Sort

```text
Extra Memory = O(1)
```

Merge Sort

```text
Extra Memory = O(n)
```

---

# 📦 Classification of Sorting Algorithms

```text
Sorting

│

├── Comparison Based

│      ├── Bubble Sort

│      ├── Selection Sort

│      ├── Insertion Sort

│      ├── Merge Sort

│      ├── Heap Sort

│      └── Quick Sort

│

└── Non-comparison Based

       ├── Counting Sort

       ├── Radix Sort

       └── Bucket Sort
```

---

# 🚀 Real-World Examples

### 📚 School Result

Students having the same marks should remain in their original order.

A **Stable Sorting Algorithm** is preferred.

---

### 🛒 E-commerce Website

Products sorted by:

- Price
- Rating
- Popularity

Often uses optimized sorting algorithms.

---

### 🏦 Banking Systems

Transactions are arranged by:

- Date
- Time
- Transaction ID

Maintaining order is important.

---

# ⚠️ Common Mistakes

## ❌ Thinking Every Sorting Algorithm is Stable

Wrong.

Quick Sort and Heap Sort are generally unstable.

---

## ❌ Ignoring Space Complexity

Sometimes an algorithm is fast but requires large extra memory.

Always consider both time and space.

---

## ❌ Using O(n²) Sorting for Huge Data

Algorithms like Bubble Sort become inefficient for large datasets.

Prefer O(n log n) algorithms like Merge Sort or Quick Sort.

---

# 💡 Best Practices

- Use Stable Sorting when duplicate order matters.
- Use In-place Sorting when memory is limited.
- Prefer Merge Sort for linked lists.
- Prefer Quick Sort for arrays in most practical cases.
- Use Counting or Radix Sort only when their input constraints are suitable.
- Learn both Time Complexity and Space Complexity before choosing an algorithm.

---

# 🎯 Interview Tip

### Question

What is the difference between Stable and Unstable Sorting?

### Answer

A Stable Sorting Algorithm preserves the relative order of equal elements after sorting, whereas an Unstable Sorting Algorithm may change their original order.

Example:

Merge Sort is Stable.

Quick Sort is generally Unstable.

---

➡️ **Next: Part 3** will cover:

- Complete Time Complexity Comparison
- Which Sorting Algorithm Should You Choose?
- Decision Tree for Selecting Algorithms
- Interview Questions (Basic → Advanced)
- MCQs
- Practice Problems
- Chapter Summary
- Quick Revision Sheet