# 📘 Chapter 07: Heap Sort (Part 2)

## Heapify, Heap Construction & Complexity Analysis

> *"Heap Sort is built upon one important operation called **Heapify**. Understanding Heapify is the key to mastering Heap Sort because every sorting step depends on restoring the Heap property after removing the largest element."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Heapify thoroughly.
- Learn how a Heap is constructed.
- Understand Heap Construction step by step.
- Learn why Heap Sort is not Stable.
- Analyze Time & Space Complexity.
- Understand Internal Working.
- Learn common mistakes and best practices.

---

# 📚 Table of Contents

1. Heapify Explained
2. Building a Max Heap
3. Heap Construction Dry Run
4. Stable vs Unstable
5. Time Complexity Analysis
6. Space Complexity
7. Internal Working
8. Memory Diagram
9. Real-World Applications
10. Common Mistakes
11. Best Practices

---

# 📖 What is Heapify?

Heapify is the process of restoring the **Heap Property**.

Whenever a node violates the Heap Property,

Heapify compares it with its children.

If necessary,

it swaps the node with the largest child.

This process continues until the subtree becomes a valid Heap.

---

## Example

Before Heapify

```text
        10

      /    \

     25     20
```

Heap Property Violated

Because

```text
10 < 25
```

---

After Heapify

```text
        25

      /    \

     10     20
```

Now,

Parent

```text
25
```

is greater than both children.

---

# 📖 Heapify Algorithm

For every node,

1. Assume the current node is the largest.
2. Compare it with the left child.
3. Compare it with the right child.
4. Find the largest among them.
5. Swap if required.
6. Repeat recursively.

---

# 🧠 Heapify Dry Run

Given

```text
Array

12 11 13 5 6 7
```

Tree

```text
        12

      /    \

    11      13

   / \      /

  5   6    7
```

Current Root

```text
12
```

Largest Child

```text
13
```

Swap

↓

```text
        13

      /    \

    11      12

   / \      /

  5   6    7
```

Heap Property Restored.

---

# 📖 Building a Max Heap

Heap construction begins from the **last non-leaf node**.

Formula

```text
Last Non-Leaf Node

↓

(n / 2) - 1
```

For

```text
n = 6
```

```text
(6 / 2) - 1

↓

2
```

So Heapify starts from index **2**.

---

# 📖 Why Start from the Last Non-Leaf Node?

Leaf nodes already satisfy the Heap Property because they have no children.

Therefore,

only non-leaf nodes need Heapify.

This makes Heap construction much faster.

---

# 🧠 Heap Construction Dry Run

Array

```text
12 11 13 5 6 7
```

---

Heapify Index

```text
2
```

Tree

```text
13

↓

Already Largest
```

No changes.

---

Heapify Index

```text
1
```

```text
11

Children

5

6
```

Already Largest.

---

Heapify Index

```text
0
```

```text
12

Children

11

13
```

Swap

↓

```text
13 11 12 5 6 7
```

Heap Built Successfully.

---

# 📖 Is Heap Sort Stable?

**No.**

Heap Sort is an **Unstable Sorting Algorithm**.

Swapping the root with the last element may change the relative order of duplicate elements.

---

## Example

Before Sorting

```text
50(A)

20

50(B)

10
```

After Heap Sort

```text
10

20

50(B)

50(A)
```

Notice

```text
50(A)
```

and

```text
50(B)
```

changed their original order.

---

# 📖 Is Heap Sort In-place?

**Yes.**

Heap Sort performs sorting inside the original array.

No extra array is required.

Only a few temporary variables are used.

Space Complexity

```text
O(1)
```

---

# 📊 Time Complexity Analysis

Heap Sort has two phases.

---

## Phase 1

Build Heap

Time Complexity

```text
O(n)
```

Although Heapify itself is **O(log n)**,

building the entire heap takes **O(n)** due to the way Heapify is applied from the bottom up.

---

## Phase 2

Remove Maximum Element

There are

```text
n - 1
```

removals.

Each removal requires Heapify.

Each Heapify

↓

```text
O(log n)
```

Total

```text
O(n log n)
```

---

## Final Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n log n) |
| Average | O(n log n) |
| Worst | O(n log n) |

Heap Sort always performs consistently.

---

# 📊 Space Complexity

| Complexity | Value |
|------------|-------|
| Auxiliary Space | O(1) |

Heap Sort is an **In-place Sorting Algorithm**.

---

# 🧠 Internal Working

```text
Array

↓

Build Max Heap

↓

Largest Element at Root

↓

Swap Root & Last Element

↓

Reduce Heap Size

↓

Heapify Again

↓

Repeat

↓

Sorted Array
```

---

# 📦 Memory Diagram

Original

```text
12

11

13

5

6

7
```

↓

Build Heap

```text
13

11

12

5

6

7
```

↓

Swap Root

```text
7

11

12

5

6

13
```

↓

Heapify

```text
12

11

7

5

6

13
```

↓

Repeat

↓

Sorted Array

```text
5

6

7

11

12

13
```

---

# 🌍 Real-World Applications

Heap Sort is commonly used in:

- Priority Queues
- CPU Scheduling
- Operating Systems
- Event Simulation
- Embedded Systems
- Memory-Constrained Applications
- Graph Algorithms (Dijkstra, Prim)

---

# ⚠️ Common Mistakes

## ❌ Wrong Child Index

Wrong

```java
left = 2 * i;
```

Correct

```java
left = 2 * i + 1;
```

---

Wrong

```java
right = 2 * i;
```

Correct

```java
right = 2 * i + 2;
```

---

## ❌ Starting Heap Construction from Wrong Index

Wrong

```java
for(int i = 0; i < n; i++)
```

Correct

```java
for(int i = n/2 - 1; i >= 0; i--)
```

---

## ❌ Forgetting Recursive Heapify

Wrong

```java
swap();
```

Correct

```java
heapify(arr, n, largest);
```

---

## ❌ Not Reducing Heap Size

Wrong

```java
heapify(arr, n, 0);
```

Correct

```java
heapify(arr, i, 0);
```

Here, `i` represents the current heap size after removing the largest element.

---

# 💡 Best Practices

- Learn the array representation of a Heap.
- Remember the formulas for parent and child indices.
- Always build the Heap from the last non-leaf node.
- Practice Heapify separately before learning Heap Sort.
- Draw Heap trees while solving problems.

---

# 🎯 Interview Tip

### Question

Why does Heap Construction take **O(n)** instead of **O(n log n)**?

### Answer

Although a single Heapify operation takes **O(log n)** in the worst case, most nodes in a heap are near the bottom and require very little work. Since Heapify is applied from the bottom up, the total work across all nodes adds up to **O(n)**, not **O(n log n)**.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Heap Sort vs Quick Sort
- Heap Sort vs Merge Sort
- Heap Sort vs Selection Sort
- Complete Comparison Table
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision Sheet
- Chapter Summary
- Frequently Asked Interview Questions