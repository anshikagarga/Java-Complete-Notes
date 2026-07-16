# 📘 Chapter 03: Collections.sort() (Part 3)

## Collections.sort() vs Arrays.sort(), Interview Questions, MCQs & Practice Problems

> *"`Collections.sort()` is the standard way of sorting List objects in Java. It works seamlessly with Comparable and Comparator, making it one of the most frequently used methods in Java development."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Collections.sort() with Arrays.sort().
- Understand when to use each method.
- Revise the complete chapter.
- Prepare for Java interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Collections.sort() vs Arrays.sort()
2. Advantages
3. Limitations
4. Real-World Applications
5. Common Mistakes
6. Best Practices
7. Interview Questions
8. MCQs
9. Quick Revision
10. Practice Problems
11. Related Topics
12. References
13. Chapter Summary

---

# 📊 Collections.sort() vs Arrays.sort()

| Feature | Collections.sort() | Arrays.sort() |
|----------|--------------------|---------------|
| Package | java.util.Collections | java.util.Arrays |
| Used For | List | Arrays |
| Supports ArrayList | ✅ Yes | ❌ No |
| Supports LinkedList | ✅ Yes | ❌ No |
| Supports Arrays | ❌ No | ✅ Yes |
| Comparable Support | ✅ Yes | ✅ Yes |
| Comparator Support | ✅ Yes | ✅ Yes (Object Arrays) |
| Internal Algorithm | TimSort | Dual-Pivot QuickSort (Primitives), TimSort (Objects) |

---

# 📖 When Should You Use Collections.sort()?

Use Collections.sort() when working with:

- ArrayList
- LinkedList
- Vector
- Stack
- Any List implementation

Example

```java
ArrayList<Integer> list = new ArrayList<>();

Collections.sort(list);
```

---

# 📖 When Should You Use Arrays.sort()?

Use Arrays.sort() when working with arrays.

Example

```java
int[] arr = {5, 3, 1, 8};

Arrays.sort(arr);
```

Output

```text
1 3 5 8
```

---

# 📖 Collections.sort() with Comparator

```java
Collections.sort(

    students,

    Comparator.comparing(Student::getMarks)

);
```

---

# 📖 Collections.sort() with Lambda

```java
Collections.sort(

    students,

    (s1, s2) -> Integer.compare(

        s1.getRollNo(),

        s2.getRollNo()

    )

);
```

---

# 📖 Collections.sort() with Method Reference

```java
Collections.sort(

    students,

    Comparator.comparing(Student::getName)

);
```

---

# 📖 Descending Order

```java
Collections.sort(

    list,

    Collections.reverseOrder()

);
```

Output

```text
90

70

50

20
```

---

# 📊 Internal Working

### Without Comparator

```text
Collections.sort()

↓

compareTo()

↓

TimSort

↓

Sorted List
```

---

### With Comparator

```text
Collections.sort()

↓

compare()

↓

TimSort

↓

Sorted List
```

---

# 🌍 Real-World Applications

Collections.sort() is widely used in:

- Student Management Systems
- Employee Management Systems
- Banking Applications
- E-Commerce Platforms
- Hospital Management Systems
- Library Management Systems
- Hotel Booking Systems
- Online Shopping Applications

---

# ✅ Advantages

- Easy to use.
- Built into the Java Collections Framework.
- Stable sorting algorithm.
- Highly optimized.
- Supports Comparable.
- Supports Comparator.
- Supports Lambda Expressions.
- Supports Method References.

---

# ⚠️ Limitations

- Works only with List implementations.
- Requires Comparable or Comparator for custom objects.
- Uses extra memory because of TimSort.
- Cannot sort primitive arrays directly.

---

# ⚠️ Common Mistakes

## ❌ Using Collections.sort() with Arrays

Wrong

```java
int[] arr = {4,2,1};

Collections.sort(arr);
```

Correct

```java
Arrays.sort(arr);
```

---

## ❌ Forgetting Comparable

Wrong

```java
Collections.sort(studentList);
```

when Student does not implement Comparable.

Result

```text
ClassCastException
```

---

## ❌ Returning Boolean

Wrong

```java
return s1.id > s2.id;
```

Correct

```java
return Integer.compare(

    s1.id,

    s2.id

);
```

---

## ❌ Comparing Strings Incorrectly

Wrong

```java
return s1.name - s2.name;
```

Correct

```java
return s1.name.compareTo(s2.name);
```

---

## ❌ Using Subtraction

Wrong

```java
return s1.salary - s2.salary;
```

Correct

```java
return Integer.compare(

    s1.salary,

    s2.salary

);
```

---

# 💡 Best Practices

- Use Collections.sort() for Lists.
- Use Arrays.sort() for arrays.
- Use Comparable for natural ordering.
- Use Comparator for custom ordering.
- Prefer `Comparator.comparing()` in Java 8+.
- Prefer Lambda Expressions over anonymous classes.
- Use Method References whenever possible.
- Use `thenComparing()` for multiple sorting criteria.

---

# 🧩 Interview Questions

## Beginner

1. What is Collections.sort()?
2. Which package contains Collections.sort()?
3. Can Collections.sort() sort arrays?
4. Which interface is required for default sorting?
5. Which algorithm does Collections.sort() use?

---

## Intermediate

6. Difference between Collections.sort() and Arrays.sort().
7. Difference between Comparable and Comparator.
8. Why is TimSort used?
9. Is Collections.sort() stable?
10. Can Collections.sort() sort custom objects?

---

## Advanced

11. Explain the internal working of Collections.sort().
12. How does Collections.sort() use compareTo()?
13. How does Collections.sort() use compare()?
14. Why is TimSort efficient for partially sorted data?
15. Can Collections.sort() work with Lambda Expressions?

---

# 🎓 MCQs

### Q1. Collections.sort() belongs to:

- A. Arrays
- B. Collections ✅
- C. Objects
- D. Math

---

### Q2. Collections.sort() is mainly used for:

- A. Arrays
- B. Lists ✅
- C. Strings
- D. Files

---

### Q3. Collections.sort() internally uses:

- A. Bubble Sort
- B. Quick Sort
- C. TimSort ✅
- D. Heap Sort

---

### Q4. Which interface is used for default sorting?

- A. Comparator
- B. Comparable ✅
- C. Runnable
- D. Cloneable

---

### Q5. Which method is used for descending order?

- A. reverse()
- B. descending()
- C. Collections.reverseOrder() ✅
- D. reverseComparator()

---

# 📝 Quick Revision

## Collections.sort()

```text
Collections.sort(list)

↓

TimSort

↓

Sorted List
```

---

## Custom Object Sorting

```text
Comparable

↓

compareTo()

----------------------

Comparator

↓

compare()
```

---

## Descending Order

```java
Collections.sort(

    list,

    Collections.reverseOrder()

);
```

---

## Properties

```text
Works with List

✅

Stable

✅

Uses TimSort

✅

Supports Comparable

✅

Supports Comparator

✅

Supports Lambda

✅
```

---

# 🧪 Practice Problems

## Beginner

- Sort an ArrayList of Integers.
- Sort an ArrayList of Strings.
- Sort a LinkedList of Integers.
- Sort a Vector.

---

## Intermediate

- Sort students by Roll Number using Comparable.
- Sort students by Name using Comparator.
- Sort employees by Salary.
- Sort products by Price.

---

## Advanced

- Sort students by Marks and then by Name.
- Sort objects using Lambda Expressions.
- Sort objects using Method References.
- Build a reusable Comparator library.
- Compare the performance of Collections.sort() and Arrays.sort().

---

# 🔗 Related Topics

- Arrays.sort()
- Comparable Interface
- Comparator Interface
- Lambda Expressions
- Method References
- Generics
- List Interface
- Stream API

---

# 📚 References

- Oracle Java Documentation
- Effective Java by Joshua Bloch
- Java: The Complete Reference
- OpenJDK Documentation
- GeeksforGeeks

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 03: Collections.sort()**.

### ✔️ Concepts Covered

- Collections.sort()
- Sorting Lists
- Ascending & Descending Sorting
- Comparable
- Comparator
- Lambda Expressions
- Method References
- TimSort
- Collections.sort() vs Arrays.sort()
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ `Collections.sort()` is used to sort **List** implementations.
- ✅ It belongs to the **java.util.Collections** class.
- ✅ It internally uses **TimSort**, which is stable and efficient.
- ✅ Custom objects can be sorted using **Comparable** or **Comparator**.
- ✅ Java 8 introduced **Lambda Expressions** and **Method References**, making sorting code shorter and cleaner.
- ✅ Use **Collections.reverseOrder()** for descending order sorting.
- ✅ Use **Arrays.sort()** when working with arrays instead of Lists.

---

# 🚀 Next Chapter

➡️ **04-Comparable-Interface.md**

### Topics Covered

- What is Comparable?
- compareTo() Method
- Natural Ordering
- Comparable vs Comparator
- Sorting Custom Objects
- Interview Questions
- Practice Problems