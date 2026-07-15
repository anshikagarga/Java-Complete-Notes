# 📘 Chapter 05: Merge Sort (Part 2)

## Merge Process, Stability & Complexity Analysis

> *"The real power of Merge Sort lies in its merge operation. Dividing the array is simple, but efficiently merging two sorted arrays is what makes Merge Sort one of the fastest comparison-based sorting algorithms."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Merge Process.
- Learn why Merge Sort is Stable.
- Understand Recursion Stack.
- Analyze Time & Space Complexity.
- Learn Internal Working.
- Understand when Merge Sort should be used.
- Learn the disadvantages of Merge Sort.

---

# 📚 Table of Contents

1. Merge Process
2. Stable Sorting
3. Recursive Working
4. Recursion Stack
5. Time Complexity Analysis
6. Space Complexity
7. Internal Working
8. Memory Diagram
9. Real-World Applications
10. Common Mistakes
11. Best Practices

---

# 📖 Understanding the Merge Process

After dividing the array,

Merge Sort starts combining smaller sorted arrays.

Example

```text
Left

[4,8]

Right

[2,6]
```

Merge Step

Compare

```text
4

vs

2
```

Smaller Element

```text
2
```

Temporary Array

```text
[2]
```

---

Compare Again

```text
4

vs

6
```

Smaller

```text
4
```

Temporary Array

```text
[2,4]
```

---

Compare

```text
8

vs

6
```

Smaller

```text
6
```

Temporary Array

```text
[2,4,6]
```

---

Remaining Element

```text
8
```

Final

```text
[2,4,6,8]
```

---

# 🧠 Step-by-Step Merge Visualization

```text
Left

4 8

Right

2 6

↓

Compare

↓

2

↓

Compare

↓

4

↓

Compare

↓

6

↓

Copy Remaining

↓

8

↓

Merged Array

2 4 6 8
```

---

# 📖 Why is Merge Sort Stable?

Merge Sort is a **Stable Sorting Algorithm**.

Equal elements always maintain their original order.

---

## Example

Before Sorting

```text
70(A)

30

70(B)

20
```

After Sorting

```text
20

30

70(A)

70(B)
```

Notice

```text
70(A)
```

still comes before

```text
70(B)
```

---

# 📖 Why Does Merge Sort Remain Stable?

During merging,

the comparison is written as

```java
if(arr[i] <= arr[j])
```

Notice

```text
<=
```

instead of

```text
<
```

If two elements are equal,

the left element is copied first,

preserving the original order.

---

# 📖 Recursive Working

Merge Sort repeatedly divides the array until only one element remains.

```text
8 4 2 6

↓

8 4

↓

8

↓

Return

↓

Merge

↓

Repeat
```

Every recursive call waits until its child calls finish.

---

# 🌳 Recursion Stack

```text
mergeSort(0,3)

↓

mergeSort(0,1)

↓

mergeSort(0,0)

↓

Return

↓

mergeSort(1,1)

↓

Return

↓

Merge

↓

mergeSort(2,3)

↓

...

↓

Final Merge
```

This sequence of recursive calls is stored in the **Call Stack**.

---

# 📊 Time Complexity Analysis

Suppose

```text
n = 8
```

Divide

```text
8

↓

4

↓

2

↓

1
```

Number of Levels

```text
log₂ n
```

At each level,

all elements are merged.

Work Done

```text
n
```

Therefore

```text
Total Work

↓

n × log n

↓

O(n log n)
```

---

# 📊 Space Complexity

Merge Sort requires an extra temporary array.

```text
Original Array

↓

Temporary Array

↓

Copy Back
```

Extra Memory

```text
O(n)
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

Merge into Temporary Array

↓

Copy Back

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

Temporary Array

```text
2

4

6

8
```

↓

Copy Back

```text
2

4

6

8
```

---

# 🌍 Real-World Applications

Merge Sort is commonly used in:

- Database indexing
- External file sorting
- Big Data processing
- Sorting Linked Lists
- Parallel computing
- Distributed systems
- Multi-threaded sorting

---

# ⚠️ Common Mistakes

## ❌ Wrong Mid Calculation

Wrong

```java
int mid = (left + right) / 2;
```

For very large values, this may cause integer overflow.

Correct

```java
int mid = left + (right - left) / 2;
```

---

## ❌ Forgetting Base Case

Wrong

```java
mergeSort(left, right);
```

Correct

```java
if(left >= right)
    return;
```

Without the base case,

the recursion never stops.

---

## ❌ Incorrect Merge Logic

Wrong

```java
while(i < mid)
```

Correct

```java
while(i <= mid)
```

---

## ❌ Forgetting Remaining Elements

Always copy the remaining elements from both left and right subarrays.

```java
while(i <= mid)

while(j <= right)
```

---

# 💡 Best Practices

- Always calculate the middle safely.
- Write the merge function separately.
- Use `<=` while comparing to maintain stability.
- Draw the recursion tree while learning.
- Practice dry runs before coding.

---

# 🎯 Interview Tip

### Question

Why is Merge Sort's Time Complexity always O(n log n)?

### Answer

Merge Sort divides the array into **log₂(n)** levels. At every level, all **n** elements are processed during the merge step. Therefore,

```text
Total Time

↓

n × log n

↓

O(n log n)
```

Unlike Bubble Sort or Insertion Sort, Merge Sort performs consistently in the Best, Average, and Worst cases.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Merge Sort vs Quick Sort
- Merge Sort vs Heap Sort
- Merge Sort vs Insertion Sort
- Complete Comparison Table
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision Sheet
- Chapter Summary
- Frequently Asked Interview Questions