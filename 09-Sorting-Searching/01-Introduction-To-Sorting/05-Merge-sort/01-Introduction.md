# 📘 Chapter 05: Merge Sort (Part 1)

> *"Merge Sort is one of the most efficient sorting algorithms. It follows the Divide and Conquer technique by recursively dividing the array into smaller parts, sorting them, and finally merging them into a sorted array."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Merge Sort.
- Learn the Divide and Conquer technique.
- Understand the Merge Process.
- Perform a complete dry run.
- Implement Merge Sort in Java.
- Understand recursion in Merge Sort.
- Analyze Time Complexity.

---

# 📚 Table of Contents

1. What is Merge Sort?
2. Why Merge Sort?
3. Divide and Conquer
4. Merge Sort Algorithm
5. Dry Run
6. Java Implementation
7. Internal Working
8. Memory Diagram
9. Time Complexity
10. Advantages
11. Limitations

---

# 🤔 What is Merge Sort?

Merge Sort is a **comparison-based** sorting algorithm that follows the **Divide and Conquer** strategy.

Instead of sorting the entire array at once, it:

- Divides the array into smaller halves.
- Recursively sorts each half.
- Merges the sorted halves into one sorted array.

---

## Example

Unsorted Array

```text
[38, 27, 43, 3, 9, 82, 10]
```

Sorted Array

```text
[3, 9, 10, 27, 38, 43, 82]
```

---

# 💡 Why is Merge Sort Important?

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

For large datasets,

Merge Sort is significantly faster.

---

# 🧠 Divide and Conquer

Merge Sort works in three steps.

## Step 1 — Divide

Divide the array into two equal halves.

```text
[38,27,43,3,9,82,10]

↓

[38,27,43]

[3,9,82,10]
```

---

## Step 2 — Conquer

Recursively divide until every subarray contains only one element.

```text
[38]

[27]

[43]

[3]

[9]

[82]

[10]
```

A single element is already sorted.

---

## Step 3 — Merge

Merge the smaller sorted arrays.

```text
[27]

+

[38]

↓

[27,38]
```

Continue until the entire array becomes sorted.

---

# 📖 Merge Sort Algorithm

1. Find the middle index.
2. Divide the array into two halves.
3. Recursively sort the left half.
4. Recursively sort the right half.
5. Merge both sorted halves.

---

# 🔄 Flow Diagram

```text
Start

↓

Find Middle

↓

Divide Array

↓

Sort Left Half

↓

Sort Right Half

↓

Merge

↓

Sorted Array
```

---

# 🧠 Dry Run

Given Array

```text
[8,4,2,6]
```

---

## Divide

```text
[8,4]

[2,6]
```

---

Again Divide

```text
[8]

[4]

[2]

[6]
```

---

## Merge

```text
[8]

+

[4]

↓

[4,8]
```

---

```text
[2]

+

[6]

↓

[2,6]
```

---

Final Merge

```text
[4,8]

+

[2,6]

↓

[2,4,6,8]
```

---

# 🌳 Recursion Tree

```text
            [8 4 2 6]

          /            \

      [8 4]          [2 6]

      /   \          /   \

    [8]  [4]      [2]  [6]

      \   /          \   /

      [4 8]         [2 6]

           \        /

          [2 4 6 8]
```

---

# 💻 Java Implementation

```java
public class MergeSort {

    public static void mergeSort(int[] arr, int left, int right){

        if(left >= right){
            return;
        }

        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);

        mergeSort(arr, mid + 1, right);

        merge(arr, left, mid, right);

    }

    public static void merge(int[] arr, int left, int mid, int right){

        int[] temp = new int[right - left + 1];

        int i = left;
        int j = mid + 1;
        int k = 0;

        while(i <= mid && j <= right){

            if(arr[i] <= arr[j]){
                temp[k++] = arr[i++];
            }else{
                temp[k++] = arr[j++];
            }

        }

        while(i <= mid){
            temp[k++] = arr[i++];
        }

        while(j <= right){
            temp[k++] = arr[j++];
        }

        for(int x = 0; x < temp.length; x++){
            arr[left + x] = temp[x];
        }

    }

    public static void main(String[] args){

        int[] arr = {8,4,2,6};

        mergeSort(arr,0,arr.length-1);

        for(int num : arr){
            System.out.print(num + " ");
        }

    }

}
```

---

## Output

```text
2 4 6 8
```

---

# 🧠 Internal Working

```text
Array

↓

Divide

↓

Recursive Calls

↓

Single Elements

↓

Merge

↓

Sorted Array
```

---

# 📦 Memory Diagram

Original

```text
8

4

2

6
```

↓

Divide

```text
8 4

2 6
```

↓

Divide Again

```text
8

4

2

6
```

↓

Merge

```text
4 8

2 6
```

↓

Final

```text
2

4

6

8
```

---

# ⚡ Time Complexity

| Case | Complexity |
|------|------------|
| Best | O(n log n) |
| Average | O(n log n) |
| Worst | O(n log n) |

Unlike Bubble, Selection, and Insertion Sort,

Merge Sort performs consistently in every case.

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(n) |

Merge Sort requires an additional temporary array during the merge process.

---

# ✅ Advantages

- Efficient for large datasets.
- Stable Sorting Algorithm.
- Guaranteed O(n log n) performance.
- Works well with Linked Lists.
- Suitable for external sorting.

---

# ⚠️ Limitations

- Requires extra memory.
- Recursive implementation increases function call overhead.
- Slower than Quick Sort for some in-memory datasets.

---

# 🌍 Real-World Applications

Merge Sort is widely used in:

- Database systems.
- External file sorting.
- Large datasets.
- Linked List sorting.
- Parallel computing.
- Big Data processing.

---

# 🎯 Interview Tip

### Question

Why is Merge Sort called a Divide and Conquer algorithm?

### Answer

Merge Sort first **divides** the array into smaller subarrays, recursively **conquers** each subproblem by sorting them, and finally **merges** the sorted subarrays into one completely sorted array. This Divide → Conquer → Merge strategy gives it a guaranteed **O(n log n)** time complexity.

---

# 🚀 Next: Part 2

In **Part 2**, you'll learn:

- Merge Process in Detail
- Stable Sorting
- Space Complexity Analysis
- Why Merge Sort is O(n log n)
- Recursion Stack
- Internal Visualization
- Common Mistakes
- Best Practices