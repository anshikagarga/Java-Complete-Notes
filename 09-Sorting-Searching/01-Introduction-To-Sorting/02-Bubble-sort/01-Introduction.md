# 📘 Chapter 02: Bubble Sort (Part 1)

> *"Bubble Sort is the simplest comparison-based sorting algorithm. It repeatedly compares adjacent elements and swaps them if they are in the wrong order. Larger elements gradually 'bubble' to the end of the array."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Bubble Sort.
- Learn the Bubble Sort algorithm.
- Understand adjacent swapping.
- Perform a dry run.
- Implement Bubble Sort in Java.
- Analyze its working.
- Learn the basic time complexity.

---

# 📚 Table of Contents

1. What is Bubble Sort?
2. Why is it called Bubble Sort?
3. Algorithm
4. Working
5. Dry Run
6. Java Implementation
7. Internal Working
8. Memory Diagram
9. Time Complexity
10. Advantages
11. Limitations

---

# 🤔 What is Bubble Sort?

Bubble Sort is a **comparison-based sorting algorithm**.

It compares two adjacent elements.

If the left element is greater than the right element,

they are swapped.

This process continues until the array becomes sorted.

---

## Example

Unsorted Array

```text
[5, 3, 8, 4, 2]
```

Sorted Array

```text
[2, 3, 4, 5, 8]
```

---

# 💡 Why is it Called Bubble Sort?

After every pass,

the **largest element moves to the end** of the array.

It behaves like an air bubble rising to the surface.

Example

```text
5 3 8 4 2

↓

3 5 8 4 2

↓

3 5 4 8 2

↓

3 5 4 2 8
```

Here,

**8 has bubbled to the last position.**

---

# 📖 Bubble Sort Algorithm

Repeat the following steps until the array is sorted.

1. Start from the first element.
2. Compare adjacent elements.
3. Swap them if they are in the wrong order.
4. Continue until the last unsorted element.
5. Repeat the process for the remaining elements.

---

# 🔄 Bubble Sort Flow

```text
Start

↓

Compare Adjacent Elements

↓

Swap if Needed

↓

Continue Till End

↓

One Pass Completed

↓

Array Sorted?

↓

No → Repeat

↓

Yes → Stop
```

---

# 🧠 Dry Run

Given Array

```text
[5, 1, 4, 2]
```

---

## Pass 1

Compare

```text
5 > 1
```

Swap

```text
1 5 4 2
```

---

Compare

```text
5 > 4
```

Swap

```text
1 4 5 2
```

---

Compare

```text
5 > 2
```

Swap

```text
1 4 2 5
```

Largest element reached the end.

---

## Pass 2

Compare

```text
1 > 4
```

No Swap

---

Compare

```text
4 > 2
```

Swap

```text
1 2 4 5
```

---

## Pass 3

Compare

```text
1 > 2
```

No Swap

Array Sorted

```text
1 2 4 5
```

---

# 💻 Java Implementation

```java
public class BubbleSort {

    public static void bubbleSort(int[] arr){

        int n = arr.length;

        for(int i = 0; i < n - 1; i++){

            for(int j = 0; j < n - i - 1; j++){

                if(arr[j] > arr[j + 1]){

                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;

                }

            }

        }

    }

    public static void main(String[] args){

        int[] arr = {5, 1, 4, 2};

        bubbleSort(arr);

        for(int num : arr){

            System.out.print(num + " ");

        }

    }

}
```

Output

```text
1 2 4 5
```

---

# 🧠 Internal Working

```text
Array

↓

Compare

↓

Swap

↓

Largest Moves Right

↓

Repeat

↓

Sorted Array
```

---

# 📦 Memory Diagram

Before

```text
Index

0   1   2   3

↓

5   1   4   2
```

After Pass 1

```text
1   4   2   5
```

After Pass 2

```text
1   2   4   5
```

---

# ⚡ Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n²)* |
| Average | O(n²) |
| Worst | O(n²) |

> **Note:** The best case becomes **O(n)** only in the optimized version (covered in Part 2).

---

# ✅ Advantages

- Easy to understand.
- Easy to implement.
- No extra memory required.
- Good for learning sorting concepts.

---

# ⚠️ Limitations

- Very slow for large datasets.
- Performs unnecessary comparisons.
- Not suitable for production systems with large input sizes.
- Inefficient compared to Merge Sort or Quick Sort.

---

# 🎯 Interview Tip

### Question

Why is Bubble Sort called Bubble Sort?

### Answer

Bubble Sort gets its name because after each pass, the largest unsorted element moves to its correct position at the end of the array, just like an air bubble rises to the surface.

---

➡️ **Next: Part 2** will cover:

- Optimized Bubble Sort
- Early Termination using `swapped` Flag
- Ascending & Descending Bubble Sort
- Stability
- In-place Property
- Complete Complexity Analysis
- Real-World Applications