# 📘 Chapter 07: Heap Sort (Part 1)

> *"Heap Sort is a comparison-based sorting algorithm that uses the Binary Heap data structure. It guarantees **O(n log n)** time complexity in all cases and performs sorting in-place without requiring extra memory."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Heap Sort.
- Learn Binary Heap.
- Understand Max Heap and Min Heap.
- Learn Heapify.
- Build a Heap.
- Perform a complete dry run.
- Implement Heap Sort in Java.
- Analyze Time Complexity.

---

# 📚 Table of Contents

1. What is Heap Sort?
2. Why Heap Sort?
3. Binary Heap
4. Max Heap
5. Min Heap
6. Heapify
7. Heap Construction
8. Heap Sort Algorithm
9. Dry Run
10. Java Implementation
11. Internal Working
12. Memory Diagram
13. Time Complexity
14. Advantages
15. Limitations

---

# 🤔 What is Heap Sort?

Heap Sort is a **comparison-based sorting algorithm** that uses a **Binary Heap** to sort elements.

Instead of repeatedly selecting the minimum or maximum element manually,

Heap Sort stores the elements inside a Heap.

Then,

- Build a Max Heap.
- Remove the maximum element.
- Place it at the end.
- Restore the Heap.
- Repeat until the array becomes sorted.

---

## Example

Unsorted Array

```text
[12, 11, 13, 5, 6, 7]
```

Sorted Array

```text
[5, 6, 7, 11, 12, 13]
```

---

# 💡 Why Heap Sort?

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

Quick Sort

```text
↓

Average

O(n log n)
```

Heap Sort

```text
↓

Always

O(n log n)
```

Heap Sort guarantees good performance in every case.

---

# 🌳 What is a Binary Heap?

A Binary Heap is a **Complete Binary Tree** that satisfies the Heap Property.

There are two types:

- Max Heap
- Min Heap

---

# 📖 Complete Binary Tree

A Complete Binary Tree is a tree where

- Every level is completely filled,
- Except possibly the last level.
- The last level is filled from left to right.

Example

```text
        10

      /    \

     8      6

    / \    /

   4   3  2
```

This is a Complete Binary Tree.

---

# 📖 Array Representation of Heap

A Heap is usually stored inside an array.

```text
Index

0 1 2 3 4 5
```

```text
Array

10 8 6 4 3 2
```

Relationships

```text
Parent

(i-1)/2
```

```text
Left Child

2*i + 1
```

```text
Right Child

2*i + 2
```

---

# 📖 Max Heap

In a Max Heap,

Every parent is greater than or equal to its children.

Example

```text
         50

       /    \

      30     40

     / \    /

   10 20 15
```

Notice

```text
50

>

30

40
```

and

```text
30

>

10

20
```

Largest element always remains at the root.

---

# 📖 Min Heap

In a Min Heap,

Every parent is smaller than or equal to its children.

Example

```text
         10

       /    \

      20     30

     / \    /

   40 50 60
```

Smallest element always remains at the root.

---

# 🎯 Which Heap is Used?

For sorting in **ascending order**

```text
Max Heap
```

For sorting in **descending order**

```text
Min Heap
```

Most interview questions use

```text
Max Heap
```

---

# 📖 What is Heapify?

Heapify is the process of converting a subtree into a valid Heap.

If one node violates the Heap property,

Heapify restores it.

Example

Before

```text
      10

     /  \

   30   20
```

Heap Property Broken

↓

After Heapify

```text
      30

     /  \

   10   20
```

---

# 📖 Building a Heap

Given

```text
12 11 13 5 6 7
```

Build Max Heap

```text
        13

      /    \

    11      12

   / \      /

  5   6    7
```

Now,

Largest element

↓

Root

---

# 📖 Heap Sort Algorithm

### Step 1

Build a Max Heap.

↓

### Step 2

Swap Root with Last Element.

↓

### Step 3

Reduce Heap Size.

↓

### Step 4

Heapify Root.

↓

### Step 5

Repeat until Heap Size becomes 1.

---

# 🔄 Flow Diagram

```text
Start

↓

Build Max Heap

↓

Swap Root & Last

↓

Reduce Heap Size

↓

Heapify

↓

Repeat

↓

Sorted Array
```

---

# 🧠 Dry Run

Given

```text
12 11 13 5 6 7
```

---

### Build Heap

```text
13 11 12 5 6 7
```

---

Swap

```text
7 11 12 5 6 13
```

Heapify

```text
12 11 7 5 6 13
```

---

Swap

```text
6 11 7 5 12 13
```

Heapify

```text
11 6 7 5 12 13
```

---

Continue

↓

Final

```text
5 6 7 11 12 13
```

---

# 💻 Java Implementation

```java
public class HeapSort {

    public static void heapSort(int[] arr){

        int n = arr.length;

        // Build Max Heap
        for(int i = n/2 - 1; i >= 0; i--){

            heapify(arr, n, i);

        }

        // Extract Elements
        for(int i = n - 1; i > 0; i--){

            int temp = arr[0];
            arr[0] = arr[i];
            arr[i] = temp;

            heapify(arr, i, 0);

        }

    }

    public static void heapify(int[] arr, int n, int i){

        int largest = i;

        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if(left < n && arr[left] > arr[largest]){

            largest = left;

        }

        if(right < n && arr[right] > arr[largest]){

            largest = right;

        }

        if(largest != i){

            int temp = arr[i];
            arr[i] = arr[largest];
            arr[largest] = temp;

            heapify(arr, n, largest);

        }

    }

    public static void main(String[] args){

        int[] arr = {12,11,13,5,6,7};

        heapSort(arr);

        for(int num : arr){

            System.out.print(num + " ");

        }

    }

}
```

---

## Output

```text
5 6 7 11 12 13
```

---

# 🧠 Internal Working

```text
Array

↓

Build Max Heap

↓

Largest Element at Root

↓

Swap Root & Last

↓

Reduce Heap

↓

Heapify

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

Repeated Swaps

↓

Final

```text
5

6

7

11

12

13
```

---

# ⚡ Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n log n) |
| Average | O(n log n) |
| Worst | O(n log n) |

Heap Sort guarantees the same performance in all cases.

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(1) |

Heap Sort is an **In-place Sorting Algorithm**.

---

# ✅ Advantages

- Guaranteed O(n log n).
- In-place sorting.
- No extra array required.
- Suitable for large datasets.
- Efficient Worst Case performance.

---

# ⚠️ Limitations

- Not Stable.
- Slower than Quick Sort in practice.
- Cache performance is not as good as Quick Sort.

---

# 🌍 Real-World Applications

Heap Sort is used in:

- Priority Queues
- Operating Systems
- Task Scheduling
- Event Simulation
- Embedded Systems
- Memory-Constrained Applications

---

# 🎯 Interview Tip

### Question

Why do we build a **Max Heap** for ascending order sorting?

### Answer

In a Max Heap, the **largest element is always at the root**. During each iteration, this largest element is swapped with the last element of the unsorted portion of the array. As the heap size decreases, the array gradually becomes sorted in **ascending order**.

---

# 🚀 Next: Part 2

In **Part 2**, you'll learn:

- Heapify in Detail
- Building Heap Step-by-Step
- Stable vs Unstable
- Complete Time Complexity Analysis
- Heap Construction Visualization
- Common Mistakes
- Best Practices