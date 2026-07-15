# 📘 Chapter 19: Encapsulation (Part 3)

## Encapsulation vs Abstraction, Interview Preparation & Best Practices

> *"Encapsulation protects an object's data by controlling access, while abstraction hides unnecessary implementation details. Together, they form the foundation of secure and maintainable object-oriented software."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Differentiate between Encapsulation and Abstraction.
- Understand how Encapsulation works internally.
- Learn UML representation of Encapsulation.
- Prepare for Java interview questions.
- Revise the complete Encapsulation chapter.
- Solve practice problems based on Encapsulation.

---

# 📚 Table of Contents

1. Encapsulation vs Abstraction
2. Internal Working
3. UML Diagram
4. Real-World Example
5. Time & Space Complexity
6. Common Mistakes
7. Best Practices
8. Interview Questions
9. Quick Revision
10. Practice Problems
11. Related Topics
12. References
13. Chapter Summary

---

# 📖 Encapsulation vs Abstraction

Although both are Object-Oriented Programming concepts, they solve different problems.

| Feature | Encapsulation | Abstraction |
|----------|---------------|-------------|
| Purpose | Protect Data | Hide Implementation |
| Focus | Security | Simplicity |
| Achieved Using | Classes + Access Modifiers | Abstract Classes & Interfaces |
| Access Control | Yes | Not Necessary |
| Hides | Data | Implementation Details |

---

## Example

### Encapsulation

```java
class Employee{

    private double salary;

    public double getSalary(){

        return salary;

    }

    public void setSalary(double salary){

        if(salary > 0){

            this.salary = salary;

        }

    }

}
```

Users cannot modify `salary` directly.

---

### Abstraction

```java
abstract class Vehicle{

    abstract void start();

}
```

Users know **what** the object can do,

but not **how** it performs the task.

---

# 🧠 Internal Working

Suppose

```java
employee.setSalary(50000);
```

Execution Flow

```text
Object Created

        │

        ▼

Setter Method Called

        │

        ▼

Validation Performed

        │

        ▼

Private Variable Updated

        │

        ▼

Getter Returns Value
```

Every modification goes through controlled methods.

---

# 📦 UML Diagram

```text
+----------------------------------+

            Student

+----------------------------------+

- name : String

- age : int

+----------------------------------+

+ setName(name : String)

+ getName() : String

+ setAge(age : int)

+ getAge() : int

+----------------------------------+
```

Legend

```text
+  Public

-  Private
```

The UML diagram clearly shows that data is hidden while methods are exposed.

---

# 🚀 Real-World Example

## Banking System

```text
Customer

      │

      ▼

Deposit()

Withdraw()

CheckBalance()

      │

      ▼

Private Balance
```

Customers interact only with public methods.

The balance remains protected inside the object.

---

## Student Portal

Students can

- View Marks
- Update Profile
- Change Password

They cannot directly modify

```text
Database Records
```

Only validated methods can perform updates.

---

# 🌍 Real-World Applications

Encapsulation is widely used in:

- Banking Applications
- ATM Software
- E-Commerce Platforms
- Student Management Systems
- Hospital Management Systems
- Airline Reservation Systems
- Spring Boot Applications
- Hibernate Entities
- JavaBeans
- REST APIs

---

# ⚡ Time & Space Complexity

| Operation | Complexity |
|------------|------------|
| Getter Method | O(1) |
| Setter Method | O(1) |
| Validation | O(1) *(Simple Conditions)* |
| Object Creation | O(Number of Fields) |

Encapsulation itself does not add significant performance overhead.

---

# ⚠️ Common Mistakes

## ❌ Public Variables

Wrong

```java
public String password;
```

Correct

```java
private String password;
```

---

## ❌ Getter for Sensitive Information

Wrong

```java
public String getPassword(){

    return password;

}
```

Sensitive information should not always be exposed.

---

## ❌ Setter Without Validation

Wrong

```java
this.salary = salary;
```

Correct

```java
if(salary > 0){

    this.salary = salary;

}
```

---

## ❌ Confusing Encapsulation with Abstraction

Remember

```text
Encapsulation

↓

Protect Data

----------------------

Abstraction

↓

Hide Implementation
```

---

# 💡 Best Practices

- Keep fields `private`.
- Validate user input inside setters.
- Expose only necessary methods.
- Avoid unnecessary getters for confidential data.
- Prefer immutable objects when data should never change.
- Keep business rules inside the class.
- Follow JavaBeans naming conventions (`getX()`, `setX()`).

---

# 🧩 Interview Questions

## Beginner

1. What is Encapsulation?
2. Why do we use Encapsulation?
3. What is Data Hiding?
4. Why are variables declared `private`?
5. What are Getter and Setter methods?

---

## Intermediate

6. Difference between Encapsulation and Data Hiding.
7. Difference between Encapsulation and Abstraction.
8. Why should setters perform validation?
9. What are immutable classes?
10. Explain JavaBeans.

---

## Advanced

11. How does Encapsulation improve software design?
12. Explain Encapsulation from the JVM perspective.
13. Can Encapsulation improve security?
14. Explain Encapsulation with a Banking System example.
15. Why should internal collections not be exposed directly?
16. Explain Encapsulation in Spring Boot entities.

---

# 📝 Quick Revision

## Encapsulation

```text
Private Variables

        │

Getter / Setter

        │

Controlled Access

        │

Secure Object
```

---

## Data Hiding

```text
private Variables

↓

Cannot Access Directly

↓

Public Methods
```

---

## Object Flow

```text
Object

↓

Setter

↓

Validation

↓

Private Variable

↓

Getter

↓

User
```

---

## Encapsulation vs Abstraction

```text
Encapsulation

↓

Protect Data

--------------------

Abstraction

↓

Hide Implementation
```

---

# 🧪 Practice Problems

### Beginner

- Create a Student class using private variables.
- Implement Getter and Setter methods.
- Validate age before storing it.

---

### Intermediate

- Create a BankAccount class with deposit and withdrawal methods.
- Implement an Employee class with salary validation.
- Build an immutable Student class.

---

### Advanced

- Design a Library Management System using Encapsulation.
- Create a Hospital Management System where patient data is private.
- Implement Encapsulation in an E-commerce Product class.
- Build a User class that securely manages passwords.

---

# 🎓 MCQs

### Q1. Which access modifier is commonly used to achieve Encapsulation?

- A. public
- B. protected
- C. private ✅
- D. default

---

### Q2. Which methods provide controlled access to private variables?

- A. Constructors
- B. Getter and Setter ✅
- C. Static Methods
- D. Abstract Methods

---

### Q3. Encapsulation mainly improves:

- A. Graphics
- B. Security & Maintainability ✅
- C. Memory Allocation
- D. Compilation Speed

---

### Q4. Which OOP principle hides implementation details?

- A. Encapsulation
- B. Inheritance
- C. Abstraction ✅
- D. Polymorphism

---

# 🔗 Related Topics

- Classes & Objects
- Access Modifiers
- Constructors
- `this` Keyword
- Inheritance
- Abstraction
- Polymorphism
- Interfaces
- JavaBeans
- Design Patterns

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java – Joshua Bloch
- Head First Java
- Clean Code – Robert C. Martin

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed **Chapter 19: Encapsulation**.

### ✔️ Concepts Covered

- What is Encapsulation?
- Data Hiding
- Access Modifiers
- Private Variables
- Getter Methods
- Setter Methods
- Validation
- Immutable Classes
- Encapsulation vs Data Hiding
- Encapsulation vs Abstraction
- UML Diagram
- JVM Working
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Encapsulation binds **data and methods** into a single unit.
- ✅ It protects object data using **private fields**.
- ✅ Getter and Setter methods provide **controlled access**.
- ✅ Validation inside setters keeps objects in a valid state.
- ✅ Encapsulation improves **security, maintainability, and flexibility**.
- ✅ Data Hiding is a part of Encapsulation, but both are not the same.
- ✅ Abstraction hides implementation details, while Encapsulation protects data.
- ✅ Encapsulation is widely used in enterprise applications such as Spring Boot, Hibernate, banking systems, and REST APIs.

---

# 🚀 Next Chapter

➡️ **01-Inheritance.md**

### Topics Covered

- What is Inheritance?
- Types of Inheritance
- `extends` Keyword
- IS-A Relationship
- Constructor Chaining in Inheritance
- Method Overriding
- `super` Keyword
- Object Memory Model
- JVM Working
- Interview Questions
- Practice Problems