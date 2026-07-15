# 📘 Chapter 02: Bubble Sort (Part 2)

## Optimized Bubble Sort, Stability & Complexity Analysis

> *"The basic Bubble Sort performs unnecessary comparisons even if the array is already sorted. The optimized version improves performance by stopping early when no swaps occur during a pass."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Optimized Bubble Sort.
- Learn the Swapped Flag.
- Perform an optimized dry run.
- Understand Stability.
- Learn In-place Sorting.
- Analyze Time & Space Complexity.
- Understand when Bubble Sort should be used.

---

# 📚 Table of Contents

1. Why Optimize Bubble Sort?
2. Swapped Flag
3. Optimized Algorithm
4. Dry Run
5. Java Implementation
6. Stable Sorting
7. In-place Sorting
8. Time & Space Complexity
9. Internal Working
10. Real-World Applications
11. Common Mistakes
12. Best Practices

---

# 🤔 Why Optimize Bubble Sort?

Suppose the array is already sorted.

```text
[10, 20, 30, 40, 50]
```

The normal Bubble Sort still performs all passes even though no swapping is required.

This results in unnecessary comparisons.

To solve this problem, we use a **Swapped Flag**.

---

# 📖 Swapped Flag

A boolean variable named `swapped` is used.

- Initially set to `false`.
- If any swap occurs during a pass, set it to `true`.
- If no swap occurs, the array is already sorted.
- Stop the algorithm immediately.

This optimization significantly improves the **Best Case Time Complexity**.

---

# 📝 Optimized Algorithm

1. Start from the first element.
2. Compare adjacent elements.
3. Swap them if required.
4. Set `swapped = true` whenever a swap occurs.
5. After completing one pass:
   - If `swapped == false`, stop.
   - Otherwise, continue with the next pass.

---

# 🧠 Dry Run

Given Array

```text
[10, 20, 30, 40]
```

---

## Pass 1

Compare

```text
10 < 20
```

No Swap

Compare

```text
20 < 30
```

No Swap

Compare

```text
30 < 40
```

No Swap

```text
swapped = false
```

Algorithm Stops.

Total Passes

```text
1
```

instead of

```text
3
```

---

# 💻 Java Implementation (Optimized)

```java
public class BubbleSort {

    public static void bubbleSort(int[] arr){

        int n = arr.length;

        for(int i = 0; i < n - 1; i++){

            boolean swapped = false;

            for(int j = 0; j < n - i - 1; j++){

                if(arr[j] > arr[j + 1]){

                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;

                    swapped = true;

                }

            }

            if(!swapped){
                break;
            }

        }

    }

    public static void main(String[] args){

        int[] arr = {10,20,30,40};

        bubbleSort(arr);

        for(int num : arr){
            System.out.print(num + " ");
        }

    }

}
```

Output

```text
10 20 30 40
```

---

# 📖 Bubble Sort in Descending Order

Simply change the comparison operator.

Ascending

```java
if(arr[j] > arr[j + 1])
```

Descending

```java
if(arr[j] < arr[j + 1])
```

Example

Input

```text
[5,2,8,1]
```

Output

```text
[8,5,2,1]
```

---

# 📖 Stable Sorting

Bubble Sort is a **Stable Sorting Algorithm**.

Equal elements maintain their original order.

Example

Before Sorting

```text
85(A)

70

85(B)

90
```

After Sorting

```text
70

85(A)

85(B)

90
```

Notice that

```text
85(A)
```

still appears before

```text
85(B)
```

---

# 📖 In-place Sorting

Bubble Sort is an **In-place Sorting Algorithm**.

It does not require any additional array.

Only a temporary variable is used during swapping.

Memory Requirement

```text
O(1)
```

---

# 📊 Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n) |
| Average | O(n²) |
| Worst | O(n²) |

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(1) |

Bubble Sort requires constant extra memory.

---

# 🧠 Internal Working

```text
Array

↓

Compare Adjacent Elements

↓

Swap if Required

↓

Set Swapped Flag

↓

Another Pass?

↓

Yes → Continue

↓

No → Stop
```

---

# 📦 Memory Diagram

```text
Before

+----+----+----+----+

|5|2|8|1|

+----+----+----+----+

↓

Swap

↓

+----+----+----+----+

|2|5|8|1|

+----+----+----+----+

↓

Continue

↓

Sorted Array
```

---

# 🌍 Real-World Applications

Bubble Sort is generally **not used in production** because of its poor performance.

However, it is useful for:

- Learning Sorting Algorithms
- Academic Assignments
- Small Data Sets
- Competitive Programming Basics
- Understanding Swapping Logic

---

# ⚠️ Common Mistakes

## ❌ Forgetting `swapped = false`

Always reset it at the beginning of every pass.

---

## ❌ Incorrect Loop Condition

Wrong

```java
j < n
```

Correct

```java
j < n - i - 1
```

---

## ❌ Forgetting `break`

Without

```java
break;
```

the optimization has no effect.

---

## ❌ Wrong Comparison

Ascending

```java
arr[j] > arr[j+1]
```

Descending

```java
arr[j] < arr[j+1]
```

---

# 💡 Best Practices

- Use Bubble Sort only for educational purposes.
- Always implement the optimized version.
- Prefer Merge Sort or Quick Sort for large datasets.
- Remember Bubble Sort is Stable and In-place.
- Analyze Time and Space Complexity before choosing an algorithm.

---

# 🎯 Interview Tip

### Question

Why is the optimized Bubble Sort faster than the normal Bubble Sort?

### Answer

The optimized Bubble Sort uses a **swapped flag**. If no swaps occur during a pass, it means the array is already sorted, so the algorithm terminates early. This reduces the Best Case Time Complexity from **O(n²)** to **O(n)**.

---

➡️ **Next: Part 3** will cover:

- Bubble Sort vs Selection Sort
- Bubble Sort vs Insertion Sort
- Complete Complexity Comparison
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision
- Chapter Summary
- Frequently Asked Interview Questions