# 📘 Chapter 16: Strings (Part 3)

## String Comparison, Methods, Best Practices & Interview Preparation

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Compare Strings correctly.
- Understand the difference between `==` and `equals()`.
- Learn commonly used String methods.
- Understand String immutability in real-world applications.
- Avoid common mistakes.
- Answer String interview questions confidently.

---

# 📚 Table of Contents

1. Comparing Strings
2. `==` vs `equals()`
3. Common String Methods
4. Real-World Applications
5. Time & Space Complexity
6. Common Mistakes
7. Best Practices
8. Interview Questions
9. Quick Revision
10. Practice Problems
11. Related Topics
12. References

---

# 🤔 Why do we need String Comparison?

Suppose you're building a Login System.

The user enters:

```text
Username: Anshika
Password: Java@123
```

Your program needs to compare the entered values with the stored values.

Using the wrong comparison operator may lead to incorrect results.

---

# 📖 Comparing Strings

Java provides two ways to compare Strings.

## 1️⃣ Using `==`

Compares **references (memory addresses)**.

```java
String s1 = "Java";
String s2 = "Java";

System.out.println(s1 == s2);
```

### Output

```
true
```

Both variables point to the same object in the String Pool.

---

## Example using `new`

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1 == s2);
```

### Output

```
false
```

Each object has a different memory location.

---

# 📦 Memory Diagram

```
Stack

s1 --------┐

            │

            ▼

Heap

Object 1

"Java"

-------------------

s2 --------┐

            │

            ▼

Heap

Object 2

"Java"
```

Even though the content is the same, the references are different.

---

# 📖 equals()

The `equals()` method compares the **actual content** of two Strings.

```java
String s1 = new String("Java");
String s2 = new String("Java");

System.out.println(s1.equals(s2));
```

### Output

```
true
```

Because both Strings contain the same characters.

---

# 🧠 Internal Working

```
equals()

↓

Compare Character by Character

↓

J
↓

a
↓

v
↓

a

↓

Return true
```

---

# 📖 equalsIgnoreCase()

Ignores uppercase and lowercase differences.

```java
String language = "JAVA";

System.out.println(language.equalsIgnoreCase("java"));
```

### Output

```
true
```

---

# 📖 Common String Methods

## length()

Returns the number of characters.

```java
String name = "Anshika";

System.out.println(name.length());
```

Output

```
7
```

---

## charAt()

Returns the character at a given index.

```java
String name = "Java";

System.out.println(name.charAt(2));
```

Output

```
v
```

---

## substring()

Extracts part of a String.

```java
String language = "Programming";

System.out.println(language.substring(3,7));
```

Output

```
gram
```

---

## contains()

Checks whether a String contains another String.

```java
String language = "Java Programming";

System.out.println(language.contains("Java"));
```

Output

```
true
```

---

## startsWith()

```java
String str = "Java Programming";

System.out.println(str.startsWith("Java"));
```

Output

```
true
```

---

## endsWith()

```java
String str = "Java Programming";

System.out.println(str.endsWith("ing"));
```

Output

```
true
```

---

## toUpperCase()

```java
String str = "java";

System.out.println(str.toUpperCase());
```

Output

```
JAVA
```

---

## toLowerCase()

```java
String str = "JAVA";

System.out.println(str.toLowerCase());
```

Output

```
java
```

---

## trim()

Removes leading and trailing spaces.

```java
String name = "   Java   ";

System.out.println(name.trim());
```

Output

```
Java
```

---

## replace()

Replaces characters or words.

```java
String str = "Java";

System.out.println(str.replace('J','K'));
```

Output

```
Kava
```

---

# 🌍 Real-World Applications

Strings are used in almost every software application.

Examples include:

- Login Systems
- Search Engines
- Email Validation
- Password Verification
- Chat Applications
- Banking Software
- E-commerce Websites
- URL Handling
- File Names
- API Responses

---

# ⚡ Time & Space Complexity

| Method | Time Complexity |
|----------|----------------|
| length() | O(1) |
| charAt() | O(1) |
| equals() | O(n) |
| substring() | O(n) |
| contains() | O(n) |
| replace() | O(n) |
| toUpperCase() | O(n) |
| toLowerCase() | O(n) |
| trim() | O(n) |

---

# ⚠️ Common Mistakes

## ❌ Comparing Strings using `==`

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);
```

Wrong for content comparison.

---

## ❌ Forgetting that Strings are Immutable

```java
String name = "Java";

name.concat(" Programming");

System.out.println(name);
```

Output

```
Java
```

Because `concat()` returns a new String.

Correct

```java
name = name.concat(" Programming");
```

---

## ❌ Ignoring Case Sensitivity

```java
"JAVA".equals("java")
```

Output

```
false
```

Use

```java
equalsIgnoreCase()
```

---

# 💡 Best Practices

- Use String literals whenever possible.
- Use `equals()` for comparing content.
- Use `equalsIgnoreCase()` when case should be ignored.
- Prefer `StringBuilder` for frequent modifications.
- Avoid creating unnecessary String objects with `new`.

---

# 🧩 Interview Questions

## Basic

1. What is a String?
2. Why is String immutable?
3. What is the String Constant Pool?
4. Difference between String literal and `new String()`?

---

## Intermediate

5. Difference between `==` and `equals()`?
6. Why are Strings stored in the String Pool?
7. Explain String immutability with memory diagrams.
8. Why is String final?

---

## Advanced

9. Why are Strings immutable in HashMap?
10. How does JVM optimize String objects?
11. Explain memory allocation for Strings.
12. Why is String thread-safe?

---

# 📝 Quick Revision

✅ String is an object.

✅ String literals are stored in the String Pool.

✅ String objects are immutable.

✅ `==` compares references.

✅ `equals()` compares content.

✅ `equalsIgnoreCase()` ignores case.

✅ Common methods:

- length()
- charAt()
- substring()
- contains()
- startsWith()
- endsWith()
- replace()
- trim()
- toUpperCase()
- toLowerCase()

---

# 🧪 Practice Problems

### Beginner

1. Reverse a String.
2. Count vowels in a String.
3. Count consonants.
4. Find String length without using `length()`.
5. Check whether a String is empty.

---

### Intermediate

6. Check Palindrome.
7. Count words in a sentence.
8. Remove duplicate characters.
9. Find the frequency of each character.
10. Compare two Strings without using `equals()`.

---

### Advanced

11. Implement your own `equals()` method.
12. Explain String Pool using a memory diagram.
13. Explain why String is immutable.
14. Demonstrate `==` vs `equals()` using code.

---

# 🔗 Related Topics

- StringBuffer
- StringBuilder
- Wrapper Classes
- Arrays
- Collections Framework

---

# 📚 References

- Oracle Java Documentation
- Java Language Specification (JLS)
- Effective Java by Joshua Bloch
- Head First Java
- OpenJDK Documentation

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have completed the **Strings** chapter.

You now understand:

- ✅ String Objects
- ✅ String Pool
- ✅ Heap & Stack Memory
- ✅ Immutability
- ✅ String Comparison
- ✅ Common String Methods
- ✅ Best Practices
- ✅ Interview Questions

➡️ Next Chapter:
**17-StringBuffer-StringBuilder.md**