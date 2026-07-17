# 📘 Chapter 20: Enums (Part 1)

> *"Enums (Enumerations) are special Java types used to represent a fixed set of constants. They make code more readable, type-safe, and maintainable by replacing magic numbers and string constants."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what Enums are.
- Learn why Enums are needed.
- Create and use Enums.
- Access Enum constants.
- Understand the internal working of Enums.
- Compare Enums with normal constants.
- Learn real-world applications.

---

# 📚 Table of Contents

1. What are Enums?
2. Why Do We Need Enums?
3. Creating an Enum
4. Using Enum Constants
5. Enum with switch Statement
6. Internal Working
7. Advantages
8. Limitations
9. Real-World Applications

---

# 🤔 What is an Enum?

An **Enum (Enumeration)** is a special data type in Java that represents a **fixed set of predefined constants**.

Instead of writing

```java
String day = "Monday";
```

or

```java
int status = 1;
```

we can define

```java
enum Day{

    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY

}
```

Now only these values are allowed.

---

# 💡 Why Do We Need Enums?

Imagine storing order status using Strings.

```java
String status = "Delivered";
```

Someone may accidentally write

```java
String status = "Delivred";
```

(Java accepts it because it's just a String.)

Using Enums

```java
enum OrderStatus{

    PENDING,
    SHIPPED,
    DELIVERED,
    CANCELLED

}
```

Now

```java
OrderStatus status = OrderStatus.DELIVERED;
```

Only valid constants can be assigned.

---

# ❌ Problem Without Enums

```java
String trafficSignal = "Grean";
```

Output

```text
No compile-time error
```

Logical mistake.

---

# ✅ Solution Using Enums

```java
enum TrafficSignal{

    RED,
    YELLOW,
    GREEN

}
```

Usage

```java
TrafficSignal signal = TrafficSignal.GREEN;
```

Now invalid values are not allowed.

---

# 📖 Creating an Enum

Syntax

```java
enum EnumName{

    CONSTANT1,
    CONSTANT2,
    CONSTANT3

}
```

Example

```java
enum Direction{

    NORTH,
    SOUTH,
    EAST,
    WEST

}
```

---

# 📖 Using Enum Constants

```java
enum Day{

    MONDAY,
    TUESDAY,
    WEDNESDAY

}

public class Demo{

    public static void main(String[] args){

        Day today = Day.MONDAY;

        System.out.println(today);

    }

}
```

Output

```text
MONDAY
```

---

# 📖 Comparing Enum Constants

Enums can be compared using

```java
==
```

because each constant is a singleton instance.

Example

```java
Day d1 = Day.MONDAY;
Day d2 = Day.MONDAY;

System.out.println(d1 == d2);
```

Output

```text
true
```

---

# 📖 Enum in switch Statement

```java
enum Day{

    MONDAY,
    TUESDAY,
    WEDNESDAY

}

public class Demo{

    public static void main(String[] args){

        Day today = Day.TUESDAY;

        switch(today){

            case MONDAY:

                System.out.println("Start of Week");
                break;

            case TUESDAY:

                System.out.println("Working Day");
                break;

            case WEDNESDAY:

                System.out.println("Mid Week");
                break;

        }

    }

}
```

Output

```text
Working Day
```

---

# 📖 Enum Variables

```java
Day today = Day.FRIDAY;
```

Enum variables can only store constants belonging to the same enum type.

Wrong

```java
today = "Friday";
```

Compile-time Error.

---

# 📦 Internal Memory Representation

```text
Day

↓

MONDAY

↓

Singleton Object

------------------

TUESDAY

↓

Singleton Object

------------------

WEDNESDAY

↓

Singleton Object
```

Every enum constant is created only once by the JVM.

---

# 📖 Internal Working

The compiler internally converts

```java
enum Day{

    MONDAY,
    TUESDAY

}
```

into a special class similar to:

```java
final class Day extends Enum<Day>{

    public static final Day MONDAY = new Day();

    public static final Day TUESDAY = new Day();

}
```

You cannot create additional enum objects using `new`.

---

# 📊 Enum vs Constants

| Normal Constants | Enum |
|------------------|------|
| Usually `public static final` | Special Java Type |
| Not Type-Safe | Type-Safe |
| Can use invalid values | Only predefined values |
| Less readable | More readable |
| More error-prone | Less error-prone |

---

# ⚡ Time Complexity

| Operation | Complexity |
|-----------|------------|
| Access Enum Constant | O(1) |
| Comparison (`==`) | O(1) |
| Switch Case | O(1) |

---

# ✅ Advantages

- Type-safe.
- Readable code.
- Fixed constants.
- Prevents invalid values.
- Works well with switch statements.
- Singleton instances.
- Improves maintainability.

---

# ⚠️ Limitations

- Cannot create new constants at runtime.
- Cannot extend another class (because enums already extend `java.lang.Enum`).
- Best suited only for fixed sets of values.

---

# 🌍 Real-World Applications

Enums are widely used in:

- Days of the Week
- Months
- Order Status
- Payment Status
- User Roles
- HTTP Methods
- Traffic Signals
- Game States
- Logging Levels
- Database Status Codes

---

# 🎯 Interview Tip

### Question

Can we create an object of an Enum using `new`?

### Answer

❌ No.

Enum constructors are **implicitly private**, and the JVM creates all enum constants when the enum class is loaded. Therefore, statements like:

```java
Day d = new Day();
```

result in a **compile-time error**.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Enum Methods (`values()`, `ordinal()`, `name()`, `valueOf()`)
- Enum Constructors
- Enum Variables & Fields
- Enum Methods
- Internal Working
- Best Practices