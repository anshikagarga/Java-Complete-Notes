# 📘 Chapter 03: Selection Sort (Part 2)

## Stable vs Unstable, In-place Sorting & Complexity Analysis

> *"Selection Sort minimizes the number of swaps, making it useful when writing data is expensive. However, unlike Bubble Sort and Insertion Sort, it is not a stable sorting algorithm."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand why Selection Sort is Unstable.
- Learn In-place Sorting.
- Implement Descending Order Selection Sort.
- Analyze Time & Space Complexity.
- Understand Internal Working.
- Learn when Selection Sort should be used.
- Compare it with Bubble Sort.

---

# 📚 Table of Contents

1. Stable vs Unstable
2. In-place Sorting
3. Descending Order
4. Time Complexity
5. Space Complexity
6. Internal Working
7. Memory Diagram
8. Real-World Applications
9. Common Mistakes
10. Best Practices

---

# 📖 Is Selection Sort Stable?

**No.**

Selection Sort is an **Unstable Sorting Algorithm**.

During swapping, equal elements may change their original order.

---

## Example

Before Sorting

```text
50(A)

20

50(B)

10
```

After Sorting

```text
10

20

50(B)

50(A)
```

Notice that

```text
50(A)
```

and

```text
50(B)
```

have changed their original order.

Hence,

```text
Selection Sort

↓

Unstable
```

---

# 📖 Why is Selection Sort Unstable?

Selection Sort swaps the minimum element with the first unsorted element.

During this swap,

duplicate elements may also move.

Example

```text
40(A)

10

40(B)

20
```

Minimum

```text
10
```

Swap

```text
10

40(B)

40(A)

20
```

The order of duplicate values changed.

---

# 📖 Is Selection Sort In-place?

**Yes.**

Selection Sort sorts the array within the original memory.

It requires only one temporary variable.

Extra Memory

```text
O(1)
```

---

# 💻 Descending Order Selection Sort

Instead of selecting the smallest element,

select the **largest** element.

```java
public static void selectionSortDescending(int[] arr){

    int n = arr.length;

    for(int i = 0; i < n - 1; i++){

        int maxIndex = i;

        for(int j = i + 1; j < n; j++){

            if(arr[j] > arr[maxIndex]){

                maxIndex = j;

            }

        }

        int temp = arr[i];
        arr[i] = arr[maxIndex];
        arr[maxIndex] = temp;

    }

}
```

Output

```text
[64, 25, 22, 12, 11]
```

---

# 📊 Time Complexity

Selection Sort always performs the same number of comparisons.

| Case | Complexity |
|------|------------|
| Best | O(n²) |
| Average | O(n²) |
| Worst | O(n²) |

Unlike Bubble Sort,

Selection Sort **cannot terminate early**.

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(1) |

Only one temporary variable is required.

---

# 📊 Number of Comparisons

For an array of size **n**

```text
Pass 1

↓

n - 1 Comparisons

Pass 2

↓

n - 2 Comparisons

Pass 3

↓

n - 3 Comparisons

...

Last Pass

↓

1 Comparison
```

Total Comparisons

```text
(n-1) + (n-2) + ...

↓

n(n-1)/2
```

Hence,

```text
O(n²)
```

---

# 📊 Number of Swaps

Selection Sort performs

```text
Maximum

↓

n - 1 Swaps
```

This is much fewer than Bubble Sort.

---

# 🧠 Internal Working

```text
Array

↓

Find Minimum

↓

Store Minimum Index

↓

Swap Once

↓

One Element Fixed

↓

Repeat

↓

Sorted Array
```

---

# 📦 Memory Diagram

Original Array

```text
64

25

12

22

11
```

↓

Find Minimum

↓

```text
11
```

↓

Swap

↓

```text
11

25

12

22

64
```

↓

Repeat

↓

Sorted Array

---

# 🌍 Real-World Applications

Selection Sort is useful when

- Memory is limited.
- Number of swaps should be minimized.
- Dataset is very small.
- Teaching Sorting Algorithms.
- Embedded Systems (small datasets).

---

# ⚠️ Common Mistakes

## ❌ Swapping Inside Inner Loop

Wrong

```java
for(...){

    if(arr[j] < arr[min]){

        swap();

    }

}
```

Correct

Swap only **after** finding the minimum element.

---

## ❌ Incorrect Loop

Wrong

```java
j = 0
```

Correct

```java
j = i + 1
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
minIndex = j;
```

---

## ❌ Assuming Selection Sort is Stable

It is **not stable**.

---

# 💡 Best Practices

- Swap only once per pass.
- Track the minimum element using an index.
- Prefer Selection Sort only for small datasets.
- Use Merge Sort or Quick Sort for large datasets.
- Remember that Selection Sort is In-place but Unstable.

---

# 🎯 Interview Tip

### Question

Why does Selection Sort perform fewer swaps than Bubble Sort?

### Answer

Bubble Sort swaps adjacent elements multiple times during each pass.

Selection Sort first finds the smallest element in the unsorted portion and performs only **one swap per pass**.

Therefore,

```text
Bubble Sort

↓

Many Swaps

----------------

Selection Sort

↓

One Swap Per Pass
```

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Selection Sort vs Bubble Sort
- Selection Sort vs Insertion Sort
- Complete Comparison Table
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision Sheet
- Chapter Summary
- Frequently Asked Interview Questions