# 📘 Chapter 8: Loops in Java (Part 2)

## for Loop, Enhanced for Loop, Nested Loops, break & continue

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Understand the `for` loop.
- Learn the Enhanced `for` (for-each) loop.
- Understand Nested Loops.
- Learn Labeled Loops.
- Understand `break` and `continue`.
- Learn JVM execution flow.
- Solve common looping problems.

---

# 📚 Table of Contents

1. for Loop
2. Enhanced for Loop
3. Nested Loops
4. Labeled Loops
5. break Statement
6. continue Statement
7. JVM Internal Working
8. Memory Diagram
9. Real-World Examples
10. Common Mistakes
11. Best Practices

---

# 🤔 Why do we need a for Loop?

The `for` loop is used when the number of iterations is known in advance.

Example:

- Print numbers from 1 to 100
- Print multiplication tables
- Traverse arrays
- Repeat a task a fixed number of times

Unlike `while`, all loop components are written in one place, making the code more readable.

---

# 📖 What is a for Loop?

The `for` loop combines:

- Initialization
- Condition
- Update

into a single statement.

---

# 📝 Syntax

```java
for(initialization; condition; update){

    // code

}
```

---

# 🔄 Flow Diagram

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
 └────────► Condition
```

---

# 💻 Beginner Example

```java
for(int i = 1; i <= 5; i++){

    System.out.println(i);

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

```java
for(int i = 1; i <= 3; i++){

    System.out.println(i);

}
```

Execution

```text
Initialize i = 1

↓

Condition

↓

True

↓

Print 1

↓

i++

↓

Condition

↓

Print 2

↓

i++

↓

Condition

↓

Print 3

↓

i++

↓

Condition False

↓

Exit
```

---

# 📦 Memory Diagram

```text
Stack Memory

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

Exit
```

---

# 🌍 Real-World Example

Printing customer IDs

```java
for(int customerId = 1; customerId <= 100; customerId++){

    System.out.println(customerId);

}
```

---

# 📖 Enhanced for Loop (for-each)

Introduced to simplify traversing arrays and collections.

It automatically accesses each element one by one.

---

# 📝 Syntax

```java
for(dataType variable : collection){

    // code

}
```

---

# 💻 Example

```java
int numbers[] = {10,20,30,40};

for(int num : numbers){

    System.out.println(num);

}
```

Output

```
10
20
30
40
```

---

# 🧠 JVM Execution

```text
Array

↓

First Element

↓

Print

↓

Second Element

↓

Print

↓

Continue until End
```

---

# 🌍 Real-World Example

Displaying all products

```java
String[] products = {

"Laptop",

"Phone",

"Keyboard"

};

for(String product : products){

    System.out.println(product);

}
```

---

# 📖 Traditional for vs Enhanced for

| Feature | Traditional for | Enhanced for |
|----------|-----------------|--------------|
| Uses Index | ✅ | ❌ |
| Easy to Modify Elements | ✅ | ❌ |
| Traversal | Manual | Automatic |
| Best For | Arrays & Index-based Logic | Reading Arrays & Collections |

---

# 📖 Nested Loops

A loop inside another loop is called a **Nested Loop**.

---

## Syntax

```java
for(){

    for(){

    }

}
```

---

# 💻 Example

```java
for(int i = 1; i <= 3; i++){

    for(int j = 1; j <= 2; j++){

        System.out.println(i + " " + j);

    }

}
```

Output

```
1 1

1 2

2 1

2 2

3 1

3 2
```

---

# 🧠 JVM Execution

```text
Outer Loop

↓

Inner Loop

↓

Inner completes

↓

Outer increments

↓

Inner starts again
```

---

# 🌍 Real-World Applications

Nested loops are commonly used for:

- Matrix Operations
- Pattern Printing
- Chess Boards
- Sudoku
- Seating Arrangement
- Game Development

---

# 📖 Labeled Loops

Java allows naming a loop using a **label**.

A labeled loop is useful when you need to control an outer loop from within an inner loop.

---

# 💻 Example

```java
outer:

for(int i = 1; i <= 3; i++){

    for(int j = 1; j <= 3; j++){

        if(j == 2){

            break outer;

        }

        System.out.println(i + " " + j);

    }

}
```

Output

```
1 1
```

---

# 📖 break Statement

The `break` statement immediately terminates the current loop.

---

## Example

```java
for(int i = 1; i <= 10; i++){

    if(i == 5){

        break;

    }

    System.out.println(i);

}
```

Output

```
1
2
3
4
```

Execution

```text
Loop

↓

i == 5

↓

break

↓

Exit Loop
```

---

# 🌍 Real-World Example

ATM

```java
while(true){

    if(correctPin){

        break;

    }

}
```

---

# 📖 continue Statement

The `continue` statement skips the current iteration and moves to the next iteration.

---

## Example

```java
for(int i = 1; i <= 5; i++){

    if(i == 3){

        continue;

    }

    System.out.println(i);

}
```

Output

```
1
2
4
5
```

Execution

```text
Loop

↓

i == 3

↓

Skip Current Iteration

↓

Continue Next Iteration
```

---

# 🌍 Real-World Example

Skip inactive users

```java
for(User user : users){

    if(!user.isActive()){

        continue;

    }

    process(user);

}
```

---

# 📊 break vs continue

| Feature | break | continue |
|----------|--------|-----------|
| Stops Loop | ✅ | ❌ |
| Skips Current Iteration | ❌ | ✅ |
| Next Iteration Executes | ❌ | ✅ |
| Exits Loop Completely | ✅ | ❌ |

---

# ⚠️ Common Mistakes

## ❌ Infinite Loop

```java
for(;;){

}
```

Runs forever unless a `break` is encountered.

---

## ❌ Modifying Loop Variable Incorrectly

```java
for(int i = 0; i < 5; ){

}
```

Without updating `i`, the loop becomes infinite.

---

## ❌ Using Enhanced for to Modify Elements

```java
for(int num : numbers){

    num++;

}
```

This does **not** modify the original array because `num` is only a copy of each element.

---

## ❌ Confusing break and continue

`break`

```
Exit Loop
```

`continue`

```
Skip Iteration
```

---

# 💡 Best Practices

- Use `for` when the number of iterations is known.
- Use `while` when the number of iterations is unknown.
- Use Enhanced `for` for read-only traversal.
- Avoid deeply nested loops whenever possible.
- Use labels sparingly; they can make code harder to read.
- Keep loop bodies simple and focused.

---

# 🎯 Interview Tip

A very common interview question is:

**Which loop should you choose?**

- ✅ `for` → Fixed number of iterations.
- ✅ `while` → Unknown number of iterations.
- ✅ `do-while` → Execute at least once.
- ✅ Enhanced `for` → Traverse arrays or collections without using an index.
