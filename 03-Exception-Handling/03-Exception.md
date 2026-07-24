# 📘 Chapter 21: Exception Handling (Part 3)

## Custom Exceptions, Exception Propagation, Interview Questions, MCQs & Chapter Summary

> *"Good developers don't just write code that works—they write code that fails gracefully. Exception Handling is one of the most important concepts for building reliable Java applications."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Create Custom Exceptions.
- Understand Checked vs Unchecked Exceptions.
- Learn Exception Propagation.
- Follow Exception Handling Best Practices.
- Answer Java Interview Questions confidently.
- Solve MCQs and coding problems.

---

# 📚 Table of Contents

1. Custom Exceptions
2. Checked vs Unchecked Exceptions
3. Exception Propagation
4. Exception Chaining
5. try-with-resources
6. Best Practices
7. Common Mistakes
8. Interview Questions
9. MCQs
10. Quick Revision
11. Practice Problems
12. Related Topics
13. References
14. Chapter Summary

---

# 📖 What is a Custom Exception?

A **Custom Exception** is a user-defined exception created by extending an existing exception class.

It is useful when the built-in exceptions do not clearly represent a business rule.

### Examples

- InvalidAgeException
- InsufficientBalanceException
- InvalidPasswordException
- ProductOutOfStockException

---

# 📖 Creating a Custom Exception

```java
class InvalidAgeException extends Exception{

    public InvalidAgeException(String message){

        super(message);

    }

}
```

Here,

- `InvalidAgeException` is our custom exception.
- It extends `Exception`, making it a **checked exception**.

---

# 📖 Using a Custom Exception

```java
class InvalidAgeException extends Exception{

    public InvalidAgeException(String message){

        super(message);

    }

}

public class Demo{

    static void vote(int age) throws InvalidAgeException{

        if(age < 18){

            throw new InvalidAgeException("Age must be at least 18.");

        }

        System.out.println("Eligible to Vote");

    }

    public static void main(String[] args){

        try{

            vote(16);

        }

        catch(InvalidAgeException e){

            System.out.println(e.getMessage());

        }

    }

}
```

Output

```text
Age must be at least 18.
```

---

# 📖 Checked vs Unchecked Exceptions

| Checked Exception | Unchecked Exception |
|-------------------|---------------------|
| Checked at compile time | Occur at runtime |
| Must be handled or declared | Handling is optional |
| Extend `Exception` | Extend `RuntimeException` |
| Example: `IOException` | Example: `NullPointerException` |

---

# 📖 Exception Propagation

When a method does not handle an exception, it is passed to the calling method.

Example

```java
public class Demo{

    static void method3(){

        int result = 10 / 0;

    }

    static void method2(){

        method3();

    }

    static void method1(){

        method2();

    }

    public static void main(String[] args){

        method1();

    }

}
```

Flow

```text
method3()

↓

method2()

↓

method1()

↓

main()

↓

JVM
```

If no method handles the exception, the JVM terminates the program.

---

# 📖 Exception Chaining

An exception can wrap another exception.

Example

```java
try{

    throw new ArithmeticException();

}

catch(ArithmeticException e){

    throw new RuntimeException("Calculation Failed", e);

}
```

The original exception (`ArithmeticException`) becomes the **cause** of the new exception.

---

# 📖 try-with-resources

Introduced in **Java 7**, `try-with-resources` automatically closes resources.

Example

```java
import java.io.BufferedReader;
import java.io.FileReader;

public class Demo{

    public static void main(String[] args){

        try(BufferedReader br = new BufferedReader(new FileReader("data.txt"))){

            System.out.println(br.readLine());

        }

        catch(Exception e){

            System.out.println(e.getMessage());

        }

    }

}
```

No need to explicitly call `close()`.

---

# 📊 Traditional try-finally vs try-with-resources

| try-finally | try-with-resources |
|-------------|--------------------|
| Manual resource closing | Automatic resource closing |
| More code | Less code |
| Higher chance of leaks | Safer and cleaner |
| Older approach | Recommended approach |

---

# 🌍 Real-World Applications

Exception Handling is heavily used in:

- Banking Applications
- Online Payment Systems
- Spring Boot REST APIs
- E-Commerce Platforms
- Database Connectivity (JDBC)
- File Upload Systems
- Cloud Services
- Android Applications

---

# ⚠️ Common Mistakes

## ❌ Empty catch Block

Wrong

```java
try{

}

catch(Exception e){

}
```

The exception is silently ignored.

---

## ❌ Catching `Throwable`

Wrong

```java
catch(Throwable t){

}
```

Avoid this unless you have a very specific reason. It also catches serious `Error`s that applications generally should not handle.

---

## ❌ Using Exceptions for Normal Logic

Wrong

```java
try{

    int result = a / b;

}

catch(Exception e){

    // Used instead of validating b
}
```

Better

```java
if(b != 0){

    int result = a / b;

}
```

---

## ❌ Ignoring Exception Messages

Always log or display meaningful information.

Good

```java
catch(Exception e){

    System.out.println(e.getMessage());

}
```

---

# 💡 Best Practices

- Catch specific exceptions before generic ones.
- Write meaningful exception messages.
- Use custom exceptions for business rules.
- Prefer `try-with-resources` for resource management.
- Avoid swallowing exceptions.
- Validate inputs before relying on exceptions.
- Log exceptions in production applications.

---

# 🧩 Interview Questions

## Beginner

1. What is an Exception?
2. Why is Exception Handling required?
3. What is the difference between Error and Exception?
4. What is a Checked Exception?
5. What is an Unchecked Exception?

---

## Intermediate

6. Difference between `throw` and `throws`.
7. Explain `finally`.
8. What is Exception Propagation?
9. Explain `printStackTrace()`.
10. What is `try-with-resources`?

---

## Advanced

11. What is a Custom Exception?
12. Can we have multiple catch blocks?
13. Why should specific exceptions be caught before generic exceptions?
14. Explain Exception Chaining.
15. What happens if an exception is not handled?

---

# 🎓 MCQs

### Q1. Which class is the parent of all Exceptions and Errors?

- A. Object
- B. Throwable ✅
- C. RuntimeException
- D. Error

---

### Q2. Which keyword automatically closes resources?

- A. close
- B. autoClose
- C. try-with-resources ✅
- D. finalize

---

### Q3. Which exception is unchecked?

- A. IOException
- B. SQLException
- C. ClassNotFoundException
- D. NullPointerException ✅

---

### Q4. A custom checked exception generally extends:

- A. RuntimeException
- B. Exception ✅
- C. Error
- D. Throwable

---

### Q5. Which block executes regardless of whether an exception occurs?

- A. catch
- B. throw
- C. finally ✅
- D. throws

---

# 📝 Quick Revision

## Basic Structure

```java
try{

    // Risky code

}

catch(Exception e){

    // Handle exception

}

finally{

    // Cleanup

}
```

---

## throw

```java
throw new ArithmeticException("Error");
```

---

## throws

```java
void read() throws IOException{

}
```

---

## Custom Exception

```java
class InvalidAgeException extends Exception{

    public InvalidAgeException(String message){

        super(message);

    }

}
```

---

## try-with-resources

```java
try(Resource r = ...){

}
```

Resources are closed automatically.

---

# 🧪 Practice Problems

## Beginner

- Handle division by zero.
- Handle invalid array index.
- Handle a `NullPointerException`.

---

## Intermediate

- Read a file using `try-with-resources`.
- Create a custom exception for age validation.
- Demonstrate multiple catch blocks.

---

## Advanced

- Build a Banking System with custom exceptions.
- Create an ATM simulation with balance validation.
- Implement an online payment validation module.
- Demonstrate exception propagation across multiple methods.

---

# 🔗 Related Topics

- Classes and Objects
- Inheritance
- Polymorphism
- File Handling
- Multithreading
- Collections Framework
- JDBC
- Spring Boot

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

You have completed **Chapter 21: Exception Handling**.

### ✔️ Concepts Covered

- Exceptions and Errors
- Checked vs Unchecked Exceptions
- `try`, `catch`, `finally`
- `throw` and `throws`
- Multiple Catch Blocks
- Nested try-catch
- Exception Methods (`getMessage()`, `printStackTrace()`)
- Custom Exceptions
- Exception Propagation
- Exception Chaining
- try-with-resources
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Exceptions represent recoverable runtime problems.
- ✅ Errors are serious JVM-level problems and are generally not recoverable.
- ✅ Use `try-catch` to handle exceptions gracefully.
- ✅ Use `finally` or **try-with-resources** to release resources.
- ✅ `throw` throws an exception object, while `throws` declares possible exceptions.
- ✅ Prefer catching **specific exceptions** before generic ones.
- ✅ Create **custom exceptions** for business-specific validation.
- ✅ Use exceptions for exceptional situations—not as a replacement for normal control flow.

---

# 🚀 Next Chapter

➡️ **04-Multithreading.md**

### Topics Covered

- Introduction to Multithreading
- Process vs Thread
- Thread Lifecycle
- Creating Threads
- `Thread` Class
- `Runnable` Interface
- Thread Methods (`start()`, `sleep()`, `join()`, etc.)
- Synchronization
- Deadlock
- Interview Questions
- MCQs
- Practice Problems