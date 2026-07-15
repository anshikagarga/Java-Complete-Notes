# 📘 Chapter 06: Quick Sort (Part 2)

## Partition Algorithms, Stability & Complexity Analysis

> *"The efficiency of Quick Sort mainly depends on how the pivot is selected and how the partitioning is performed. A good pivot leads to balanced partitions and excellent performance."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Partition process deeply.
- Learn Lomuto Partition Scheme.
- Learn Hoare Partition Scheme.
- Understand Stable vs Unstable sorting.
- Analyze Time & Space Complexity.
- Understand the Recursion Tree.
- Learn common mistakes and best practices.

---

# 📚 Table of Contents

1. Partition Algorithm
2. Lomuto Partition
3. Hoare Partition
4. Stable vs Unstable
5. Time Complexity Analysis
6. Space Complexity
7. Recursion Tree
8. Internal Working
9. Memory Diagram
10. Common Mistakes
11. Best Practices

---

# 📖 What is Partitioning?

Partitioning is the heart of Quick Sort.

Its purpose is to place the **pivot element** at its correct sorted position.

After partitioning,

- All elements smaller than the pivot are on the left.
- All elements greater than the pivot are on the right.

Example

```text
Before

8 4 7 9 3 10 5

Pivot = 5
```

After Partition

```text
4 3 5 8 9 10 7
```

Notice

```text
Left Side

↓

4 3
```

```text
Pivot

↓

5
```

```text
Right Side

↓

8 9 10 7
```

---

# 📖 Lomuto Partition Scheme

Lomuto Partition is the most common implementation used in coding interviews.

### Steps

1. Choose the last element as the pivot.
2. Maintain an index `i` for smaller elements.
3. Traverse the array using `j`.
4. If `arr[j] < pivot`, swap `arr[i]` and `arr[j]`.
5. Finally, place the pivot at index `i + 1`.

---

## Example

Array

```text
5 2 8 1 7
```

Pivot

```text
7
```

Traversal

```text
5 < 7

↓

Swap
```

```text
2 < 7

↓

Swap
```

```text
8 > 7

↓

Ignore
```

```text
1 < 7

↓

Swap
```

Final Swap

```text
5 2 1 7 8
```

---

# 💻 Lomuto Partition Code

```java
public static int partition(int[] arr, int low, int high){

    int pivot = arr[high];

    int i = low - 1;

    for(int j = low; j < high; j++){

        if(arr[j] < pivot){

            i++;

            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;

        }

    }

    int temp = arr[i + 1];
    arr[i + 1] = arr[high];
    arr[high] = temp;

    return i + 1;

}
```

---

# 📖 Hoare Partition Scheme

Hoare Partition was introduced by **Tony Hoare**, the inventor of Quick Sort.

Instead of placing the pivot directly,

it uses two pointers.

```text
Left Pointer

↓

Moves Right
```

```text
Right Pointer

↓

Moves Left
```

When both pointers stop,

their elements are swapped.

---

## Example

```text
7 2 1 6 8 5 3 4
```

Pivot

```text
7
```

Left Pointer

```text
→
```

Right Pointer

```text
←
```

After partitioning,

smaller elements remain on the left,

larger elements remain on the right.

The pivot is **not necessarily** at its final sorted position after one partition.

---

# 📊 Lomuto vs Hoare Partition

| Feature | Lomuto | Hoare |
|----------|---------|--------|
| Pivot | Last Element | Usually First Element |
| Swaps | More | Fewer |
| Simplicity | Easy | Slightly Complex |
| Interview Usage | Very Common | Common |
| Performance | Good | Better |

---

# 📖 Is Quick Sort Stable?

**No.**

Quick Sort is an **Unstable Sorting Algorithm**.

Equal elements may change their original order after swapping.

---

## Example

Before Sorting

```text
40(A)

20

40(B)

10
```

After Sorting

```text
10

20

40(B)

40(A)
```

Notice

```text
40(A)
```

and

```text
40(B)
```

have changed their order.

---

# 📖 Is Quick Sort In-place?

**Yes.**

Quick Sort sorts the array inside the original memory.

It does not create another array for sorting.

Only recursion stack memory is used.

---

# 📊 Time Complexity Analysis

## Best Case

Pivot divides the array into two equal halves.

```text
n

↓

n/2

↓

n/4

↓

...
```

Number of Levels

```text
log₂ n
```

Work at each level

```text
n
```

Total

```text
O(n log n)
```

---

## Average Case

Random pivot usually creates balanced partitions.

Time Complexity

```text
O(n log n)
```

---

## Worst Case

Occurs when the pivot is always the smallest or largest element.

Example

```text
1 2 3 4 5
```

Choosing the last element as pivot every time results in:

```text
n

↓

n-1

↓

n-2

↓

...
```

Time Complexity

```text
O(n²)
```

---

# 📊 Space Complexity

| Case | Complexity |
|------|------------|
| Average | O(log n) |
| Worst | O(n) |

The extra space is used only by the recursion stack.

---

# 🌳 Recursion Tree (Balanced Case)

```text
                [8 4 7 9 3 10 5]

               /               \

           Smaller           Larger

          /      \          /      \

      Smaller  Larger   Smaller  Larger

          ...

        Until One Element
```

---

# 🧠 Internal Working

```text
Choose Pivot

↓

Partition Array

↓

Pivot Positioned

↓

Sort Left Half

↓

Sort Right Half

↓

Repeat

↓

Sorted Array
```

---

# 📦 Memory Diagram

Original

```text
5

2

8

1

7
```

↓

Partition

```text
5

2

1

7

8
```

↓

Recursive Calls

```text
1

2

5

7

8
```

---

# ⚠️ Common Mistakes

## ❌ Wrong Base Case

Wrong

```java
if(low == high)
```

Correct

```java
if(low < high)
```

---

## ❌ Choosing a Poor Pivot

Always selecting the smallest or largest element can lead to:

```text
O(n²)
```

---

## ❌ Incorrect Partition Logic

Wrong

```java
if(arr[j] <= pivot)
```

Correct

```java
if(arr[j] < pivot)
```

---

## ❌ Forgetting Recursive Calls

Wrong

```java
partition(...);
```

Correct

```java
quickSort(left);

quickSort(right);
```

---

# 💡 Best Practices

- Use randomized pivot selection for better average performance.
- Learn both Lomuto and Hoare partition schemes.
- Always draw the recursion tree while learning.
- Use Quick Sort for in-memory arrays.
- Practice partition logic separately before implementing the full algorithm.

---

# 🎯 Interview Tip

### Question

Why does Quick Sort sometimes take O(n²) time?

### Answer

Quick Sort performs poorly when the chosen pivot repeatedly creates highly unbalanced partitions, such as when the smallest or largest element is selected every time. In this case, the recursion depth becomes **n**, resulting in a Worst Case Time Complexity of **O(n²)**. Randomized or median-of-three pivot selection helps reduce this risk.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Quick Sort vs Merge Sort
- Quick Sort vs Heap Sort
- Complete Comparison Table
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision Sheet
- Chapter Summary
- Frequently Asked Interview Questions