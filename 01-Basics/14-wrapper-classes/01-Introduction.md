# 📘 Chapter 14: Wrapper Classes (Part 1)

> *"Wrapper Classes allow primitive data types to be treated as objects. They are one of the most important concepts in Java because Collections, Generics, and many Java APIs work only with objects, not primitives."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Wrapper Classes.
- Learn why Wrapper Classes are needed.
- Identify wrapper classes for each primitive type.
- Understand Autoboxing and Unboxing.
- Convert between primitives and objects.
- Learn common methods of wrapper classes.
- Analyze performance considerations.

---

# 📚 Table of Contents

1. What are Wrapper Classes?
2. Why Wrapper Classes?
3. Primitive vs Object
4. Wrapper Classes Table
5. Creating Wrapper Objects
6. Autoboxing
7. Unboxing
8. Internal Working
9. Common Methods
10. Time Complexity
11. Advantages
12. Limitations

---

# 🤔 What are Wrapper Classes?

A Wrapper Class is a class that wraps a primitive value inside an object.

Example

```java
int x = 10;
```

Primitive value.

Wrapper object

```java
Integer obj = Integer.valueOf(10);
```

Now the value `10` behaves like an object.

---

# 💡 Why Do We Need Wrapper Classes?

Many Java features work only with objects.

Examples

- Collections Framework
- Generics
- Stream API
- Synchronization Utilities
- Reflection

Primitive values cannot be stored directly in generic collections.

❌ Invalid

```java
ArrayList<int> list = new ArrayList<>();
```

✅ Correct

```java
ArrayList<Integer> list = new ArrayList<>();
```

---

# 📖 Primitive vs Object

| Primitive | Wrapper Object |
|-----------|----------------|
| int | Integer |
| double | Double |
| char | Character |
| boolean | Boolean |

Primitive

```java
int a = 5;
```

Object

```java
Integer b = 5;
```

---

# 📊 Wrapper Classes Table

| Primitive | Wrapper Class |
|-----------|----------------|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

All wrapper classes are present in the

```text
java.lang
```

package.

---

# 📖 Creating Wrapper Objects

## Method 1: Using valueOf()

```java
Integer obj = Integer.valueOf(100);
```

Recommended.

---

## Method 2: Autoboxing

```java
Integer obj = 100;
```

Java automatically converts the primitive to an object.

---

## Method 3: Constructor (Deprecated)

```java
Integer obj = new Integer(100);
```

Avoid this in modern Java.

---

# 📖 Autoboxing

Autoboxing means

```text
Primitive

↓

Wrapper Object
```

automatically.

Example

```java
int x = 10;

Integer obj = x;
```

Java internally performs

```java
Integer obj = Integer.valueOf(x);
```

---

# 📖 Unboxing

Unboxing means

```text
Wrapper Object

↓

Primitive
```

automatically.

Example

```java
Integer obj = 20;

int x = obj;
```

Java internally performs

```java
int x = obj.intValue();
```

---

# 📊 Autoboxing & Unboxing Flow

```text
Primitive int

↓

Autoboxing

↓

Integer Object

↓

Unboxing

↓

Primitive int
```

---

# 💻 Example

```java
public class Demo {

    public static void main(String[] args) {

        int a = 5;

        Integer obj = a;   // Autoboxing

        int b = obj;       // Unboxing

        System.out.println(a);
        System.out.println(obj);
        System.out.println(b);

    }

}
```

Output

```text
5
5
5
```

---

# 🧠 Internal Working

```text
int a = 5

↓

Integer.valueOf(5)

↓

Integer Object

↓

intValue()

↓

int b = 5
```

---

# 📖 Common Wrapper Methods

## Integer

```java
Integer.parseInt("123")
```

Converts String to int.

---

```java
Integer.valueOf("123")
```

Converts String to Integer object.

---

```java
Integer.toString(123)
```

Converts int to String.

---

```java
Integer.max(10, 20)
```

Returns larger value.

---

```java
Integer.min(10, 20)
```

Returns smaller value.

---

# 💻 Example

```java
String s = "100";

int x = Integer.parseInt(s);

System.out.println(x + 50);
```

Output

```text
150
```

---

# 📖 Character Wrapper Methods

```java
Character.isDigit('5');
```

↓

```text
true
```

---

```java
Character.isLetter('A');
```

↓

```text
true
```

---

```java
Character.toUpperCase('a');
```

↓

```text
'A'
```

---

# 📖 Boolean Wrapper Methods

```java
Boolean.parseBoolean("true");
```

↓

```text
true
```

---

# ⚡ Time Complexity

Most wrapper operations are constant time.

| Operation | Complexity |
|-----------|------------|
| valueOf() | O(1) |
| intValue() | O(1) |
| parseInt() | O(n) |
| toString() | O(n) |

Here `n` is the number of digits in the string.

---

# ✅ Advantages

- Allows primitives to be used in Collections.
- Supports Generics.
- Provides utility methods.
- Enables conversion between types.
- Supports null values (unlike primitives).

---

# ⚠️ Limitations

- Uses more memory than primitives.
- Slightly slower than primitives.
- Can cause `NullPointerException` during unboxing.
- Excessive boxing/unboxing may affect performance.

---

# 🌍 Real-World Applications

Wrapper classes are used in:

- ArrayList<Integer>
- HashMap<Integer, String>
- Stream API
- Database frameworks
- JSON serialization
- Spring applications
- Hibernate/JPA
- Java libraries

---

# 🎯 Interview Tip

### Question

Why can't we use `ArrayList<int>`?

### Answer

Generics in Java work only with reference types (objects), not primitive types. Therefore, `ArrayList<int>` is invalid. We must use the wrapper class `Integer`, which allows primitive `int` values to be stored as objects through autoboxing.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Wrapper Class Caching
- Integer Cache
- Equality (`==` vs `.equals()`)
- NullPointerException in Unboxing
- Performance Considerations
- Common Mistakes
- Best Practices