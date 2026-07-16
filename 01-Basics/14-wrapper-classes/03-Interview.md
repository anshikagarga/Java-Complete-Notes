# 📘 Chapter 14: Wrapper Classes (Part 3)

## Wrapper Classes vs Primitive Types, Interview Questions, MCQs & Practice Problems

> *"Wrapper Classes bridge the gap between primitive data types and objects. They are essential for working with Java Collections, Generics, Streams, and many modern Java APIs."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Wrapper Classes and Primitive Types.
- Understand when to use each.
- Revise the complete Wrapper Classes chapter.
- Prepare for Java interviews.
- Solve practice problems.

---

# 📚 Table of Contents

1. Wrapper Classes vs Primitive Types
2. Advantages
3. Limitations
4. Real-World Applications
5. Common Mistakes
6. Best Practices
7. Interview Questions
8. MCQs
9. Quick Revision
10. Practice Problems
11. Related Topics
12. References
13. Chapter Summary

---

# 📊 Wrapper Classes vs Primitive Types

| Feature | Primitive Type | Wrapper Class |
|----------|----------------|---------------|
| Type | Basic Data Type | Object |
| Package | Built into Java | java.lang |
| Memory Usage | Less | More |
| Performance | Faster | Slightly Slower |
| Null Value | ❌ No | ✅ Yes |
| Generics Support | ❌ No | ✅ Yes |
| Collections Support | ❌ No | ✅ Yes |
| Utility Methods | ❌ No | ✅ Yes |
| Object Methods | ❌ No | ✅ Yes |

---

# 📖 When Should You Use Primitive Types?

Use primitive types when:

- Performing mathematical calculations.
- Writing loops.
- Working with arrays.
- Optimizing performance.
- Memory efficiency is important.

Example

```java
int age = 21;

double salary = 50000.50;
```

---

# 📖 When Should You Use Wrapper Classes?

Use wrapper classes when:

- Working with Collections.
- Using Generics.
- Using Streams.
- Values can be null.
- Calling utility methods.

Example

```java
ArrayList<Integer> list = new ArrayList<>();
```

---

# 📊 Decision Flow

```text
Need an Object?

↓

YES

↓

Wrapper Class

----------------------

Need Maximum Performance?

↓

YES

↓

Primitive Type
```

---

# 📖 Wrapper Class Utility Methods

## Integer

```java
Integer.parseInt("123")
```

↓

Converts String to int.

---

```java
Integer.valueOf("123")
```

↓

Converts String to Integer.

---

```java
Integer.max(20,30)
```

↓

Returns Maximum Value.

---

```java
Integer.min(20,30)
```

↓

Returns Minimum Value.

---

## Double

```java
Double.parseDouble("25.5");
```

---

## Boolean

```java
Boolean.parseBoolean("true");
```

---

## Character

```java
Character.isLetter('A');
```

```java
Character.isDigit('5');
```

```java
Character.toUpperCase('a');
```

---

# 🌍 Real-World Applications

Wrapper Classes are widely used in

- ArrayList
- LinkedList
- HashMap
- HashSet
- TreeMap
- Stream API
- Optional
- Hibernate
- Spring Boot
- JDBC
- REST APIs
- JSON Parsing
- Serialization
- Reflection

---

# ✅ Advantages

- Can be stored in Collections.
- Works with Generics.
- Provides many utility methods.
- Supports Autoboxing.
- Supports Unboxing.
- Supports null values.
- Easy conversion between data types.

---

# ⚠️ Limitations

- Uses more memory.
- Slightly slower than primitives.
- Can throw NullPointerException while unboxing.
- Frequent boxing/unboxing affects performance.

---

# ⚠️ Common Mistakes

## ❌ Using == Instead of equals()

Wrong

```java
Integer a = 500;
Integer b = 500;

System.out.println(a == b);
```

Correct

```java
System.out.println(a.equals(b));
```

---

## ❌ Using Wrapper Classes for Heavy Calculations

Wrong

```java
Integer sum = 0;

for(int i=0;i<1000000;i++){

    sum += i;

}
```

Better

```java
int sum = 0;

for(int i=0;i<1000000;i++){

    sum += i;

}
```

Primitives are much faster.

---

## ❌ Ignoring Null During Unboxing

Wrong

```java
Integer x = null;

int y = x;
```

Correct

```java
if(x != null){

    int y = x;

}
```

---

## ❌ Using Deprecated Constructors

Wrong

```java
Integer obj = new Integer(10);
```

Correct

```java
Integer obj = Integer.valueOf(10);
```

or

```java
Integer obj = 10;
```

---

# 💡 Best Practices

- Use primitives whenever possible.
- Use Wrapper Classes when objects are required.
- Use `.equals()` for object comparison.
- Prefer `valueOf()` instead of constructors.
- Avoid unnecessary Autoboxing and Unboxing.
- Handle `null` safely before unboxing.
- Understand Integer Cache for interviews.

---

# 🧩 Interview Questions

## Beginner

1. What are Wrapper Classes?
2. Why do we need Wrapper Classes?
3. Which package contains Wrapper Classes?
4. What is Autoboxing?
5. What is Unboxing?

---

## Intermediate

6. Difference between Primitive Types and Wrapper Classes.
7. Explain Integer Cache.
8. Difference between `==` and `.equals()`.
9. Why can't Generics use primitive types?
10. What happens during Autoboxing?

---

## Advanced

11. Explain Integer Cache with examples.
12. Why does `Integer a = 100; Integer b = 100; a == b` return true?
13. Why can Unboxing throw NullPointerException?
14. Why is `Integer.valueOf()` preferred over constructors?
15. Explain the performance impact of Autoboxing.

---

# 🎓 MCQs

### Q1. Wrapper Classes belong to:

- A. java.util
- B. java.lang ✅
- C. java.io
- D. java.sql

---

### Q2. Which Wrapper Class is used for `int`?

- A. Int
- B. Integer ✅
- C. Number
- D. Long

---

### Q3. Autoboxing converts

- A. Object → Primitive
- B. Primitive → Object ✅
- C. String → Integer
- D. Object → String

---

### Q4. Which method compares Wrapper object values?

- A. ==
- B. compare()
- C. equals() ✅
- D. hashCode()

---

### Q5. Which values are cached by Integer?

- A. 0 to 100
- B. -100 to 100
- C. -128 to 127 ✅
- D. -256 to 255

---

# 📝 Quick Revision

## Wrapper Classes

```text
byte      → Byte
short     → Short
int       → Integer
long      → Long
float     → Float
double    → Double
char      → Character
boolean   → Boolean
```

---

## Autoboxing

```text
Primitive

↓

Wrapper Object
```

Example

```java
int x = 10;

Integer obj = x;
```

---

## Unboxing

```text
Wrapper Object

↓

Primitive
```

Example

```java
Integer obj = 10;

int x = obj;
```

---

## Integer Cache

```text
-128

↓

127
```

Objects within this range are reused.

---

## Object Comparison

```text
==

↓

Reference Comparison

--------------------

equals()

↓

Value Comparison
```

---

# 🧪 Practice Problems

## Beginner

- Convert `int` to `Integer`.
- Convert `Integer` to `int`.
- Parse an integer from a String.
- Convert an integer to a String.

---

## Intermediate

- Demonstrate Integer Cache.
- Compare Wrapper Objects using `==` and `.equals()`.
- Handle null values during unboxing.
- Store Wrapper Objects inside an ArrayList.

---

## Advanced

- Measure the performance difference between primitives and wrappers.
- Build a wrapper conversion utility.
- Demonstrate Autoboxing inside Collections.
- Explain Wrapper Class behavior in Stream API.

---

# 🔗 Related Topics

- Data Types
- Type Casting
- Arrays
- ArrayList
- Collections Framework
- Generics
- Comparable
- Comparator
- Stream API
- Optional Class

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

You have completed **Chapter 14: Wrapper Classes**.

### ✔️ Concepts Covered

- Wrapper Classes
- Primitive vs Wrapper
- Autoboxing
- Unboxing
- Integer Cache
- `==` vs `.equals()`
- Utility Methods
- Performance Considerations
- Best Practices
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ Wrapper Classes convert primitive values into objects.
- ✅ They are present in the **java.lang** package.
- ✅ Wrapper Classes are required for **Collections** and **Generics**.
- ✅ **Autoboxing** automatically converts primitives to wrapper objects.
- ✅ **Unboxing** automatically converts wrapper objects to primitives.
- ✅ Integer values between **-128 and 127** are cached.
- ✅ Use `.equals()` to compare wrapper object values instead of `==`.
- ✅ Prefer primitive types for performance-critical code and Wrapper Classes when object behavior is required.

---

# 🚀 Next Chapter

➡️ **15-strings.md**

### Topics Covered

- What are Enums?
- Why Enums?
- Creating Enums
- Enum Methods
- Enum Constructors
- Enum with switch
- Enum vs Constants
- Interview Questions
- Practice Problems