# 📘 Chapter 06: Lambda with Comparator (Part 1)

> *"Java 8 introduced Lambda Expressions, making Comparator implementations much shorter, cleaner, and easier to read. Instead of creating anonymous classes, we can now write sorting logic in a single line."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Lambda Expressions.
- Learn why Lambda is used with Comparator.
- Compare Traditional Comparator vs Lambda Comparator.
- Sort collections using Lambda Expressions.
- Sort in ascending and descending order.
- Learn different Comparator methods introduced in Java 8.

---

# 📚 Table of Contents

1. Introduction
2. What is Lambda Expression?
3. Why Lambda with Comparator?
4. Traditional Comparator
5. Lambda Comparator
6. Ascending Sorting
7. Descending Sorting
8. Comparator Utility Methods
9. Internal Working
10. Best Practices

---

# 📖 What is a Lambda Expression?

A **Lambda Expression** is an anonymous function introduced in **Java 8**.

It allows us to write functional programming style code.

General Syntax

```java
(parameters) -> expression
```

or

```java
(parameters) -> {

    statements;

}
```

Example

```java
(a, b) -> a + b
```

---

# 📖 Why Use Lambda with Comparator?

Before Java 8, sorting required creating an anonymous Comparator class.

Example

```java
Collections.sort(list, new Comparator<Integer>() {

    @Override
    public int compare(Integer a, Integer b) {

        return a.compareTo(b);

    }

});
```

This code is lengthy.

Using Lambda

```java
Collections.sort(list,

(a, b) -> a.compareTo(b));
```

Much cleaner and easier to understand.

---

# 📖 Traditional Comparator

Example

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        List<Integer> list =

        Arrays.asList(50,20,40,10);

        Collections.sort(list,

        new Comparator<Integer>() {

            @Override

            public int compare(Integer a, Integer b) {

                return a.compareTo(b);

            }

        });

        System.out.println(list);

    }

}
```

Output

```text
[10, 20, 40, 50]
```

---

# 📖 Lambda Comparator

The same program becomes much shorter.

```java
import java.util.*;

public class Demo {

    public static void main(String[] args) {

        List<Integer> list =

        Arrays.asList(50,20,40,10);

        Collections.sort(

        list,

        (a,b) -> a.compareTo(b)

        );

        System.out.println(list);

    }

}
```

Output

```text
[10, 20, 40, 50]
```

---

# 📖 Sorting in Ascending Order

Example

```java
List<Integer> list =

Arrays.asList(9,3,7,1,5);

list.sort(

(a,b) -> a.compareTo(b)

);

System.out.println(list);
```

Output

```text
[1,3,5,7,9]
```

---

# 📖 Sorting in Descending Order

Example

```java
List<Integer> list =

Arrays.asList(9,3,7,1,5);

list.sort(

(a,b) -> b.compareTo(a)

);

System.out.println(list);
```

Output

```text
[9,7,5,3,1]
```

---

# 📖 Using Comparator.reverseOrder()

Instead of writing custom logic,

Java provides

```java
Comparator.reverseOrder()
```

Example

```java
List<Integer> list =

Arrays.asList(9,3,7,1);

list.sort(

Comparator.reverseOrder()

);

System.out.println(list);
```

Output

```text
[9,7,3,1]
```

---

# 📖 Comparator.naturalOrder()

Sorts data in ascending order.

Example

```java
list.sort(

Comparator.naturalOrder()

);
```

Output

```text
[1,3,7,9]
```

---

# 📖 Comparator Utility Methods

Java 8 provides many useful Comparator methods.

| Method | Purpose |
|---------|----------|
| `naturalOrder()` | Ascending order |
| `reverseOrder()` | Descending order |
| `comparing()` | Sort by object field |
| `thenComparing()` | Secondary sorting |
| `reversed()` | Reverse existing Comparator |
| `nullsFirst()` | Null values first |
| `nullsLast()` | Null values last |

---

# 📦 Internal Working

```text
Collection

↓

Comparator

↓

Lambda Expression

↓

compare()

↓

Sorting Algorithm

↓

Sorted Collection
```

---

# 💡 Best Practices

- Use Lambda Expressions instead of anonymous Comparator classes.
- Use `Comparator.naturalOrder()` and `Comparator.reverseOrder()` whenever possible.
- Prefer `Integer.compare()` over subtraction (`a - b`) for integer comparisons.
- Keep Lambda expressions short and readable.
- Use method references where appropriate.

---

# 🌍 Real-World Applications

Lambda with Comparator is widely used in:

- Employee Management Systems
- Student Ranking Systems
- Banking Applications
- E-Commerce Product Sorting
- Airline Booking Systems
- Hospital Management
- Spring Boot Applications

---

# 🎯 Interview Tip

### Question

Why is Lambda preferred over an anonymous Comparator class?

### Answer

Because Lambda Expressions reduce boilerplate code, improve readability, make Comparator implementations concise, and work seamlessly with Java 8 Functional Programming features.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Comparator.comparing()
- thenComparing()
- reversed()
- nullsFirst()
- nullsLast()
- Sorting Objects using Lambda
- Method References with Comparator