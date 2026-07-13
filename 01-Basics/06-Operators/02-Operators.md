# 📘 Chapter 6: Operators in Java (Part 2)

## Relational, Logical, Assignment & Ternary Operators

---

# 🎯 Learning Objectives

After completing this section, you will be able to:

- Understand Relational Operators.
- Learn Logical Operators.
- Understand Short-Circuit Evaluation.
- Learn Assignment Operators.
- Understand the Ternary Operator.
- Learn Operator Precedence and Associativity.
- Write cleaner conditional expressions.

---

# 📚 Table of Contents

1. Relational Operators
2. Logical Operators
3. Short-Circuit Evaluation
4. Assignment Operators
5. Ternary Operator
6. Operator Precedence
7. Associativity
8. JVM Internal Working
9. Memory Diagrams
10. Real-World Applications
11. Common Mistakes
12. Best Practices

---

# 📖 Relational Operators

Relational operators compare two values.

The result is always a **boolean** (`true` or `false`).

| Operator | Meaning | Example |
|----------|---------|----------|
| == | Equal To | a == b |
| != | Not Equal To | a != b |
| > | Greater Than | a > b |
| < | Less Than | a < b |
| >= | Greater Than or Equal To | a >= b |
| <= | Less Than or Equal To | a <= b |

---

## Example

```java
int a = 20;
int b = 10;

System.out.println(a > b);
System.out.println(a < b);
System.out.println(a == b);
System.out.println(a != b);
```

### Output

```
true
false
false
true
```

---

# 🌍 Real-World Example

Login System

```java
if(passwordLength >= 8)
```

Exam Result

```java
if(marks >= 33)
```

Bank Balance

```java
if(balance > withdrawalAmount)
```

---

# 📖 Logical Operators

Logical operators combine multiple conditions.

| Operator | Meaning |
|----------|----------|
| && | Logical AND |
| \|\| | Logical OR |
| ! | Logical NOT |

---

## Logical AND (&&)

Returns **true** only if **both conditions are true**.

### Example

```java
int age = 22;
boolean hasLicense = true;

System.out.println(age >= 18 && hasLicense);
```

Output

```
true
```

Truth Table

| A | B | A && B |
|---|---|---------|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

---

## Logical OR (||)

Returns **true** if **at least one condition is true**.

```java
boolean weekend = false;
boolean holiday = true;

System.out.println(weekend || holiday);
```

Output

```
true
```

Truth Table

| A | B | A \|\| B |
|---|---|-----------|
| T | T | T |
| T | F | T |
| F | T | T |
| F | F | F |

---

## Logical NOT (!)

Reverses the boolean value.

```java
boolean loggedIn = false;

System.out.println(!loggedIn);
```

Output

```
true
```

---

# 🧠 Short-Circuit Evaluation

Java does **not evaluate unnecessary conditions**.

This improves performance.

---

## Example (&&)

```java
int a = 10;

if(a < 5 && ++a > 15){

}
```

Execution

```
a < 5

↓

False

↓

Second condition skipped
```

Value of `a`

```
10
```

because `++a` is never executed.

---

## Example (||)

```java
int a = 10;

if(a > 5 || ++a > 15){

}
```

Execution

```
a > 5

↓

True

↓

Second condition skipped
```

Again,

```
a = 10
```

---

# 📦 Memory Diagram

```text
Stack

a = 10

↓

Condition 1

↓

False

↓

Condition 2

Skipped

↓

a remains 10
```

---

# 📖 Assignment Operators

Assignment operators assign values to variables.

| Operator | Meaning |
|----------|----------|
| = | Assign |
| += | Add & Assign |
| -= | Subtract & Assign |
| *= | Multiply & Assign |
| /= | Divide & Assign |
| %= | Modulus & Assign |

---

## Example

```java
int x = 10;

x += 5;

System.out.println(x);
```

Output

```
15
```

Equivalent to

```java
x = x + 5;
```

---

## More Examples

```java
x -= 2;
```

Equivalent

```java
x = x - 2;
```

---

```java
x *= 3;
```

Equivalent

```java
x = x * 3;
```

---

```java
x /= 2;
```

Equivalent

```java
x = x / 2;
```

---

```java
x %= 3;
```

Equivalent

```java
x = x % 3;
```

---

# 🌍 Real-World Example

Shopping Cart

```java
total += itemPrice;
```

Bank Account

```java
balance -= withdrawal;
```

Game Score

```java
score += 100;
```

---

# 📖 Ternary Operator

The Ternary Operator is a shorthand for an `if-else` statement.

### Syntax

```java
condition ? value1 : value2;
```

---

## Example

```java
int age = 20;

String result = age >= 18 ? "Adult" : "Minor";

System.out.println(result);
```

Output

```
Adult
```

---

## Equivalent if-else

```java
String result;

if(age >= 18){

    result = "Adult";

}else{

    result = "Minor";

}
```

---

# 🌍 Real-World Example

Student Result

```java
String status = marks >= 33 ? "Pass" : "Fail";
```

E-commerce

```java
String offer = premium ? "20% OFF" : "5% OFF";
```

---

# 📖 Operator Precedence

When multiple operators are used in one expression,

Java follows a fixed order.

Higher precedence operators execute first.

| Operator | Priority |
|----------|-----------|
| () | Highest |
| ++ -- ! | High |
| * / % | High |
| + - | Medium |
| < <= > >= | Low |
| == != | Lower |
| && | Lower |
| \|\| | Lowest |
| = | Assignment |

---

## Example

```java
int result = 10 + 5 * 2;
```

Execution

```
5 × 2

↓

10

↓

10 + 10

↓

20
```

Output

```
20
```

---

# 📖 Associativity

If operators have the same precedence,

Java evaluates them using associativity.

Example

```java
20 - 10 - 5
```

Execution

```
20 - 10

↓

10 - 5

↓

5
```

Associativity

```
Left → Right
```

---

# ⚠️ Common Mistakes

### ❌ Using = instead of ==

Wrong

```java
if(a = 10)
```

Correct

```java
if(a == 10)
```

---

### ❌ Confusing && and ||

`&&`

Both conditions must be true.

`||`

Only one condition needs to be true.

---

### ❌ Ignoring Operator Precedence

```java
10 + 5 * 2
```

Output

```
20
```

NOT

```
30
```

---

# 💡 Best Practices

- Use parentheses to improve readability.
- Prefer the ternary operator only for simple conditions.
- Use `&&` and `||` to simplify complex conditions.
- Avoid deeply nested ternary operators.
- Understand precedence before writing complex expressions.

---

# 🚀 Interviewer's Notes

Interviewers frequently ask:

- Difference between `=` and `==`
- Difference between `&&` and `&`
- Difference between `||` and `|`
- What is Short-Circuit Evaluation?
- Explain Operator Precedence.
- When should you use the Ternary Operator?

👉 Always explain with a small code example.