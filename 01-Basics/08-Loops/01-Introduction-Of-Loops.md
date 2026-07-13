# 📘 Chapter 8: Loops in Java (Part 1)

> "Loops allow a program to execute a block of code repeatedly until a specified condition becomes false."

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand why loops are needed.
- Learn different types of loops in Java.
- Understand the `while` loop.
- Learn the `do-while` loop.
- Compare `while` and `do-while`.
- Understand JVM execution flow.
- Solve beginner-level looping problems.

---

# 📚 Table of Contents

1. Why do we need Loops?
2. What are Loops?
3. Types of Loops
4. while Loop
5. do-while Loop
6. Difference between while & do-while
7. JVM Execution Flow
8. Memory Diagram
9. Beginner Examples
10. Real-World Examples
11. Common Mistakes
12. Best Practices
13. Interview Questions
14. Quick Revision
15. Practice Problems
16. Related Topics
17. References

---

# 🤔 Why do we need Loops?

Imagine you want to print

```
Hello Java
```

100 times.

Without loops

```java
System.out.println("Hello Java");
System.out.println("Hello Java");
System.out.println("Hello Java");
...
```

The code becomes repetitive and difficult to maintain.

Instead,

```java
for(int i = 1; i <= 100; i++){

    System.out.println("Hello Java");

}
```

Loops make programs shorter, cleaner, and more efficient.

---

# 📖 What is a Loop?

A **Loop** is a control statement that repeatedly executes a block of code until a specified condition becomes false.

A loop consists of three main parts:

- Initialization
- Condition
- Update

---

# 📚 Types of Loops

Java provides three main looping statements.

```text
                Loops
                  │
      ┌───────────┼────────────┐
      │           │            │
    while       do-while      for
                               │
                        Enhanced for
```

---

# 🔄 Loop Life Cycle

Every loop follows the same execution pattern.

```text
Initialization

      │

      ▼

Condition

      │

 ┌────┴────┐
 │         │

True     False
 │         │

 ▼         ▼

Execute   Exit

 │

 ▼

Update

 │

 └──────────────► Condition
```

---

# 📖 while Loop

The `while` loop executes as long as the condition is `true`.

If the condition becomes `false`, the loop terminates.

---

# 📝 Syntax

```java
while(condition){

    // code

}
```

---

# 💻 Beginner Example

```java
int i = 1;

while(i <= 5){

    System.out.println(i);

    i++;

}
```

Output

```
1
2
3
4
5
```

---

# 🧠 JVM Internal Working

Program

```java
int i = 1;

while(i <= 3){

    System.out.println(i);

    i++;

}
```

Execution

```text
i = 1

↓

Check Condition

↓

True

↓

Print 1

↓

i++

↓

Check Condition

↓

True

↓

Print 2

↓

i++

↓

Check Condition

↓

True

↓

Print 3

↓

i++

↓

Condition False

↓

Loop Ends
```

---

# 📦 Memory Diagram

```text
Stack Memory

----------------

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

Exit
```

---

# 🌍 Real-World Example

ATM PIN Verification

```java
int attempts = 1;

while(attempts <= 3){

    System.out.println("Enter PIN");

    attempts++;

}
```

---

# 📖 do-while Loop

The `do-while` loop executes the block **at least once**, even if the condition is `false`.

The condition is checked **after** executing the loop body.

---

# 📝 Syntax

```java
do{

    // code

}while(condition);
```

---

# 💻 Beginner Example

```java
int i = 1;

do{

    System.out.println(i);

    i++;

}while(i <= 5);
```

Output

```
1
2
3
4
5
```

---

# 🧠 JVM Internal Working

```text
Start

↓

Execute Body

↓

Check Condition

↓

True?

↓

Yes

↓

Repeat

↓

No

↓

Exit
```

---

# 📦 Memory Diagram

```text
Stack

i = 1

↓

Execute

↓

i = 2

↓

Condition

↓

Repeat
```

---

# 💻 Example Showing the Difference

### while

```java
int i = 10;

while(i <= 5){

    System.out.println(i);

}
```

Output

```
No Output
```

---

### do-while

```java
int i = 10;

do{

    System.out.println(i);

}while(i <= 5);
```

Output

```
10
```

Reason

The `do-while` loop executes once before checking the condition.

---

# 📊 while vs do-while

| Feature | while | do-while |
|----------|--------|-----------|
| Condition Checked | Before Execution | After Execution |
| Executes At Least Once | ❌ No | ✅ Yes |
| Semicolon Required | ❌ | ✅ Yes |
| Suitable For | Unknown iterations | Menu-driven programs |

---

# 🌍 Real-World Applications

### Login System

```java
while(!authenticated){

    login();

}
```

---

### ATM Machine

```java
do{

    showMenu();

}while(choice != 4);
```

---

### Game Loop

```java
while(gameRunning){

    updateGame();

}
```

---

### Download Manager

```java
while(fileRemaining){

    downloadChunk();

}
```

---

# ⚠️ Common Mistakes

## ❌ Forgetting Update

```java
int i = 1;

while(i <= 5){

    System.out.println(i);

}
```

Infinite Loop

---

## ❌ Using Assignment Instead of Comparison

Wrong

```java
while(flag = true)
```

Correct

```java
while(flag == true)
```

or simply

```java
while(flag)
```

---

## ❌ Forgetting Semicolon in do-while

Wrong

```java
}while(i <= 5)
```

Correct

```java
}while(i <= 5);
```

---

# 💡 Best Practices

- Always update the loop variable.
- Avoid infinite loops unless intentionally required.
- Keep loop conditions simple.
- Use meaningful variable names (`count`, `index`, `attempts`).
- Prefer `for` loops when the number of iterations is known.

---

# 🎯 Interview Tip

Remember:

```text
while

↓

Condition First

↓

Execution
```

```text
do-while

↓

Execution First

↓

Condition
```

This is one of the most frequently asked Java interview questions.

---

➡️ **Next Part (Part 2):**

- `for` Loop
- Enhanced `for` Loop (for-each)
- Nested Loops
- Labeled Loops
- `break` Statement
- `continue` Statement
- JVM Execution Flow