# Part 2 — StringBuffer

---

# What is StringBuffer?

`StringBuffer` is a mutable sequence of characters introduced in Java to overcome the immutability limitation of the `String` class.

Unlike `String`, a `StringBuffer` object can be modified after creation without creating a new object.

```
String        → Immutable
StringBuffer  → Mutable
```

---

# Why do we need StringBuffer?

Suppose you are modifying a string thousands of times.

### Using String

```java
String name = "Java";

name = name + " Programming";
name = name + " Language";
name = name + " Tutorial";
```

Every concatenation creates

- New Object
- New Memory
- Old object becomes Garbage

Result

```
More Objects
More Memory
More Garbage Collection
Lower Performance
```

---

### Using StringBuffer

```java
StringBuffer sb = new StringBuffer("Java");

sb.append(" Programming");
sb.append(" Language");
sb.append(" Tutorial");
```

Only one object is modified.

```
Better Performance
Less Memory
No Extra Objects
```

---

# Internal Working

When StringBuffer is created

```java
StringBuffer sb = new StringBuffer("Navin");
```

JVM creates

```
Stack
---------------------
sb
 |
 |
 ▼

Heap
---------------------------------
StringBuffer Object

Capacity = 21
Length = 5

N a v i n
---------------------------------
```

Notice

Length

```
5
```

Capacity

```
21
```

---

# Why Capacity is 21?

When StringBuffer is initialized with a string

```java
new StringBuffer("Navin")
```

Capacity formula

```
Capacity = String Length + 16
```

Here

```
Length = 5

Capacity

5 + 16 = 21
```

---

# Default Capacity

```java
StringBuffer sb = new StringBuffer();
```

Default capacity

```
16
```

Example

```java
System.out.println(sb.capacity());
```

Output

```
16
```

---

# capacity() Method

Returns total allocated memory.

```java
StringBuffer sb = new StringBuffer();

System.out.println(sb.capacity());
```

Output

```
16
```

---

Example

```java
StringBuffer sb = new StringBuffer("Navin");

System.out.println(sb.capacity());
System.out.println(sb.length());
```

Output

```
21
5
```

Explanation

```
Capacity → Total Storage

Length → Characters Present
```

---

# ASCII Diagram

```
Stack
---------------------
sb
 |
 ▼

Heap
-------------------------------------------------

Capacity = 21

Index

0 1 2 3 4

N a v i n

Remaining Space

_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

-------------------------------------------------
```

---

# append()

Adds data at the end.

```java
StringBuffer sb = new StringBuffer("Navin");

sb.append(" Reddy");

System.out.println(sb);
```

Output

```
Navin Reddy
```

---

Memory

Before

```
Navin
```

After append

```
Navin Reddy
```

Same Object

No new object created.

---

# insert()

Adds data at a specific index.

```java
StringBuffer sb = new StringBuffer("Java");

sb.insert(0,"Core ");

System.out.println(sb);
```

Output

```
Core Java
```

---

# deleteCharAt()

Deletes one character.

```java
StringBuffer sb = new StringBuffer("Navin");

sb.deleteCharAt(2);

System.out.println(sb);
```

Output

```
Navin

↓

Nain
```

Character at index 2

```
v
```

gets removed.

---

# setLength()

Changes buffer length.

```java
StringBuffer sb = new StringBuffer("Java");

sb.setLength(10);

System.out.println(sb.length());
```

Output

```
10
```

Extra positions are filled internally.

---

# ensureCapacity()

Suppose

```java
StringBuffer sb = new StringBuffer();

System.out.println(sb.capacity());
```

Output

```
16
```

Now

```java
sb.ensureCapacity(100);

System.out.println(sb.capacity());
```

Output

```
100
```

Now JVM reserves space for 100 characters.

---

# What happens when capacity becomes full?

Suppose

Capacity

```
16
```

Current Length

```
16
```

Now one more character is inserted.

JVM automatically increases capacity.

Formula

```
New Capacity

(oldCapacity × 2) + 2
```

Example

```
Old Capacity

16

↓

(16 × 2) + 2

↓

34
```

ASCII

Before

```
Capacity = 16
████████████████
```

After

```
Capacity = 34
████████████████__________________
```

---

# toString()

Converts StringBuffer into String.

```java
StringBuffer sb = new StringBuffer("Navin");

String str = sb.toString();

System.out.println(str);
```

Output

```
Navin
```

Useful because many APIs work with String instead of StringBuffer.

---

# Real-World Applications

✔ Building SQL Queries

✔ Creating HTML

✔ File Processing

✔ Log Generation

✔ Report Generation

✔ Dynamic Text Editors

✔ CSV Generation

✔ XML Builders

---

# Time Complexity

| Operation | Complexity |
|-----------|------------|
| append() | O(1) Average |
| insert() | O(n) |
| deleteCharAt() | O(n) |
| setLength() | O(1) |
| capacity() | O(1) |
| toString() | O(n) |

---

# Common Mistakes

❌ Using String instead of StringBuffer for repeated modifications

❌ Confusing Capacity with Length

❌ Forgetting that insert() shifts characters

❌ Assuming append() creates a new object

---

# Best Practices

✔ Use StringBuffer when data changes frequently

✔ Use append() instead of String concatenation inside loops

✔ Use ensureCapacity() when expected size is known

✔ Convert to String only when required

---

# Quick Revision

- StringBuffer is mutable
- Default Capacity = 16
- Capacity with String = Length + 16
- append() adds at end
- insert() inserts at index
- deleteCharAt() removes one character
- ensureCapacity() increases buffer
- Capacity formula

```
(oldCapacity × 2) + 2
```

- Thread Safe ✔
- Mutable ✔