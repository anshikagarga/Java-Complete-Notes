# 📘 Chapter 02: Arrays.sort() (Part 2)

## Binary Search, Comparator, Sorting 2D Arrays & Custom Objects

> *"Arrays.sort() becomes even more powerful when combined with methods like `Arrays.binarySearch()` and custom Comparators for sorting complex data structures."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Learn `Arrays.binarySearch()`
- Sort arrays in descending order
- Sort using Comparators
- Sort 2D Arrays
- Sort Custom Objects
- Understand Comparator with Arrays.sort()
- Learn Internal Working

---

# 📚 Table of Contents

1. Arrays.binarySearch()
2. Binary Search Rules
3. Sorting in Descending Order
4. Comparator with Arrays.sort()
5. Sorting 2D Arrays
6. Sorting Custom Objects
7. Internal Working
8. Best Practices
9. Common Mistakes
10. Interview Tips

---

# 📖 Arrays.binarySearch()

Java provides another useful method:

```java
Arrays.binarySearch()
```

It searches an element in a **sorted array**.

> **Important:** The array **must be sorted** before using `binarySearch()`.

---

# 📖 Syntax

```java
Arrays.binarySearch(array, key);
```

---

## Example

```java
import java.util.Arrays;

public class Demo {

    public static void main(String[] args) {

        int[] arr = {10,20,30,40,50};

        int index = Arrays.binarySearch(arr,30);

        System.out.println(index);

    }

}
```

Output

```text
2
```

---

# 📖 If Element is Not Found

```java
int[] arr = {10,20,30,40};

System.out.println(

Arrays.binarySearch(arr,25)

);
```

Output

```text
-3
```

The returned negative value indicates that the element is not present.

The insertion point can be calculated using:

```java
insertionPoint = -(result + 1);
```

---

# 📖 Binary Search Rules

✅ Array must be sorted.

✅ Time Complexity

```
O(log n)
```

✅ Faster than Linear Search.

---

# 📖 Descending Order using Arrays.sort()

Primitive arrays cannot directly be sorted in descending order.

Wrong

```java
int[] arr = {10,20,30};

Arrays.sort(arr,

Collections.reverseOrder());
```

Compilation Error

---

Correct

```java
Integer[] arr = {10,20,30};

Arrays.sort(arr,

Collections.reverseOrder());

System.out.println(Arrays.toString(arr));
```

Output

```text
[30,20,10]
```

---

# 📖 Comparator with Arrays.sort()

Comparator allows custom sorting.

Example

```java
Integer[] arr =

{4,1,8,3};

Arrays.sort(

arr,

Comparator.reverseOrder()

);

System.out.println(Arrays.toString(arr));
```

Output

```text
[8,4,3,1]
```

---

# 📖 Custom Comparator

Sort according to string length.

```java
String[] names =

{

"Java",

"C",

"Python",

"HTML"

};

Arrays.sort(

names,

(a,b) ->

a.length() - b.length()

);

System.out.println(

Arrays.toString(names)

);
```

Output

```text
[C, Java, HTML, Python]
```

---

# 📖 Sorting 2D Arrays

Suppose

```java
int[][] students = {

{101,90},

{102,70},

{103,85}

};
```

Sort according to marks.

```java
Arrays.sort(

students,

(a,b) ->

Integer.compare(

a[1],

b[1]

)

);
```

Print

```java
for(int[] row : students){

System.out.println(

Arrays.toString(row)

);

}
```

Output

```text
[102,70]

[103,85]

[101,90]
```

---

# 📖 Sorting Custom Objects

Suppose

```java
class Student{

int id;

String name;

}
```

Array

```java
Student[] students = {

new Student(1,"Riya"),

new Student(2,"Anshika"),

new Student(3,"Aman")

};
```

Sort by name

```java
Arrays.sort(

students,

(a,b)->

a.name.compareTo(b.name)

);
```

Sort by id

```java
Arrays.sort(

students,

(a,b)->

Integer.compare(a.id,b.id)

);
```

---

# 📦 Internal Working

```text
Array

↓

Arrays.sort()

↓

Comparator (Optional)

↓

Sorting Algorithm

↓

Sorted Array
```

---

# 📊 Arrays.sort() vs Arrays.binarySearch()

| Arrays.sort() | Arrays.binarySearch() |
|---------------|-----------------------|
| Sorts array | Searches element |
| O(n log n) | O(log n) |
| Changes array | Doesn't modify array |
| Used before searching | Requires sorted array |

---

# 💡 Best Practices

- Always sort before using `binarySearch()`.
- Use `Integer[]` instead of `int[]` when a Comparator is required.
- Prefer `Integer.compare()` over subtraction (`a - b`) to avoid integer overflow.
- Use lambda expressions to keep Comparator code concise.
- Choose meaningful comparison logic when sorting custom objects.

---

# ⚠️ Common Mistakes

## ❌ Using binarySearch() on an Unsorted Array

Wrong

```java
int[] arr = {40,10,20};

Arrays.binarySearch(arr,20);
```

Result is unpredictable.

Correct

```java
Arrays.sort(arr);

Arrays.binarySearch(arr,20);
```

---

## ❌ Using reverseOrder() with Primitive Arrays

Wrong

```java
int[] arr={1,2,3};

Arrays.sort(

arr,

Collections.reverseOrder()

);
```

Correct

```java
Integer[] arr={1,2,3};

Arrays.sort(

arr,

Collections.reverseOrder()

);
```

---

## ❌ Comparing Integers by Subtraction

Risky

```java
(a,b) -> a - b
```

Safer

```java
Integer.compare(a,b)
```

---

# 🌍 Real-World Applications

Arrays.sort() with Comparators is used in:

- Student Ranking Systems
- Employee Salary Sorting
- Product Price Sorting
- Airline Reservation Systems
- Movie Rating Applications
- Sports Leaderboards
- E-commerce Platforms

---

# 🎯 Interview Tip

### Question

Why should `Integer.compare()` be preferred over `a - b` inside a Comparator?

### Answer

Using `a - b` can cause **integer overflow** for very large values. `Integer.compare(a, b)` safely compares two integers without overflow and is the recommended approach.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Interview Questions
- MCQs
- Coding Practice
- Best Practices
- Chapter Summary