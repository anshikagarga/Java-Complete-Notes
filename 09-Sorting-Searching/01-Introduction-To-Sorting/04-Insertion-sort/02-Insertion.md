# 📘 Chapter 04: Insertion Sort (Part 2)

## Stable Sorting, Adaptive Nature & Complexity Analysis

> *"Insertion Sort is one of the few simple sorting algorithms that performs exceptionally well on nearly sorted data. It is Stable, In-place, and Adaptive, making it an important algorithm in both interviews and real-world applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand why Insertion Sort is Stable.
- Learn why it is Adaptive.
- Understand In-place Sorting.
- Implement Descending Order Insertion Sort.
- Analyze Time & Space Complexity.
- Learn Internal Working.
- Know when Insertion Sort should be used.

---

# 📚 Table of Contents

1. Stable Sorting
2. Adaptive Nature
3. In-place Sorting
4. Descending Order
5. Time Complexity
6. Space Complexity
7. Internal Working
8. Memory Diagram
9. Real-World Applications
10. Common Mistakes
11. Best Practices

---

# 📖 Is Insertion Sort Stable?

**Yes.**

Insertion Sort is a **Stable Sorting Algorithm**.

Equal elements always maintain their original order.

---

## Example

Before Sorting

```text
90(A)

70

90(B)

80
```

After Sorting

```text
70

80

90(A)

90(B)
```

Notice that

```text
90(A)
```

still comes before

```text
90(B)
```

The original order of duplicate elements is preserved.

---

# 📖 Why is Insertion Sort Stable?

Insertion Sort only shifts elements that are **strictly greater** than the key.

Condition

```java
arr[j] > key
```

Notice that it is **greater than (`>`)**, not **greater than or equal (`>=`)**.

Therefore,

duplicate elements are **not shifted unnecessarily**, preserving their original order.

---

# 📖 Is Insertion Sort Adaptive?

**Yes.**

Insertion Sort is an **Adaptive Sorting Algorithm**.

If the array is already sorted or nearly sorted,

very few comparisons and shifts are performed.

Example

```text
[10,20,30,40,50]
```

Only comparisons occur.

No shifting.

Time Complexity

```text
O(n)
```

---

# 📖 Is Insertion Sort In-place?

**Yes.**

Insertion Sort sorts the array inside the same memory.

Only one extra variable is used.

```java
int key;
```

Extra Space

```text
O(1)
```

---

# 💻 Descending Order Insertion Sort

Simply reverse the comparison.

Ascending

```java
while(j >= 0 && arr[j] > key)
```

Descending

```java
while(j >= 0 && arr[j] < key)
```

### Java Code

```java
public static void insertionSortDescending(int[] arr){

    for(int i = 1; i < arr.length; i++){

        int key = arr[i];
        int j = i - 1;

        while(j >= 0 && arr[j] < key){

            arr[j + 1] = arr[j];
            j--;

        }

        arr[j + 1] = key;

    }

}
```

Output

```text
9 8 5 3 1
```

---

# 📊 Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n) |
| Average | O(n²) |
| Worst | O(n²) |

---

## Best Case

Array

```text
10 20 30 40 50
```

Only comparisons occur.

No shifting.

Complexity

```text
O(n)
```

---

## Worst Case

Array

```text
50 40 30 20 10
```

Every element must be shifted.

Complexity

```text
O(n²)
```

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(1) |

Only one additional variable (`key`) is used.

---

# 📊 Number of Comparisons

Worst Case

```text
Pass 1

↓

1 Comparison

Pass 2

↓

2 Comparisons

Pass 3

↓

3 Comparisons

...

Total

↓

1 + 2 + 3 + ...

↓

n(n-1)/2
```

Therefore,

```text
O(n²)
```

---

# 🧠 Internal Working

```text
Sorted Part

↓

Pick Key

↓

Compare

↓

Shift Larger Elements

↓

Insert Key

↓

Increase Sorted Portion

↓

Repeat
```

---

# 📦 Memory Diagram

Original

```text
8

5

3

9

1
```

↓

Key

```text
5
```

↓

Shift

```text
8
```

↓

Insert

```text
5

8

3

9

1
```

↓

Repeat

↓

Sorted Array

---

# 🌍 Real-World Applications

Insertion Sort is used in:

- Small datasets
- Nearly sorted arrays
- TimSort (used internally by Java and Python for object sorting)
- Online sorting
- Educational purposes
- Embedded systems

---

# ⚠️ Common Mistakes

## ❌ Using Wrong Loop Condition

Wrong

```java
while(j > 0)
```

Correct

```java
while(j >= 0)
```

---

## ❌ Forgetting to Insert the Key

Wrong

```java
while(...){

}
```

Correct

```java
arr[j + 1] = key;
```

---

## ❌ Swapping Instead of Shifting

Insertion Sort uses **shifting**, not repeated swapping.

Correct

```java
arr[j + 1] = arr[j];
```

---

## ❌ Using `>=` Instead of `>`

Wrong

```java
arr[j] >= key
```

This may change the order of duplicate elements and break stability.

Correct

```java
arr[j] > key
```

---

# 💡 Best Practices

- Always use shifting instead of swapping.
- Remember that Insertion Sort is Stable, Adaptive, and In-place.
- Prefer it for nearly sorted arrays.
- Avoid using it for very large datasets.
- Practice dry runs to understand shifting logic.

---

# 🎯 Interview Tip

### Question

Why is Insertion Sort considered Adaptive?

### Answer

Insertion Sort performs fewer operations when the array is already sorted or nearly sorted. It only shifts elements that are out of place. Therefore, its Best Case Time Complexity becomes **O(n)**, making it an Adaptive Sorting Algorithm.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Insertion Sort vs Bubble Sort
- Insertion Sort vs Selection Sort
- Insertion Sort vs Merge Sort
- Complete Comparison Table
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision Sheet
- Chapter Summary
- Frequently Asked Interview Questions