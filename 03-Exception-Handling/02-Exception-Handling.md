# 📘 Chapter 21: Exception Handling (Part 2)

## finally, throw, throws, Multi-Catch & Nested try-catch

> *"Exception Handling is not only about catching exceptions. Java also provides keywords like `finally`, `throw`, and `throws` to write robust, maintainable, and fault-tolerant applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand the `finally` block.
- Learn the difference between `throw` and `throws`.
- Throw custom exceptions.
- Handle multiple exceptions.
- Understand nested try-catch.
- Use exception methods such as `getMessage()` and `printStackTrace()`.
- Follow best practices.

---

# 📚 Table of Contents

1. finally Block
2. throw Keyword
3. throws Keyword
4. throw vs throws
5. Multi-Catch
6. Nested try-catch
7. Exception Methods
8. Internal Working
9. Common Mistakes
10. Best Practices

---

# 📖 finally Block

The `finally` block contains code that **always executes**, regardless of whether an exception occurs or not.

It is commonly used for resource cleanup, such as:

- Closing files
- Closing database connections
- Closing network sockets
- Releasing locks

---

## Syntax

```java
try{

    // Risky code

}

catch(Exception e){

    // Handle exception

}

finally{

    // Always executes

}
```

---

## Example

```java
public class Demo{

    public static void main(String[] args){

        try{

            int result = 10 / 0;

        }

        catch(ArithmeticException e){

            System.out.println("Cannot divide by zero.");

        }

        finally{

            System.out.println("Finally Block Executed");

        }

    }

}
```

Output

```text
Cannot divide by zero.

Finally Block Executed
```

---

## Example Without Exception

```java
try{

    System.out.println("Hello");

}

finally{

    System.out.println("Finally");

}
```

Output

```text
Hello

Finally
```

---

# 📖 throw Keyword

The `throw` keyword is used to **explicitly create and throw an exception**.

Syntax

```java
throw new ExceptionType("Message");
```

---

## Example

```java
public class Demo{

    public static void main(String[] args){

        int age = 15;

        if(age < 18){

            throw new ArithmeticException("Not Eligible");

        }

    }

}
```

Output

```text
Exception in thread "main"

java.lang.ArithmeticException: Not Eligible
```

---

## Handling a Thrown Exception

```java
public class Demo{

    public static void main(String[] args){

        try{

            throw new ArithmeticException("Invalid");

        }

        catch(ArithmeticException e){

            System.out.println(e.getMessage());

        }

    }

}
```

Output

```text
Invalid
```

---

# 📖 throws Keyword

The `throws` keyword declares that a method **may throw an exception**, leaving the responsibility of handling it to the caller.

Syntax

```java
returnType methodName() throws ExceptionType{

}
```

---

## Example

```java
import java.io.IOException;

public class Demo{

    static void readFile() throws IOException{

        throw new IOException("File Not Found");

    }

    public static void main(String[] args){

        try{

            readFile();

        }

        catch(IOException e){

            System.out.println(e.getMessage());

        }

    }

}
```

Output

```text
File Not Found
```

---

# 📊 throw vs throws

| throw | throws |
|--------|---------|
| Used to explicitly throw an exception | Used to declare exceptions |
| Used inside a method | Used in the method signature |
| Throws one exception object at a time | Can declare multiple exceptions |
| Followed by an exception object | Followed by exception class names |

---

# 📖 Multi-Catch

Java allows handling multiple exception types in a single catch block using `|`.

Example

```java
public class Demo{

    public static void main(String[] args){

        try{

            String s = null;

            System.out.println(s.length());

        }

        catch(ArithmeticException | NullPointerException e){

            System.out.println("Handled");

        }

    }

}
```

Output

```text
Handled
```

---

# 📖 Nested try-catch

A `try` block can be placed inside another `try` block.

Example

```java
public class Demo{

    public static void main(String[] args){

        try{

            try{

                int result = 10 / 0;

            }

            catch(ArithmeticException e){

                System.out.println("Inner Catch");

            }

        }

        catch(Exception e){

            System.out.println("Outer Catch");

        }

    }

}
```

Output

```text
Inner Catch
```

---

# 📖 Exception Methods

### 1. getMessage()

Returns the exception message.

```java
try{

    int result = 10 / 0;

}

catch(Exception e){

    System.out.println(e.getMessage());

}
```

Output

```text
/ by zero
```

---

### 2. printStackTrace()

Prints the complete stack trace.

```java
try{

    int result = 10 / 0;

}

catch(Exception e){

    e.printStackTrace();

}
```

Output (Example)

```text
java.lang.ArithmeticException: / by zero
    at Demo.main(Demo.java:5)
```

---

### 3. toString()

Returns the exception class name along with the message.

```java
catch(Exception e){

    System.out.println(e);

}
```

Output

```text
java.lang.ArithmeticException: / by zero
```

---

# 📦 Internal Working

Consider

```java
throw new ArithmeticException("Error");
```

Flow

```text
Create Exception Object

↓

throw

↓

JVM Searches Matching catch

↓

Found?

↓

Yes

↓

Execute catch

↓

finally

↓

Continue Program

↓

No

↓

Program Terminates
```

---

# ⚠️ Common Mistakes

## ❌ Catching Generic Exception First

Wrong

```java
try{

}

catch(Exception e){

}

catch(ArithmeticException e){

}
```

Compile-time Error.

Correct

```java
try{

}

catch(ArithmeticException e){

}

catch(Exception e){

}
```

---

## ❌ Using throw Without an Exception Object

Wrong

```java
throw ArithmeticException;
```

Correct

```java
throw new ArithmeticException();
```

---

## ❌ Ignoring finally for Resource Cleanup

Wrong

```java
FileInputStream file = new FileInputStream("data.txt");

// File never closed
```

Better

```java
finally{

    file.close();

}
```

Or use **try-with-resources** (recommended in modern Java).

---

## ❌ Confusing throw and throws

Remember:

- `throw` → Throws an exception object.
- `throws` → Declares possible exceptions in a method signature.

---

# 💡 Best Practices

- Catch the most specific exception first.
- Avoid empty catch blocks.
- Use meaningful exception messages.
- Use `finally` (or try-with-resources) for cleanup.
- Prefer custom exceptions for business rules.
- Do not use exceptions for normal control flow.

---

# 🌍 Real-World Applications

These features are commonly used in:

- File Handling
- JDBC Database Operations
- REST APIs
- Spring Boot Applications
- Banking Systems
- Payment Gateways
- Logging Frameworks
- Cloud Applications

---

# 🎯 Interview Tip

### Question

What is the difference between `throw` and `throws`?

### Answer

- **`throw`** is used **inside a method** to explicitly throw an exception object.
- **`throws`** is used **in the method signature** to declare that the method may throw one or more exceptions, allowing the caller to handle them.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- Custom Exceptions
- Checked vs Unchecked Exceptions
- Exception Propagation
- Interview Questions
- MCQs
- Practice Problems
- Quick Revision
- Chapter Summary