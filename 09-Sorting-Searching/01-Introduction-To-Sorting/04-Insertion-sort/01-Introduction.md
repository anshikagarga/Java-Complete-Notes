# 📘 Chapter 04: Insertion Sort (Part 1)

> *"Insertion Sort builds the sorted array one element at a time by inserting each element into its correct position. It works similarly to the way we arrange playing cards in our hands."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Insertion Sort.
- Learn how Insertion Sort works.
- Perform a complete dry run.
- Implement Insertion Sort in Java.
- Understand shifting instead of swapping.
- Analyze its Time Complexity.
- Know where Insertion Sort is used.

---

# 📚 Table of Contents

1. What is Insertion Sort?
2. Why is it Called Insertion Sort?
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

# 🤔 What is Insertion Sort?

Insertion Sort is a **comparison-based sorting algorithm** that builds the sorted portion of the array one element at a time.

Instead of repeatedly swapping elements like Bubble Sort or selecting the minimum element like Selection Sort, Insertion Sort:

- Picks one element.
- Finds its correct position in the sorted part.
- Inserts it there by shifting larger elements to the right.

---

## Example

Unsorted Array

```text
[8, 5, 3, 9, 1]
```

Sorted Array

```text
[1, 3, 5, 8, 9]
```

---

# 💡 Why is it Called Insertion Sort?

Each element is **inserted** into its correct position in the already sorted portion.

Think of arranging playing cards.

Initially

```text
8
```

Next Card

```text
5
```

Insert before 8

```text
5 8
```

Next Card

```text
3
```

Insert before 5

```text
3 5 8
```

Continue until every card is placed correctly.

---

# 🃏 Real-Life Analogy

Imagine you're holding playing cards.

Whenever you receive a new card,

you don't reshuffle all the cards.

Instead,

you insert the new card into its correct position.

Insertion Sort follows the same idea.

---

# 📖 Insertion Sort Algorithm

1. Consider the first element as already sorted.
2. Pick the next element (called the **key**).
3. Compare it with elements in the sorted part.
4. Shift larger elements one position to the right.
5. Insert the key into its correct position.
6. Repeat until the array is completely sorted.

---

# 🔄 Flow Diagram

```text
Start

↓

Take Next Element

↓

Compare with Previous Elements

↓

Shift Larger Elements

↓

Insert Key

↓

Repeat

↓

Sorted Array
```

---

# 🧠 Dry Run

Given Array

```text
[8, 5, 3, 9, 1]
```

---

## Initial

Sorted Part

```text
8
```

Unsorted Part

```text
5 3 9 1
```

---

## Pass 1

Key

```text
5
```

Compare

```text
8 > 5
```

Shift

```text
8
```

Insert

```text
5 8 3 9 1
```

---

## Pass 2

Key

```text
3
```

Compare

```text
8 > 3

↓

Shift

5 > 3

↓

Shift
```

Insert

```text
3 5 8 9 1
```

---

## Pass 3

Key

```text
9
```

Already greater than 8

Insert

```text
3 5 8 9 1
```

No shifting required.

---

## Pass 4

Key

```text
1
```

Shift

```text
9

↓

8

↓

5

↓

3
```

Insert

```text
1 3 5 8 9
```

Array Sorted.

---

# 💻 Java Implementation

```java
public class InsertionSort {

    public static void insertionSort(int[] arr){

        int n = arr.length;

        for(int i = 1; i < n; i++){

            int key = arr[i];
            int j = i - 1;

            while(j >= 0 && arr[j] > key){

                arr[j + 1] = arr[j];
                j--;

            }

            arr[j + 1] = key;

        }

    }

    public static void main(String[] args){

        int[] arr = {8,5,3,9,1};

        insertionSort(arr);

        for(int num : arr){

            System.out.print(num + " ");

        }

    }

}
```

---

## Output

```text
1 3 5 8 9
```

---

# 🧠 Internal Working

```text
Array

↓

Pick Key

↓

Compare with Sorted Part

↓

Shift Elements

↓

Insert Key

↓

Repeat

↓

Sorted Array
```

Unlike Bubble Sort,

Insertion Sort performs **shifting** instead of repeated swapping.

---

# 📦 Memory Diagram

Before

```text
+----+----+----+----+----+

|8|5|3|9|1|

+----+----+----+----+----+
```

Pass 1

```text
+----+----+----+----+----+

|5|8|3|9|1|

+----+----+----+----+----+
```

Pass 2

```text
+----+----+----+----+----+

|3|5|8|9|1|

+----+----+----+----+----+
```

Final

```text
+----+----+----+----+----+

|1|3|5|8|9|

+----+----+----+----+----+
```

---

# ⚡ Time Complexity

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

Only one extra variable (`key`) is used.

---

# ✅ Advantages

- Easy to implement.
- Efficient for small datasets.
- Excellent for nearly sorted arrays.
- Stable Sorting Algorithm.
- In-place Sorting Algorithm.
- Adaptive in nature.

---

# ⚠️ Limitations

- Slow for large datasets.
- Worst-case complexity is O(n²).
- Less efficient than Merge Sort and Quick Sort on large inputs.

---

# 🌍 Real-World Applications

Insertion Sort is commonly used in:

- Small datasets.
- Nearly sorted arrays.
- Hybrid sorting algorithms (such as TimSort).
- Educational purposes.
- Online sorting where elements arrive one by one.

---

# 🎯 Interview Tip

### Question

Why is Insertion Sort faster than Bubble Sort for nearly sorted arrays?

### Answer

Insertion Sort only shifts elements that are out of place. If the array is already or nearly sorted, very few shifts are required, resulting in a Best Case Time Complexity of **O(n)**. Bubble Sort, unless optimized, still performs many unnecessary comparisons.

---

➡️ **Next: Part 2** will cover:

- Stable vs Unstable
- In-place & Adaptive Property
- Ascending & Descending Insertion Sort
- Complete Complexity Analysis
- Internal Working with Visualization
- Common Mistakes
- Best Practices