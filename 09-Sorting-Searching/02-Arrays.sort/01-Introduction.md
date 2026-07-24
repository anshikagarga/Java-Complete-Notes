# 📘 Chapter 02: Arrays.sort()

> *"Instead of implementing sorting algorithms manually, Java provides the `Arrays.sort()` method to sort arrays efficiently. It uses highly optimized algorithms internally, making it the preferred choice in most real-world applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand `Arrays.sort()`.
- Learn how Java sorts arrays internally.
- Sort primitive arrays.
- Sort String arrays.
- Sort objects.
- Sort in ascending and descending order.
- Understand Time Complexity.
- Know interview questions related to `Arrays.sort()`.

---

# 📚 Table of Contents

1. Introduction
2. Why Arrays.sort()?
3. Syntax
4. Sorting Primitive Arrays
5. Sorting String Arrays
6. Sorting Partial Arrays
7. Sorting in Descending Order
8. Internal Working
9. Time Complexity
10. Best Practices
11. Common Mistakes

---

# 📖 What is Arrays.sort()?

`Arrays.sort()` is a static method provided by the **java.util.Arrays** class.

It sorts an array in ascending order.

Package

```java
import java.util.Arrays;
```

---

# 💡 Why Use Arrays.sort()?

Instead of writing

- Bubble Sort
- Selection Sort
- Merge Sort
- Quick Sort

Java already provides an optimized sorting method.

Advantages

- Faster
- Reliable
- Optimized
- Easy to Use
- Less Code

---

# 📖 Syntax

```java
Arrays.sort(array);
```

Example

```java
int[] numbers = {40,10,50,20};

Arrays.sort(numbers);
```

---

# 📖 Sorting Integer Array

Example

```java
import java.util.Arrays;

public class Demo {

    public static void main(String[] args) {

        int[] arr = {50,20,40,10,30};

        Arrays.sort(arr);

        System.out.println(Arrays.toString(arr));

    }

}
```

Output

```text
[10, 20, 30, 40, 50]
```

---

# 📖 Sorting Double Array

```java
double[] marks = {92.5,81.3,75.8,99.9};

Arrays.sort(marks);

System.out.println(Arrays.toString(marks));
```

Output

```text
[75.8, 81.3, 92.5, 99.9]
```

---

# 📖 Sorting Character Array

```java
char[] ch = {'Z','A','D','B'};

Arrays.sort(ch);

System.out.println(Arrays.toString(ch));
```

Output

```text
[A, B, D, Z]
```

---

# 📖 Sorting String Array

```java
String[] names = {

    "Riya",

    "Anshika",

    "Aman",

    "Rohan"

};

Arrays.sort(names);

System.out.println(Arrays.toString(names));
```

Output

```text
[Aman, Anshika, Riya, Rohan]
```

---

# 📖 Sorting Partial Array

Syntax

```java
Arrays.sort(array, fromIndex, toIndex);
```

Example

```java
int[] arr = {50,40,30,20,10};

Arrays.sort(arr,1,4);

System.out.println(Arrays.toString(arr));
```

Output

```text
[50, 20, 30, 40, 10]
```

Only indices **1 to 3** are sorted (`toIndex` is exclusive).

---

# 📖 Sorting in Descending Order

For **primitive arrays**, `Arrays.sort()` only sorts in ascending order.

For object arrays (like `Integer[]`), you can use a comparator.

Example

```java
Integer[] arr = {10,50,30,20};

Arrays.sort(arr, Collections.reverseOrder());

System.out.println(Arrays.toString(arr));
```

Output

```text
[50, 30, 20, 10]
```

> `Collections.reverseOrder()` works only with object types such as `Integer[]`, `Double[]`, and `String[]`, not primitive arrays like `int[]`.

---

# 📦 Internal Working

The algorithm used depends on the array type.

| Array Type | Algorithm |
|------------|-----------|
| Primitive Arrays | Dual-Pivot QuickSort |
| Object Arrays | TimSort |

**Dual-Pivot QuickSort**

- Fast
- In-place
- Efficient for primitive data

**TimSort**

- Stable sorting algorithm
- Combination of Merge Sort + Insertion Sort
- Efficient for partially sorted data

---

# 📊 Time Complexity

## Primitive Arrays

| Case | Complexity |
|------|------------|
| Best | O(n log n) |
| Average | O(n log n) |
| Worst | O(n²) *(Dual-Pivot QuickSort worst case)* |

---

## Object Arrays

| Case | Complexity |
|------|------------|
| Best | O(n) *(nearly sorted)* |
| Average | O(n log n) |
| Worst | O(n log n) |

---

# 💡 Best Practices

- Use `Arrays.sort()` instead of implementing sorting algorithms manually in production code.
- Use `Integer[]` if you need custom ordering with a `Comparator`.
- Import `java.util.Arrays`.
- Prefer `Arrays.toString()` to display array contents.
- Use partial sorting only when required.

---

# ⚠️ Common Mistakes

## ❌ Forgetting to Import Arrays

Wrong

```java
Arrays.sort(arr);
```

Error

```text
Cannot find symbol Arrays
```

Correct

```java
import java.util.Arrays;
```

---

## ❌ Using reverseOrder() with int[]

Wrong

```java
int[] arr = {4,2,1};

Arrays.sort(arr, Collections.reverseOrder());
```

Correct

```java
Integer[] arr = {4,2,1};

Arrays.sort(arr, Collections.reverseOrder());
```

---

## ❌ Forgetting Arrays.toString()

Wrong

```java
System.out.println(arr);
```

Output

```text
[I@36baf30c
```

Correct

```java
System.out.println(Arrays.toString(arr));
```

---

# 🌍 Real-World Applications

`Arrays.sort()` is widely used in:

- Student Management Systems
- Employee Records
- E-Commerce Product Listings
- Banking Applications
- Data Analytics
- Search Optimization
- Competitive Programming

---

# 🎯 Interview Tip

### Question

Which sorting algorithm does `Arrays.sort()` use internally?

### Answer

- **Primitive arrays:** Dual-Pivot QuickSort
- **Object arrays:** TimSort (Merge Sort + Insertion Sort)

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Binary Search using `Arrays.binarySearch()`
- Sorting with Comparators
- Sorting 2D Arrays
- Sorting Custom Objects
- Interview Questions