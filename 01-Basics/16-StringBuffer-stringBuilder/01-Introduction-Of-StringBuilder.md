# StringBuffer and StringBuilder

---

# 🎯 Learning Objectives

After completing this chapter you will know

- Mutable Strings
- StringBuffer
- StringBuilder
- Capacity
- Length
- append()
- deleteCharAt()
- insert()
- setLength()
- Performance Difference
- Thread Safety

---

# Why StringBuffer?

String objects are immutable.

```
String

Cannot Modify
```

Sometimes we need

```
Modify

Delete

Insert

Append
```

Instead of creating a new object every time,

Java provides

```
StringBuffer
```

---

# Mutable String

```
String

Immutable ❌

StringBuffer

Mutable ✅

StringBuilder

Mutable ✅
```

---

# Example

```java
StringBuffer sb = new StringBuffer();

System.out.println(sb.capacity());
```

Output

```
16
```

---

# Why Capacity = 16?

When StringBuffer is created,

Java allocates

```
16 characters

Default Buffer
```

---

# Example

```java
StringBuffer sb = new StringBuffer("Navin");
```

Capacity

```
5 + 16

=

21
```

---

# Capacity Formula

```
capacity

=

String Length

+

16
```

---

# append()

```java
sb.append(" Reddy");
```

Before

```
Navin
```

After

```
Navin Reddy
```

---

# deleteCharAt()

```java
sb.deleteCharAt(2);
```

Before

```
Navin
```

After

```
Navin
```

---

# insert()

```java
sb.insert(0,"Java ");
```

Output

```
Java Navin
```

---

# setLength()

```java
sb.setLength(30);
```

Increases buffer size.

---

# StringBuilder

Exactly same methods

But

```
Not Thread Safe
```

Therefore

Very Fast.

---

# Thread Safety

StringBuffer

```
Thread Safe

Slow
```

StringBuilder

```
Not Thread Safe

Fast
```

---

# Performance

```
Fastest

StringBuilder

↓

StringBuffer

↓

String
```

---

# Interview Question

Why String is immutable?

Why StringBuilder is faster?

Difference between String and StringBuffer?

Difference between StringBuffer and StringBuilder?

What is Capacity?

What is String Constant Pool?
