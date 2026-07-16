# 📘 Chapter 03: Collections.sort() (Part 1)

> *"`Collections.sort()` is a utility method provided by the Java Collections Framework to sort List objects. It can sort primitive wrapper classes, Strings, and custom objects using Comparable or Comparator."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand `Collections.sort()`.
- Learn why it is used.
- Understand its syntax.
- Sort Lists in ascending and descending order.
- Learn how `Collections.sort()` works internally.
- Analyze Time Complexity.
- Understand its limitations.

---

# 📚 Table of Contents

1. What is Collections.sort()?
2. Why Collections.sort()?
3. Syntax
4. Internal Working
5. Sorting Integer List
6. Sorting String List
7. Descending Order
8. Time Complexity
9. Advantages
10. Limitations

---

# 🤔 Why Do We Need Collections.sort()?

Suppose we have an `ArrayList`.

```java
ArrayList<Integer> numbers = new ArrayList<>();

numbers.add(40);
numbers.add(10);
numbers.add(90);
numbers.add(20);
```

Current List

```text
40 10 90 20
```

Now,

we want

```text
10 20 40 90
```

Instead of writing

- Bubble Sort
- Merge Sort
- Quick Sort

Java provides a built-in method

```java
Collections.sort()
```

---

# 📖 What is Collections.sort()?

`Collections.sort()` is a static utility method of the `Collections` class.

Package

```java
java.util
```

It sorts objects stored inside a **List**.

Supported Collections

- ArrayList
- LinkedList
- Vector
- Stack

It does **not** work directly with arrays.

For arrays,

use

```java
Arrays.sort()
```

---

# 📖 Syntax

## Ascending Order

```java
Collections.sort(list);
```

---

## Descending Order

```java
Collections.sort(list, Collections.reverseOrder());
```

---

# 📖 Method Signature

```java
public static <T extends Comparable<? super T>>
void sort(List<T> list)
```

This means:

- The list elements must implement `Comparable`.
- Java uses the `compareTo()` method internally.

---

# 📖 How Collections.sort() Works Internally

Suppose

```java
Collections.sort(list);
```

Internally,

Java checks

```text
Does the object implement Comparable?
```

↓

Yes

↓

Call

```java
compareTo()
```

↓

Compare Objects

↓

Swap if Necessary

↓

Repeat

↓

Sorted List

---

# 💻 Example 1: Sorting Integer List

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        ArrayList<Integer> list = new ArrayList<>();

        list.add(40);
        list.add(10);
        list.add(90);
        list.add(20);

        Collections.sort(list);

        System.out.println(list);

    }

}
```

Output

```text
[10, 20, 40, 90]
```

---

# 💻 Example 2: Sorting String List

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        ArrayList<String> list = new ArrayList<>();

        list.add("Banana");
        list.add("Apple");
        list.add("Orange");
        list.add("Mango");

        Collections.sort(list);

        System.out.println(list);

    }

}
```

Output

```text
[Apple, Banana, Mango, Orange]
```

Strings are sorted alphabetically because `String` already implements `Comparable`.

---

# 💻 Example 3: Descending Order

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        ArrayList<Integer> list = new ArrayList<>();

        list.add(10);
        list.add(40);
        list.add(20);
        list.add(30);

        Collections.sort(list, Collections.reverseOrder());

        System.out.println(list);

    }

}
```

Output

```text
[40, 30, 20, 10]
```

---

# 📖 Collections.reverseOrder()

Java provides

```java
Collections.reverseOrder()
```

which returns a Comparator that sorts elements in descending order.

Example

```java
Collections.sort(list, Collections.reverseOrder());
```

---

# 🧠 Internal Working

```text
Collections.sort()

↓

Uses TimSort

↓

Calls compareTo()

↓

Compare Objects

↓

Swap if Needed

↓

Sorted List
```

---

# 📦 Memory Diagram

Before Sorting

```text
40

10

90

20
```

↓

Collections.sort()

↓

After Sorting

```text
10

20

40

90
```

---

# ⚡ Time Complexity

Internally,

Java uses **TimSort** (for most object lists).

| Case | Complexity |
|------|------------|
| Best | O(n) |
| Average | O(n log n) |
| Worst | O(n log n) |

---

# 📊 Space Complexity

| Complexity |
|------------|
| O(n) |

TimSort requires additional memory for merging runs.

---

# ✅ Advantages

- Easy to use.
- No need to implement sorting algorithms manually.
- Stable sorting.
- Efficient for real-world data.
- Optimized using TimSort.

---

# ⚠️ Limitations

- Works only with `List` implementations.
- Objects must implement `Comparable` or a `Comparator` must be provided.
- Uses additional memory compared to in-place algorithms like Heap Sort.

---

# 🌍 Real-World Applications

`Collections.sort()` is commonly used for sorting:

- Student Lists
- Employee Records
- Product Catalogs
- Customer Data
- File Names
- Dates
- Transaction History
- Rankings

---

# 🎯 Interview Tip

### Question

What algorithm does `Collections.sort()` use internally?

### Answer

For object lists, `Collections.sort()` uses **TimSort**, a hybrid sorting algorithm derived from **Merge Sort** and **Insertion Sort**. It is **stable**, performs very well on partially sorted data, and has a worst-case time complexity of **O(n log n)**.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Sorting Custom Objects
- Comparable with Collections.sort()
- Comparator with Collections.sort()
- Internal Working
- Common Mistakes
- Best Practices