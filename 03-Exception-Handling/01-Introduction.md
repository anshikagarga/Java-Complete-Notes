# 📘 Chapter 21: Exception Handling (Part 1)

> *"Exception Handling is a mechanism in Java used to handle runtime errors gracefully, ensuring that the normal flow of the program is not interrupted unexpectedly."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what an Exception is.
- Differentiate between Errors and Exceptions.
- Learn why Exception Handling is needed.
- Understand the Exception Hierarchy.
- Write programs using `try` and `catch`.
- Handle multiple exceptions.
- Learn real-world applications.

---

# 📚 Table of Contents

1. What is Exception Handling?
2. Why Do We Need Exception Handling?
3. Error vs Exception
4. Exception Hierarchy
5. Types of Exceptions
6. try-catch Block
7. Multiple catch Blocks
8. Internal Working
9. Advantages
10. Real-World Applications

---

# 🤔 What is an Exception?

An **Exception** is an **unexpected event** that occurs during the execution of a program and disrupts its normal flow.

Examples:

- Dividing by zero
- Accessing an invalid array index
- Reading a missing file
- Parsing invalid input
- Dereferencing a `null` reference

Without exception handling, the program terminates abnormally.

---

# 💡 Why Do We Need Exception Handling?

Suppose a banking application transfers money.

```java
int balance = 1000;

int amount = 0;

System.out.println(balance / amount);
```

Output

```text
Exception in thread "main"
java.lang.ArithmeticException: / by zero
```

The application crashes.

Using Exception Handling, the application can display a meaningful message instead of terminating unexpectedly.

---

# ❌ Program Without Exception Handling

```java
public class Demo{

    public static void main(String[] args){

        System.out.println("Program Started");

        int result = 10 / 0;

        System.out.println(result);

        System.out.println("Program Ended");

    }

}
```

Output

```text
Program Started

Exception in thread "main"

java.lang.ArithmeticException: / by zero
```

`Program Ended` is never printed.

---

# ✅ Program With Exception Handling

```java
public class Demo{

    public static void main(String[] args){

        try{

            int result = 10 / 0;

            System.out.println(result);

        }

        catch(ArithmeticException e){

            System.out.println("Cannot divide by zero.");

        }

        System.out.println("Program Continues...");

    }

}
```

Output

```text
Cannot divide by zero.

Program Continues...
```

---

# 📖 Error vs Exception

| Error | Exception |
|-------|-----------|
| Serious problem | Recoverable problem |
| Handled by JVM | Can be handled by programmer |
| Usually cannot recover | Program can continue |
| Example: `OutOfMemoryError` | Example: `ArithmeticException` |

---

# 📦 Exception Hierarchy

```text
Object
   │
Throwable
   │
 ┌──────────────┐
 │              │
Error       Exception
                 │
        ┌───────────────┐
        │               │
 Checked        RuntimeException
 Exception             │
                ┌───────────────┐
                │               │
      ArithmeticException
      NullPointerException
      ArrayIndexOutOfBoundsException
      NumberFormatException
```

---

# 📖 Types of Exceptions

### 1. Checked Exceptions

Checked at compile time.

Examples

- IOException
- SQLException
- ClassNotFoundException

Must be handled or declared using `throws`.

---

### 2. Unchecked Exceptions

Occur at runtime.

Examples

- ArithmeticException
- NullPointerException
- ArrayIndexOutOfBoundsException
- NumberFormatException

Handling is optional but recommended.

---

# 📖 try Block

The `try` block contains code that may throw an exception.

Syntax

```java
try{

    // Risky code

}
```

Example

```java
try{

    int result = 20 / 0;

}
```

---

# 📖 catch Block

The `catch` block handles the exception.

Syntax

```java
catch(ExceptionType e){

    // Handling code

}
```

Example

```java
try{

    int result = 20 / 0;

}

catch(ArithmeticException e){

    System.out.println("Division by zero is not allowed.");

}
```

Output

```text
Division by zero is not allowed.
```

---

# 📖 Multiple catch Blocks

Different exceptions can be handled separately.

Example

```java
public class Demo{

    public static void main(String[] args){

        try{

            String s = null;

            System.out.println(s.length());

        }

        catch(ArithmeticException e){

            System.out.println("Arithmetic Error");

        }

        catch(NullPointerException e){

            System.out.println("Null Reference");

        }

    }

}
```

Output

```text
Null Reference
```

---

# 📖 Generic Exception Handling

A generic `Exception` catch block can handle multiple exception types.

Example

```java
try{

    int result = 10 / 0;

}

catch(Exception e){

    System.out.println("Exception Handled");

}
```

Output

```text
Exception Handled
```

> 💡 Place more specific catch blocks before a generic `Exception` catch block.

---

# 📦 Internal Working

When Java executes

```java
int result = 10 / 0;
```

Flow

```text
Program Starts

↓

Exception Occurs

↓

JVM Creates Exception Object

↓

Looks for Matching catch Block

↓

Found?

↓

Yes → Execute catch

↓

Continue Program

↓

No

↓

Terminate Program
```

---

# 📊 Common Runtime Exceptions

| Exception | Cause |
|-----------|-------|
| ArithmeticException | Divide by zero |
| NullPointerException | Accessing null object |
| ArrayIndexOutOfBoundsException | Invalid array index |
| NumberFormatException | Invalid number conversion |
| ClassCastException | Invalid object casting |

---

# ⚡ Time Complexity

Exception handling itself does not change the algorithmic complexity.

| Operation | Complexity |
|-----------|------------|
| try Block | Depends on code |
| catch Block | O(1) (handler execution) |

---

# ✅ Advantages

- Prevents abnormal program termination.
- Improves reliability.
- Enables graceful error recovery.
- Separates error-handling code from normal logic.
- Makes applications more robust.

---

# ⚠️ Limitations

- Excessive exception handling can reduce readability.
- Throwing exceptions has some performance overhead.
- Exceptions should not replace normal program logic.

---

# 🌍 Real-World Applications

Exception Handling is widely used in:

- Banking Systems
- ATM Software
- E-Commerce Applications
- Hospital Management Systems
- Spring Boot REST APIs
- File Handling
- Database Operations
- Online Payment Gateways

---

# 🎯 Interview Tip

### Question

What happens if an exception is not handled?

### Answer

If an exception is not handled, it propagates up the call stack. If no suitable handler is found, the JVM prints the exception stack trace and terminates the program.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- `finally` Block
- `throw`
- `throws`
- `printStackTrace()`
- `getMessage()`
- Multi-catch
- Nested try-catch
- Best Practices