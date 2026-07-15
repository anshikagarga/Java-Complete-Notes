# 📘 Chapter 06: Quick Sort (Part 1)

> *"Quick Sort is one of the fastest and most widely used sorting algorithms. It follows the Divide and Conquer technique by selecting a Pivot element and partitioning the array around it."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Quick Sort.
- Learn the Divide and Conquer technique.
- Understand the Pivot concept.
- Learn the Partition Algorithm.
- Perform a complete dry run.
- Implement Quick Sort in Java.
- Analyze its Time Complexity.

---

# 📚 Table of Contents

1. What is Quick Sort?
2. Why Quick Sort?
3. Divide and Conquer
4. Pivot
5. Partition Process
6. Quick Sort Algorithm
7. Dry Run
8. Java Implementation
9. Internal Working
10. Memory Diagram
11. Time Complexity
12. Advantages
13. Limitations

---

# 🤔 What is Quick Sort?

Quick Sort is a **comparison-based sorting algorithm** that follows the **Divide and Conquer** approach.

Instead of repeatedly merging arrays like Merge Sort,

Quick Sort works by:

- Selecting a **Pivot** element.
- Placing the pivot at its correct sorted position.
- Moving smaller elements to the left.
- Moving larger elements to the right.
- Recursively sorting both partitions.

---

## Example

Unsorted Array

```text
[8, 4, 7, 9, 3, 10, 5]
```

Sorted Array

```text
[3, 4, 5, 7, 8, 9, 10]
```

---

# 💡 Why Quick Sort?

Bubble Sort

```text
↓

O(n²)
```

Selection Sort

```text
↓

O(n²)
```

Insertion Sort

```text
↓

O(n²)
```

Merge Sort

```text
↓

O(n log n)
```

Quick Sort (Average)

```text
↓

O(n log n)
```

Quick Sort is usually **faster than Merge Sort** for arrays because:

- Better cache utilization
- In-place sorting
- No extra array required

---

# 🧠 Divide and Conquer

Quick Sort works in three steps.

## Step 1 — Choose Pivot

Example

```text
8 4 7 9 3 10 5

Pivot = 5
```

---

## Step 2 — Partition

Move

```text
Smaller

↓

Left
```

Move

```text
Larger

↓

Right
```

Result

```text
4 3 5 8 9 10 7
```

Notice

```text
Pivot

↓

Correct Position
```

---

## Step 3 — Recursively Sort

Sort Left

```text
4 3
```

Sort Right

```text
8 9 10 7
```

Repeat until every partition contains one element.

---

# 📖 What is a Pivot?

A **Pivot** is an element selected to divide the array into two parts.

Every element

```text
< Pivot

↓

Left
```

Every element

```text
> Pivot

↓

Right
```

The pivot itself reaches its correct sorted position after partitioning.

---

# 🎯 Choosing a Pivot

There are several ways to choose a pivot.

### 1. First Element

```text
Pivot = arr[low]
```

---

### 2. Last Element

```text
Pivot = arr[high]
```

*(Most common in interview questions.)*

---

### 3. Middle Element

```text
Pivot = arr[(low + high)/2]
```

---

### 4. Random Pivot

Randomly select any element.

This helps avoid the worst case.

---

### 5. Median of Three

Choose the median of:

- First element
- Middle element
- Last element

Used in many optimized implementations.

---

# 📖 Partition Process

Suppose

```text
[8,4,7,9,3,10,5]
```

Pivot

```text
5
```

After partitioning

```text
4 3 5 8 9 10 7
```

Notice

```text
4 3

↓

Smaller
```

```text
8 9 10 7

↓

Greater
```

Pivot

```text
5

↓

Correct Position
```

---

# 📖 Quick Sort Algorithm

1. Select a pivot.
2. Partition the array.
3. Place pivot at the correct position.
4. Recursively sort the left partition.
5. Recursively sort the right partition.

---

# 🔄 Flow Diagram

```text
Start

↓

Choose Pivot

↓

Partition

↓

Pivot Fixed

↓

Sort Left

↓

Sort Right

↓

Sorted Array
```

---

# 🧠 Dry Run

Given

```text
[5,2,8,1,7]
```

Pivot

```text
7
```

Partition

```text
5 2 1 7 8
```

Left

```text
5 2 1
```

Right

```text
8
```

Again

```text
Pivot = 1

↓

1 2 5
```

Final

```text
1 2 5 7 8
```

---

# 💻 Java Implementation (Lomuto Partition)

```java
public class QuickSort {

    public static void quickSort(int[] arr, int low, int high){

        if(low < high){

            int pivotIndex = partition(arr, low, high);

            quickSort(arr, low, pivotIndex - 1);

            quickSort(arr, pivotIndex + 1, high);

        }

    }

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

    public static void main(String[] args){

        int[] arr = {5,2,8,1,7};

        quickSort(arr,0,arr.length-1);

        for(int num : arr){

            System.out.print(num + " ");

        }

    }

}
```

---

## Output

```text
1 2 5 7 8
```

---

# 🧠 Internal Working

```text
Choose Pivot

↓

Partition

↓

Pivot Fixed

↓

Recursively Sort Left

↓

Recursively Sort Right

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

Sort Left

```text
1

2

5
```

↓

Final

```text
1

2

5

7

8
```

---

# ⚡ Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n log n) |
| Average | O(n log n) |
| Worst | O(n²) |

Worst case occurs when the pivot is always the smallest or largest element.

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(log n) |

This space is due to the recursion stack.

Quick Sort does **not** require an extra array like Merge Sort.

---

# ✅ Advantages

- Very fast in practice.
- In-place sorting.
- Excellent cache performance.
- Suitable for large arrays.
- Widely used in real-world software.

---

# ⚠️ Limitations

- Worst-case Time Complexity is O(n²).
- Recursive implementation.
- Not Stable.
- Performance depends on pivot selection.

---

# 🌍 Real-World Applications

Quick Sort is used in:

- Standard library implementations.
- Database systems.
- Search engines.
- Large in-memory datasets.
- Competitive Programming.
- Operating Systems.

---

# 🎯 Interview Tip

### Question

Why is Quick Sort usually faster than Merge Sort?

### Answer

Quick Sort sorts the array **in-place**, requiring very little extra memory. It also has excellent cache locality because it works within the same array. Although both algorithms have an average time complexity of **O(n log n)**, Quick Sort is often faster in real-world applications due to lower constant factors.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Lomuto vs Hoare Partition
- Stable vs Unstable
- Space Complexity Analysis
- Worst Case Analysis
- Recursion Tree
- Common Mistakes
- Best Practices