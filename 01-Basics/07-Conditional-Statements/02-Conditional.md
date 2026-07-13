# 📘 Chapter 7: Conditional Statements in Java (Part 2)

## switch Statement, Enhanced switch & yield

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Understand the `switch` statement.
- Learn how the JVM executes a switch.
- Understand the `break` statement.
- Learn about fall-through behavior.
- Understand Enhanced Switch Expressions (Java 14+).
- Learn the `yield` keyword.
- Compare `if-else` and `switch`.

---

# 📚 Table of Contents

1. Why switch?
2. switch Statement
3. Internal Working
4. break Statement
5. Default Case
6. Fall-through
7. Enhanced Switch (Java 14+)
8. yield Keyword
9. switch vs if-else
10. Memory Diagram
11. Real-World Examples
12. Common Mistakes
13. Best Practices

---

# 🤔 Why do we need switch?

Suppose you're building an **Online Food Delivery App**.

The user selects:

```
1 → Pizza

2 → Burger

3 → Pasta

4 → Sandwich
```

Using multiple `if-else` statements works, but the code becomes lengthy and difficult to maintain.

For fixed choices, the `switch` statement provides a cleaner and more readable solution.

---

# 📖 What is switch?

The `switch` statement selects one block of code from multiple possible options based on the value of an expression.

Unlike `if-else`, it performs **value matching** instead of evaluating multiple boolean expressions.

---

# 📝 Syntax

```java
switch(expression){

    case value1:
        // code
        break;

    case value2:
        // code
        break;

    default:
        // code
}
```

---

# 🧠 Internal Working (JVM Perspective)

When a `switch` statement is executed:

1. The expression is evaluated **once**.
2. Java compares the expression with each `case`.
3. If a match is found, execution jumps directly to that case.
4. If no match exists, the `default` block executes (if present).

Flow

```text
Expression

      │
      ▼

Compare with Cases

      │

Match?

 ┌────┴─────┐
 │          │
Yes         No
 │          │
 ▼          ▼

Execute   Default
```

---

# 💻 Beginner Example

```java
public class Demo {

    public static void main(String[] args) {

        int day = 3;

        switch(day){

            case 1:
                System.out.println("Monday");
                break;

            case 2:
                System.out.println("Tuesday");
                break;

            case 3:
                System.out.println("Wednesday");
                break;

            default:
                System.out.println("Invalid Day");
        }

    }

}
```

Output

```
Wednesday
```

---

# 📖 break Statement

The `break` statement immediately terminates the current `switch` block.

Without `break`, Java continues executing the following cases.

---

Example

```java
int number = 2;

switch(number){

    case 1:
        System.out.println("One");
        break;

    case 2:
        System.out.println("Two");
        break;

    case 3:
        System.out.println("Three");
        break;

}
```

Output

```
Two
```

---

# 📖 Default Case

The `default` block executes when none of the cases match.

Example

```java
int month = 15;

switch(month){

    case 1:
        System.out.println("January");
        break;

    default:
        System.out.println("Invalid Month");

}
```

Output

```
Invalid Month
```

---

# 📖 Fall-through

If `break` is omitted, Java executes the matched case and all subsequent cases until it encounters a `break` or reaches the end of the switch.

Example

```java
int number = 2;

switch(number){

    case 1:
        System.out.println("One");

    case 2:
        System.out.println("Two");

    case 3:
        System.out.println("Three");

}
```

Output

```
Two
Three
```

Execution

```text
Match Case 2

↓

Print Two

↓

No break

↓

Print Three

↓

End
```

---

# ⚠️ Why does Fall-through happen?

A traditional `switch` continues executing subsequent cases after finding a match until a `break` is encountered.

This behavior is intentional and can sometimes be useful, but forgetting `break` is a common source of bugs.

---

# 🚀 Enhanced Switch (Java 14+)

Java introduced a cleaner syntax called the **Switch Expression**.

Instead of `:` and `break`, it uses `->`.

Example

```java
int day = 2;

switch(day){

    case 1 -> System.out.println("Monday");

    case 2 -> System.out.println("Tuesday");

    case 3 -> System.out.println("Wednesday");

    default -> System.out.println("Invalid");
}
```

Advantages

- Cleaner syntax
- No accidental fall-through
- No need for `break`
- Easier to read

---

# 📖 Returning a Value using switch

A switch expression can directly return a value.

```java
int day = 3;

String result = switch(day){

    case 1 -> "Monday";

    case 2 -> "Tuesday";

    case 3 -> "Wednesday";

    default -> "Invalid";

};

System.out.println(result);
```

Output

```
Wednesday
```

---

# 📖 yield Keyword

When a switch expression contains multiple statements inside a case, use `yield` to return the result.

Example

```java
int number = 2;

String result = switch(number){

    case 1 -> "One";

    case 2 -> {

        System.out.println("Processing...");

        yield "Two";
    }

    default -> "Invalid";

};

System.out.println(result);
```

Output

```
Processing...

Two
```

---

# 📦 Memory Diagram

```text
Stack Memory

day = 2

↓

Switch Expression

↓

Compare Cases

↓

Case 2 Matched

↓

Return "Tuesday"
```

---

# 🌍 Real-World Applications

The `switch` statement is commonly used in:

- ATM Menus
- Restaurant Ordering Systems
- Calculator Applications
- Banking Menus
- Ticket Booking Systems
- CLI (Command Line Interface) Programs
- Game Menus
- State Machines

---

# 📊 switch vs if-else

| Feature | if-else | switch |
|----------|----------|---------|
| Condition Type | Boolean Expressions | Fixed Values |
| Readability | Better for complex conditions | Better for multiple fixed options |
| Fall-through | ❌ No | ✅ Yes (Traditional switch) |
| Supports Ranges | ✅ Yes | ❌ No |
| Performance | Good | Often optimized for constant values |
| Java 14+ Expression | ❌ | ✅ Yes |

---

# ⚠️ Common Mistakes

### ❌ Forgetting break

```java
case 1:
    System.out.println("One");
```

Without `break`, execution continues into the next case.

---

### ❌ Using switch for ranges

Wrong

```java
switch(marks > 80)
```

Use `if-else` for conditions involving ranges.

---

### ❌ Duplicate case values

```java
case 1:
case 1:
```

This causes a compilation error.

---

# 💡 Best Practices

- Use `switch` for fixed values.
- Use `if-else` for ranges and complex conditions.
- Prefer Enhanced Switch (`->`) in modern Java.
- Always include a `default` case.
- Use descriptive enum values with `switch` whenever possible.