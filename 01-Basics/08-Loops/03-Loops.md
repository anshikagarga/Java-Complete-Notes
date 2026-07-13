# 📘 Chapter 8: Loops in Java (Part 3)

## Interview Preparation, Best Practices & Revision

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Compare all loop types in Java.
- Analyze the time and space complexity of loops.
- Choose the appropriate loop for different scenarios.
- Answer interview questions confidently.
- Revise the complete Loops chapter.

---

# 📚 Table of Contents

1. JVM Execution Flow
2. Time & Space Complexity
3. Loop Comparison
4. Real-World Applications
5. Common Mistakes
6. Best Practices
7. Interview Questions
8. Quick Revision
9. Practice Problems
10. Related Topics
11. References
12. Chapter Summary

---

# 🧠 JVM Execution Flow

Example

```java
for(int i = 1; i <= 3; i++){

    System.out.println(i);

}
```

Execution Flow

```text
Program Starts

      │

      ▼

Initialization

i = 1

      │

      ▼

Condition

i <= 3

      │

 ┌────┴────┐
 │         │

True     False

 │         │

 ▼         ▼

Execute    Exit

 │

 ▼

Update (i++)

 │

 └────────────► Condition Again
```

---

# 📦 Memory Diagram

```text
Stack Memory

--------------------

i = 1

↓

Print

↓

i = 2

↓

Print

↓

i = 3

↓

Print

↓

i = 4

↓

Condition False

↓

Loop Ends
```

---

# ⚡ Time & Space Complexity

## while Loop

```java
while(i < n)
```

| Time | Space |
|------|-------|
| O(n) | O(1) |

---

## do-while Loop

```java
do{

}while(i < n);
```

| Time | Space |
|------|-------|
| O(n) | O(1) |

---

## for Loop

```java
for(int i=0;i<n;i++)
```

| Time | Space |
|------|-------|
| O(n) | O(1) |

---

## Nested Loops

```java
for(...){

    for(...){

    }

}
```

| Time | Space |
|------|-------|
| O(n²) | O(1) |

---

## Triple Nested Loops

```java
for(){

    for(){

        for(){

        }

    }

}
```

| Time | Space |
|------|-------|
| O(n³) | O(1) |

---

# 🌍 Real-World Applications

## Banking System

```java
for(Transaction t : transactions){

    process(t);

}
```

---

## Social Media

```java
while(hasMorePosts){

    loadNextPost();

}
```

---

## Gaming

```java
while(gameRunning){

    updateGame();

}
```

---

## E-Commerce

```java
for(Product product : products){

    display(product);

}
```

---

## Data Processing

```java
for(int row = 0; row < matrix.length; row++){

    for(int col = 0; col < matrix[0].length; col++){

    }

}
```

Nested loops are commonly used in matrix operations.

---

# 📊 Complete Comparison

| Feature | while | do-while | for | Enhanced for |
|----------|--------|-----------|------|--------------|
| Condition Before Execution | ✅ | ❌ | ✅ | ✅ |
| Executes At Least Once | ❌ | ✅ | ❌ | ❌ |
| Initialization Inside Loop | ❌ | ❌ | ✅ | ✅ |
| Best for Arrays | ❌ | ❌ | ✅ | ✅ |
| Uses Index | Optional | Optional | ✅ | ❌ |
| Modify Elements Easily | ✅ | ✅ | ✅ | ❌ |
| Collections Support | ❌ | ❌ | ✅ | ✅ |

---

# 🎯 When Should You Use Which Loop?

### Use `for`

✔ Number of iterations is known.

Examples

- Print numbers
- Traverse arrays using index
- Counting

---

### Use `while`

✔ Number of iterations is unknown.

Examples

- Login systems
- Waiting for user input
- File reading
- Network connections

---

### Use `do-while`

✔ Code must execute at least once.

Examples

- ATM menu
- Restaurant ordering system
- Game menu

---

### Use Enhanced `for`

✔ Reading arrays or collections.

Examples

- Product list
- Student records
- Employee database

---

# ⚠️ Common Mistakes

## ❌ Infinite Loop

```java
while(true){

}
```

Unless there is a `break`, this loop never ends.

---

## ❌ Off-by-One Error

Wrong

```java
for(int i = 1; i <= array.length; i++)
```

Correct

```java
for(int i = 0; i < array.length; i++)
```

---

## ❌ Missing Update

```java
int i = 1;

while(i <= 10){

    System.out.println(i);

}
```

Infinite loop because `i` never changes.

---

## ❌ Modifying Collection During Enhanced for

```java
for(String name : names){

    names.remove(name);

}
```

This can throw a `ConcurrentModificationException`.

---

## ❌ Confusing break and continue

```
break

↓

Exit Loop
```

```
continue

↓

Skip Current Iteration
```

---

# 💡 Best Practices

- Use meaningful loop variable names (`index`, `count`, `row`, `column`).
- Keep loop conditions simple.
- Avoid unnecessary nested loops.
- Use Enhanced `for` for read-only traversal.
- Prefer `break` over complex boolean flags when appropriate.
- Always verify loop termination conditions.

---

# 💼 Interviewer's Notes

Interviewers commonly ask:

- Difference between `while` and `for`.
- Difference between `while` and `do-while`.
- Difference between `break` and `continue`.
- Difference between `for` and Enhanced `for`.
- Why does `do-while` execute at least once?
- Explain Nested Loops.
- What causes an infinite loop?
- What is an off-by-one error?
- When should you use an Enhanced `for` loop?
- Can you modify an array using an Enhanced `for` loop?
- Why can't you safely remove elements from a collection inside an Enhanced `for` loop?

Always explain using a small code example.

---

# 🧩 Interview Questions

## Beginner

1. What is a loop?
2. Why do we need loops?
3. What are the different types of loops in Java?
4. Difference between `while` and `for`.
5. Difference between `while` and `do-while`.

---

## Intermediate

6. What is an Enhanced `for` loop?
7. Difference between `break` and `continue`.
8. What is a Nested Loop?
9. Explain labeled loops.
10. What is an infinite loop?

---

## Advanced

11. Explain JVM execution of a `for` loop.
12. Can a `for` loop be written without initialization?
13. What happens if the update expression is omitted?
14. Why can't we modify collection structure during Enhanced `for` iteration?
15. Explain loop complexity with examples.

---

# 📝 Quick Revision

## Types of Loops

```text
Loops

↓

while

↓

do-while

↓

for

↓

Enhanced for
```

---

## while

```java
while(condition){

}
```

Condition checked first.

---

## do-while

```java
do{

}while(condition);
```

Body executes first.

---

## for

```java
for(initialization; condition; update){

}
```

Best when iterations are known.

---

## Enhanced for

```java
for(int num : numbers){

}
```

Best for traversing arrays and collections.

---

## break

```
Exit Loop
```

---

## continue

```
Skip Current Iteration
```

---

# 🧪 Practice Problems

## Beginner

1. Print numbers from 1 to 100.
2. Print even numbers from 1 to 50.
3. Print multiplication tables.
4. Find the sum of the first N natural numbers.

---

## Intermediate

5. Reverse a number.
6. Check whether a number is a palindrome.
7. Print star patterns.
8. Find the factorial of a number.
9. Generate the Fibonacci series.

---

## Advanced

10. Traverse a 2D array using nested loops.
11. Print Pascal's Triangle.
12. Build a menu-driven ATM using a `do-while` loop.
13. Implement matrix addition and multiplication.
14. Simulate a simple game loop using `while`.

---

# 🏆 LeetCode Practice

## Easy

- 1480. Running Sum of 1d Array
- 1920. Build Array from Permutation
- 1295. Find Numbers with Even Number of Digits
- 412. Fizz Buzz

## Medium

- 7. Reverse Integer
- 9. Palindrome Number
- 50. Pow(x, n)
- 54. Spiral Matrix

## Advanced

- 48. Rotate Image
- 73. Set Matrix Zeroes
- 59. Spiral Matrix II

---

# 🔗 Related Topics

- Variables
- Operators
- Conditional Statements
- Arrays
- Methods
- Collections
- Recursion

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java — Joshua Bloch
- OpenJDK Documentation

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **Chapter 8: Loops in Java**.

### ✔️ Concepts Covered

- while Loop
- do-while Loop
- for Loop
- Enhanced for Loop
- Nested Loops
- Labeled Loops
- break Statement
- continue Statement
- JVM Execution Flow
- Time & Space Complexity
- Interview Questions
- Best Practices
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Use **for** when the number of iterations is known.
- ✅ Use **while** when the number of iterations is unknown.
- ✅ Use **do-while** when the loop must execute at least once.
- ✅ Use **Enhanced for** for read-only traversal of arrays and collections.
- ✅ Use **break** to terminate a loop immediately.
- ✅ Use **continue** to skip the current iteration.
- ✅ Always update loop variables to avoid infinite loops.
- ✅ Be careful with loop boundaries to avoid off-by-one errors.

➡️ **Next Chapter:** `09-Class and Object.md`