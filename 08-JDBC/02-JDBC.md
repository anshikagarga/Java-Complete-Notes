# 📘 Chapter 08: JDBC (Java Database Connectivity) (Part 2)

> *"JDBC provides different objects for executing SQL statements. Choosing the correct object—Statement, PreparedStatement, or CallableStatement—improves performance, security, and maintainability."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand Statement
- Learn PreparedStatement
- Learn ResultSet
- Perform CRUD Operations
- Understand executeQuery() and executeUpdate()
- Prevent SQL Injection
- Learn Batch Processing
- Understand Transactions

---

# 📚 Table of Contents

1. Statement
2. PreparedStatement
3. Statement vs PreparedStatement
4. ResultSet
5. CRUD Operations
6. executeQuery() vs executeUpdate()
7. SQL Injection
8. Batch Processing
9. Transactions
10. Best Practices

---

# 📖 Statement

A Statement is used to execute simple SQL queries.

Syntax

```java
Statement st =

con.createStatement();
```

Execute Query

```java
ResultSet rs =

st.executeQuery(

"SELECT * FROM student"

);
```

Execute Update

```java
st.executeUpdate(

"DELETE FROM student"

);
```

---

# 📖 Limitations of Statement

Statement is not recommended for user input because

- SQL Injection Risk
- Poor Performance
- SQL is compiled every time

---

# 📖 PreparedStatement

PreparedStatement is an improved version of Statement.

Advantages

- Faster
- More Secure
- Prevents SQL Injection
- Supports Parameters

Syntax

```java
PreparedStatement ps =

con.prepareStatement(

"SELECT * FROM student WHERE id=?"

);
```

---

# 📖 Setting Parameters

```java
ps.setInt(1,101);
```

Execute

```java
ResultSet rs =

ps.executeQuery();
```

---

# 💻 Example

```java
PreparedStatement ps =

con.prepareStatement(

"SELECT * FROM student WHERE id=?"

);

ps.setInt(1,101);

ResultSet rs =

ps.executeQuery();
```

---

# 📊 Statement vs PreparedStatement

| Statement | PreparedStatement |
|------------|-------------------|
| Dynamic SQL | Precompiled SQL |
| Slower | Faster |
| SQL Injection Possible | SQL Injection Prevented |
| No Parameters | Supports Parameters |
| Less Efficient | More Efficient |

---

# 📖 ResultSet

ResultSet stores the data returned by a SELECT query.

```text
Database

↓

SELECT Query

↓

ResultSet
```

---

# 📖 Reading Data

```java
while(rs.next()){

    System.out.println(

    rs.getInt("id")

    );

    System.out.println(

    rs.getString("name")

    );

}
```

---

# 📖 Common ResultSet Methods

| Method | Description |
|----------|-------------|
| next() | Move to next row |
| previous() | Move to previous row (scrollable ResultSet) |
| first() | Move to first row |
| last() | Move to last row |
| getInt() | Read integer |
| getString() | Read String |
| getDouble() | Read double |
| getBoolean() | Read boolean |

---

# 📖 CRUD Operations

CRUD stands for

```text
Create

Read

Update

Delete
```

---

## Create (INSERT)

```java
PreparedStatement ps =

con.prepareStatement(

"INSERT INTO student VALUES(?,?)"

);

ps.setInt(1,101);

ps.setString(2,"Anshika");

ps.executeUpdate();
```

---

## Read (SELECT)

```java
PreparedStatement ps =

con.prepareStatement(

"SELECT * FROM student"

);

ResultSet rs =

ps.executeQuery();
```

---

## Update

```java
PreparedStatement ps =

con.prepareStatement(

"UPDATE student SET name=? WHERE id=?"

);

ps.setString(1,"Rahul");

ps.setInt(2,101);

ps.executeUpdate();
```

---

## Delete

```java
PreparedStatement ps =

con.prepareStatement(

"DELETE FROM student WHERE id=?"

);

ps.setInt(1,101);

ps.executeUpdate();
```

---

# 📖 executeQuery() vs executeUpdate()

| executeQuery() | executeUpdate() |
|----------------|-----------------|
| SELECT | INSERT |
| Returns ResultSet | Returns int |
| Used for Reading | Used for Create, Update, Delete |

---

### executeQuery()

```java
ResultSet rs =

ps.executeQuery();
```

Returns

```text
ResultSet
```

---

### executeUpdate()

```java
int rows =

ps.executeUpdate();
```

Returns

```text
Number of affected rows
```

Example

```text
1 Row Updated
```

---

# 📖 SQL Injection

SQL Injection is a security vulnerability where malicious SQL code is inserted into user input.

Wrong

```java
String sql =

"SELECT * FROM student WHERE name='"

+ name +

"'";
```

If the user enters

```text
' OR '1'='1
```

the query may return all records.

---

# ✅ Prevent SQL Injection

Use PreparedStatement.

```java
PreparedStatement ps =

con.prepareStatement(

"SELECT * FROM student WHERE name=?"

);

ps.setString(1,name);
```

The input is treated as data, not executable SQL.

---

# 📖 Batch Processing

Batch Processing executes multiple SQL statements together.

Advantages

- Faster
- Fewer database calls
- Better performance

Example

```java
PreparedStatement ps =

con.prepareStatement(

"INSERT INTO student VALUES(?,?)"

);

ps.setInt(1,101);
ps.setString(2,"Aman");
ps.addBatch();

ps.setInt(1,102);
ps.setString(2,"Riya");
ps.addBatch();

ps.executeBatch();
```

---

# 📖 Transactions

A transaction is a group of SQL operations executed as one unit.

Properties

- All operations succeed, or
- All operations fail.

---

### Auto Commit

By default

```java
con.setAutoCommit(true);
```

Each SQL statement is committed automatically.

---

### Manual Transaction

```java
con.setAutoCommit(false);

ps.executeUpdate();

ps.executeUpdate();

con.commit();
```

---

### Rollback

If an error occurs

```java
con.rollback();
```

Database returns to the previous consistent state.

---

# 📦 Internal Working

```text
Java Program

↓

PreparedStatement

↓

SQL Query

↓

Database

↓

ResultSet / Update Count

↓

Java Program
```

---

# 💡 Best Practices

- Prefer **PreparedStatement** over Statement.
- Use parameterized queries to prevent SQL Injection.
- Close `ResultSet`, `Statement`, and `Connection`.
- Use transactions for multiple related operations.
- Use batch processing for bulk inserts and updates.
- Handle `SQLException` properly.
- Use try-with-resources to automatically close resources.

---

# ⚠️ Common Mistakes

## ❌ Using Statement with User Input

Wrong

```java
Statement st =

con.createStatement();
```

Correct

```java
PreparedStatement ps =

con.prepareStatement(

"SELECT * FROM student WHERE id=?"

);
```

---

## ❌ Forgetting commit()

When AutoCommit is disabled

```java
con.setAutoCommit(false);
```

Always call

```java
con.commit();
```

Otherwise, changes will not be saved.

---

## ❌ Forgetting rollback()

If an exception occurs

```java
catch(SQLException e){

    con.rollback();

}
```

This keeps the database consistent.

---

## ❌ Not Closing Resources

Wrong

```java
Connection con =

DriverManager.getConnection(...);
```

Never left open.

Correct

Use

```java
try-with-resources
```

or explicitly call

```java
rs.close();

ps.close();

con.close();
```

---

# 🌍 Real-World Applications

JDBC is widely used in:

- Banking Applications
- Student Management Systems
- Hospital Management Systems
- E-Commerce Platforms
- Payroll Systems
- Inventory Management
- ERP Software
- Spring Boot Applications
- Financial Systems
- Enterprise Java Applications

---

# 🎯 Interview Tip

### Question

Why is PreparedStatement preferred over Statement?

### Answer

PreparedStatement is preferred because it:

- Prevents SQL Injection attacks.
- Uses precompiled SQL, improving performance.
- Supports parameterized queries.
- Produces cleaner and more maintainable code.

---

# 🚀 Next: Part 3

In **Part 3**, we'll cover:

- CallableStatement
- JDBC Metadata
- Connection Pooling
- JDBC Interview Questions
- MCQs
- Practice Problems
- Chapter Summary