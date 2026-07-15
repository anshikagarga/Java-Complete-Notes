# 📘 Chapter 03: Selection Sort (Part 1)

> *"Selection Sort is a simple comparison-based sorting algorithm that repeatedly selects the smallest element from the unsorted portion of the array and places it at its correct position."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Selection Sort.
- Learn how Selection Sort works.
- Perform a dry run.
- Implement Selection Sort in Java.
- Understand its internal working.
- Learn why Selection Sort performs fewer swaps.
- Analyze its Time Complexity.

---

# 📚 Table of Contents

1. What is Selection Sort?
2. Why is it called Selection Sort?
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

# 🤔 What is Selection Sort?

Selection Sort is a **comparison-based sorting algorithm**.

Instead of repeatedly swapping adjacent elements like Bubble Sort, it:

- Finds the smallest element.
- Places it at its correct position.
- Repeats the same process for the remaining unsorted elements.

After every pass, one element is permanently placed in its correct position.

---

## Example

Unsorted Array

```text
[64, 25, 12, 22, 11]
```

Sorted Array

```text
[11, 12, 22, 25, 64]
```

---

# 💡 Why is it Called Selection Sort?

During every iteration, the algorithm **selects** the smallest element from the unsorted portion.

Example

```text
64 25 12 22 11

↓

Select 11

↓

Swap with 64

↓

11 25 12 22 64
```

Again,

```text
25 12 22 64

↓

Select 12

↓

Swap

↓

11 12 25 22 64
```

This process continues until the array becomes sorted.

---

# 📖 Selection Sort Algorithm

Repeat the following steps:

1. Assume the first unsorted element is the minimum.
2. Traverse the remaining array.
3. Find the actual minimum element.
4. Swap it with the first unsorted element.
5. Repeat for the remaining array.

---

# 🔄 Selection Sort Flow

```text
Start

↓

Assume Minimum Element

↓

Traverse Remaining Array

↓

Found Smaller Element?

↓

Yes

↓

Update Minimum Index

↓

End of Traversal

↓

Swap

↓

Repeat

↓

Sorted Array
```

---

# 🧠 Dry Run

Given Array

```text
[64, 25, 12, 22, 11]
```

---

## Pass 1

Minimum

```text
64
```

Traverse

```text
25

↓

12

↓

11
```

Minimum Found

```text
11
```

Swap

```text
11 25 12 22 64
```

---

## Pass 2

Remaining Array

```text
25 12 22 64
```

Minimum

```text
12
```

Swap

```text
11 12 25 22 64
```

---

## Pass 3

Remaining

```text
25 22 64
```

Minimum

```text
22
```

Swap

```text
11 12 22 25 64
```

---

## Pass 4

Remaining

```text
25 64
```

Already Sorted

Final Array

```text
11 12 22 25 64
```

---

# 💻 Java Implementation

```java
public class SelectionSort {

    public static void selectionSort(int[] arr){

        int n = arr.length;

        for(int i = 0; i < n - 1; i++){

            int minIndex = i;

            for(int j = i + 1; j < n; j++){

                if(arr[j] < arr[minIndex]){

                    minIndex = j;

                }

            }

            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;

        }

    }

    public static void main(String[] args){

        int[] arr = {64,25,12,22,11};

        selectionSort(arr);

        for(int num : arr){

            System.out.print(num + " ");

        }

    }

}
```

Output

```text
11 12 22 25 64
```

---

# 🧠 Internal Working

```text
Array

↓

Find Minimum

↓

Swap

↓

One Position Fixed

↓

Repeat

↓

Sorted Array
```

Unlike Bubble Sort, Selection Sort performs **only one swap per pass**.

---

# 📦 Memory Diagram

Before

```text
+----+----+----+----+----+

|64|25|12|22|11|

+----+----+----+----+----+
```

Pass 1

```text
+----+----+----+----+----+

|11|25|12|22|64|

+----+----+----+----+----+
```

Pass 2

```text
+----+----+----+----+----+

|11|12|25|22|64|

+----+----+----+----+----+
```

Final

```text
+----+----+----+----+----+

|11|12|22|25|64|

+----+----+----+----+----+
```

---

# ⚡ Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n²) |
| Average | O(n²) |
| Worst | O(n²) |

Unlike Bubble Sort, Selection Sort always scans the remaining array, even if it is already sorted.

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(1) |

Selection Sort uses only one temporary variable during swapping.

---

# ✅ Advantages

- Easy to understand.
- Easy to implement.
- Uses very little memory.
- Performs fewer swaps than Bubble Sort.
- Suitable when swapping is expensive.

---

# ⚠️ Limitations

- Poor performance for large datasets.
- Always performs O(n²) comparisons.
- Not adaptive.
- Generally slower than Merge Sort and Quick Sort.

---

# 🌍 Real-World Applications

Selection Sort is mainly used for:

- Educational purposes.
- Small datasets.
- Situations where memory usage is important.
- Systems where minimizing swaps is beneficial.

---

# 🎯 Interview Tip

### Question

Why does Selection Sort perform fewer swaps than Bubble Sort?

### Answer

Selection Sort finds the smallest element in the unsorted portion and performs only **one swap** at the end of each pass. Bubble Sort may perform multiple swaps during a single pass, making Selection Sort more efficient when swap operations are costly.

---

➡️ **Next: Part 2** will cover:

- Stable vs Unstable Selection Sort
- In-place Property
- Optimized Selection Sort
- Ascending & Descending Sorting
- Complete Complexity Analysis
- Internal Working
- Common Mistakes
- Best Practices