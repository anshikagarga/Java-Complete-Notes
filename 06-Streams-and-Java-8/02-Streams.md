# 📘 Chapter 06: Streams and Java 8 (Part 2)

## Stream API, Intermediate Operations & Terminal Operations

> *"The Stream API allows developers to process collections in a declarative, readable, and efficient way without modifying the original data source."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the Stream API.
- Learn how Streams work internally.
- Understand Intermediate Operations.
- Understand Terminal Operations.
- Learn `filter()`, `map()`, `sorted()`, `distinct()`, `limit()`, `skip()`.
- Learn `collect()`, `reduce()`, `count()`, `findFirst()`, `anyMatch()`, etc.
- Understand Lazy Evaluation.

---

# 📚 Table of Contents

1. What is Stream API?
2. How Streams Work
3. Creating Streams
4. Intermediate Operations
5. Terminal Operations
6. Lazy Evaluation
7. Stream Pipeline
8. Internal Working
9. Best Practices
10. Common Mistakes

---

# 📖 What is Stream API?

The **Stream API** was introduced in **Java 8** to process collections in a functional and declarative manner.

A stream:

- Does **not** store data.
- Processes data from a source.
- Supports chaining operations.
- Can be processed sequentially or in parallel.

---

# 📖 Stream Pipeline

A stream generally consists of three stages.

```text
Source

↓

Intermediate Operations

↓

Terminal Operation

↓

Result
```

Example

```java
list.stream()

    .filter(x -> x > 10)

    .map(x -> x * 2)

    .forEach(System.out::println);
```

---

# 📖 Creating Streams

## From Collection

```java
List<String> list = List.of("Java", "Python", "C++");

Stream<String> stream = list.stream();
```

---

## From Array

```java
String[] languages = {"Java", "Python", "C++"};

Arrays.stream(languages)
      .forEach(System.out::println);
```

---

## Using Stream.of()

```java
Stream.of(10, 20, 30, 40)
      .forEach(System.out::println);
```

---

# 📖 Intermediate Operations

Intermediate operations return another **Stream**.

They are **lazy**, meaning they do not execute until a terminal operation is called.

Common Intermediate Operations

| Method | Purpose |
|---------|---------|
| `filter()` | Filters elements |
| `map()` | Transforms elements |
| `sorted()` | Sorts elements |
| `distinct()` | Removes duplicates |
| `limit()` | Limits elements |
| `skip()` | Skips elements |
| `peek()` | Performs an action while debugging |

---

# 📖 filter()

Selects elements based on a condition.

Example

```java
List<Integer> numbers = List.of(10, 15, 20, 25, 30);

numbers.stream()

       .filter(x -> x > 20)

       .forEach(System.out::println);
```

Output

```text
25
30
```

---

# 📖 map()

Transforms each element into another form.

Example

```java
List<String> names = List.of("java", "python");

names.stream()

     .map(String::toUpperCase)

     .forEach(System.out::println);
```

Output

```text
JAVA
PYTHON
```

---

# 📖 sorted()

Sorts the stream.

Example

```java
List<Integer> list = List.of(40, 10, 30, 20);

list.stream()

    .sorted()

    .forEach(System.out::println);
```

Output

```text
10
20
30
40
```

Descending Order

```java
list.stream()

    .sorted(Comparator.reverseOrder())

    .forEach(System.out::println);
```

---

# 📖 distinct()

Removes duplicate elements.

Example

```java
List<Integer> list = List.of(10, 20, 10, 30, 20);

list.stream()

    .distinct()

    .forEach(System.out::println);
```

Output

```text
10
20
30
```

---

# 📖 limit()

Returns only the first **N** elements.

Example

```java
Stream.of(10, 20, 30, 40, 50)

      .limit(3)

      .forEach(System.out::println);
```

Output

```text
10
20
30
```

---

# 📖 skip()

Skips the first **N** elements.

Example

```java
Stream.of(10, 20, 30, 40)

      .skip(2)

      .forEach(System.out::println);
```

Output

```text
30
40
```

---

# 📖 Terminal Operations

Terminal operations produce the final result and end the stream pipeline.

Common Terminal Operations

| Method | Purpose |
|---------|---------|
| `forEach()` | Iterates over elements |
| `collect()` | Collects results |
| `reduce()` | Reduces to a single value |
| `count()` | Counts elements |
| `findFirst()` | Finds the first element |
| `findAny()` | Finds any element |
| `anyMatch()` | Checks if any element matches |
| `allMatch()` | Checks if all elements match |
| `noneMatch()` | Checks if no element matches |

---

# 📖 collect()

Collects stream elements into a collection.

Example

```java
List<String> result =

    List.of("java", "python")

        .stream()

        .map(String::toUpperCase)

        .collect(Collectors.toList());

System.out.println(result);
```

Output

```text
[JAVA, PYTHON]
```

---

# 📖 reduce()

Combines all elements into a single result.

Example

```java
int sum =

    List.of(10, 20, 30)

        .stream()

        .reduce(0, Integer::sum);

System.out.println(sum);
```

Output

```text
60
```

---

# 📖 count()

Counts the elements.

Example

```java
long count =

    List.of(10, 20, 30)

        .stream()

        .count();

System.out.println(count);
```

Output

```text
3
```

---

# 📖 findFirst()

Returns the first element wrapped in an `Optional`.

Example

```java
Optional<Integer> first =

    List.of(10, 20, 30)

        .stream()

        .findFirst();

System.out.println(first.get());
```

Output

```text
10
```

> Prefer `orElse()` or `orElseThrow()` over `get()` in production code to avoid exceptions when the stream is empty.

---

# 📖 anyMatch()

Checks if at least one element satisfies the condition.

Example

```java
boolean result =

    List.of(10, 20, 30)

        .stream()

        .anyMatch(x -> x > 25);

System.out.println(result);
```

Output

```text
true
```

---

# 📖 allMatch()

Checks whether all elements satisfy the condition.

```java
boolean result =

    List.of(10, 20, 30)

        .stream()

        .allMatch(x -> x > 5);

System.out.println(result);
```

Output

```text
true
```

---

# 📖 noneMatch()

Checks whether no elements satisfy the condition.

```java
boolean result =

    List.of(10, 20, 30)

        .stream()

        .noneMatch(x -> x < 0);

System.out.println(result);
```

Output

```text
true
```

---

# 📖 Lazy Evaluation

Intermediate operations are **lazy**.

Nothing executes until a terminal operation is encountered.

Example

```java
list.stream()

    .filter(x -> x > 10)

    .map(x -> x * 2);
```

No output is produced because there is no terminal operation.

Now

```java
list.stream()

    .filter(x -> x > 10)

    .map(x -> x * 2)

    .forEach(System.out::println);
```

The pipeline executes.

---

# 📦 Internal Working

```text
Collection

↓

stream()

↓

filter()

↓

map()

↓

sorted()

↓

collect()

↓

Result
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting a Terminal Operation

Wrong

```java
list.stream()

    .filter(x -> x > 10);
```

Nothing happens.

Correct

```java
list.stream()

    .filter(x -> x > 10)

    .forEach(System.out::println);
```

---

## ❌ Reusing a Stream

Wrong

```java
Stream<Integer> stream = list.stream();

stream.count();

stream.forEach(System.out::println);
```

Output

```text
IllegalStateException
```

A stream can be consumed only once.

---

## ❌ Modifying the Source During Stream Processing

Avoid changing the underlying collection while the stream is operating on it, as it can lead to unexpected behavior or exceptions.

---

# 💡 Best Practices

- Keep stream pipelines readable.
- Prefer method references where appropriate.
- Use streams for data processing, not for complex side effects.
- Avoid reusing streams after a terminal operation.
- Prefer `Optional` methods like `orElse()` instead of directly calling `get()`.
- Choose parallel streams only after measuring performance.

---

# 🌍 Real-World Applications

The Stream API is used in:

- Spring Boot Applications
- REST APIs
- Data Filtering
- Report Generation
- Payroll Systems
- Banking Applications
- E-Commerce Platforms
- Analytics Dashboards

---

# 🎯 Interview Tip

### Question

What is the difference between Intermediate and Terminal Operations?

### Answer

| Intermediate Operations | Terminal Operations |
|-------------------------|--------------------|
| Return another Stream | Produce the final result |
| Lazy execution | Trigger stream execution |
| Can be chained | End the stream pipeline |
| Examples: `filter()`, `map()`, `sorted()` | Examples: `collect()`, `reduce()`, `count()`, `forEach()` |

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Optional Class
- Date & Time API
- Default Methods
- Static Methods in Interfaces
- Parallel Streams
- Interview Questions
- MCQs
- Practice Problems
- Chapter Summary