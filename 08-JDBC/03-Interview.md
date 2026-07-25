# 📘 Chapter 08: JDBC (Java Database Connectivity) (Part 3)

> *"JDBC is one of the most important backend technologies for Java developers. Every Java interview expects knowledge of JDBC architecture, CRUD operations, PreparedStatement, transactions, and database connectivity."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand CallableStatement
- Learn JDBC Metadata
- Understand Connection Pooling
- Revise JDBC Concepts
- Solve Interview Questions
- Practice MCQs
- Solve JDBC Coding Problems

---

# 📚 Table of Contents

1. CallableStatement
2. JDBC Metadata
3. Connection Pooling
4. Interview Questions
5. MCQs
6. Practice Problems
7. Best Practices
8. Common Mistakes
9. Chapter Summary

---

# 📖 CallableStatement

CallableStatement is used to execute **Stored Procedures** in a database.

Package

```java
java.sql
```

Syntax

```java
CallableStatement cs =

con.prepareCall(

"{call procedure_name()}"

);
```

---

## Example

Suppose a stored procedure exists:

```sql
CALL getStudents();
```

Java Code

```java
CallableStatement cs =

con.prepareCall(

"{call getStudents()}"

);

ResultSet rs =

cs.executeQuery();
```

Output

```text
Student Records Retrieved
```

---

# 📖 Why Use CallableStatement?

Advantages

- Faster execution
- Supports stored procedures
- Reduces network traffic
- Business logic stays inside the database
- Better performance for repeated operations

---

# 📖 JDBC Metadata

Metadata means **data about data**.

JDBC provides metadata about

- Database
- Tables
- Columns
- Drivers
- Connections

---

## DatabaseMetaData

Used to retrieve database information.

Example

```java
DatabaseMetaData db =

con.getMetaData();

System.out.println(

db.getDatabaseProductName()

);
```

Output

```text
MySQL
```

---

## Common DatabaseMetaData Methods

| Method | Description |
|---------|-------------|
| getDatabaseProductName() | Database name |
| getDriverName() | JDBC Driver name |
| getDriverVersion() | Driver version |
| getUserName() | Connected username |
| getURL() | Database URL |

---

# 📖 ResultSetMetaData

Provides information about query results.

Example

```java
ResultSetMetaData rsmd =

rs.getMetaData();

System.out.println(

rsmd.getColumnCount()

);
```

Output

```text
5
```

---

## Common ResultSetMetaData Methods

| Method | Description |
|---------|-------------|
| getColumnCount() | Total columns |
| getColumnName() | Column name |
| getColumnTypeName() | Data type |
| getTableName() | Table name |

---

# 📖 Connection Pooling

Creating a new database connection every time is expensive.

Instead,

applications reuse existing connections.

```text
Application

↓

Connection Pool

↓

Database
```

---

## Advantages

- Faster
- Better Performance
- Lower Memory Usage
- Better Scalability
- Reduced Database Load

---

## Popular Connection Pool Libraries

- HikariCP ⭐ (Most Popular)
- Apache DBCP
- C3P0
- Tomcat JDBC Pool

---

# 📖 JDBC Lifecycle

```text
Load Driver

↓

Open Connection

↓

Create Statement

↓

Execute SQL

↓

Process Result

↓

Close Resources
```

---

# 📦 Internal Working

```text
Java Program

↓

JDBC API

↓

DriverManager

↓

Connection

↓

PreparedStatement

↓

Database

↓

ResultSet

↓

Java Program
```

---

# 💡 Best Practices

- Prefer **PreparedStatement** over Statement.
- Use **try-with-resources** to close resources automatically.
- Use **Connection Pooling** in enterprise applications.
- Commit transactions only after successful execution.
- Rollback transactions if an error occurs.
- Store credentials securely.
- Never expose database passwords in source code.

---

# ⚠️ Common Mistakes

## ❌ Hardcoding Credentials

Wrong

```java
String password = "root123";
```

Correct

Store credentials in

- properties file
- environment variables
- Spring Boot configuration

---

## ❌ Forgetting to Close Resources

Wrong

```java
Connection con =
DriverManager.getConnection(...);
```

Never left open.

Correct

```java
try(

Connection con =

DriverManager.getConnection(...)

){

}
```

---

## ❌ Using Statement Instead of PreparedStatement

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

## ❌ Ignoring Transactions

Wrong

```java
ps.executeUpdate();

ps.executeUpdate();
```

If one query fails, the database may become inconsistent.

Correct

```java
con.setAutoCommit(false);

try{

    ps.executeUpdate();

    ps.executeUpdate();

    con.commit();

}

catch(SQLException e){

    con.rollback();

}
```

---

# 🎤 Interview Questions

## Beginner Level

### Q1. What is JDBC?

**Answer**

JDBC (Java Database Connectivity) is a Java API used to connect Java applications with relational databases.

---

### Q2. Which package contains JDBC classes?

**Answer**

```java
java.sql
```

---

### Q3. Which class creates a database connection?

**Answer**

```java
DriverManager
```

Method

```java
getConnection()
```

---

### Q4. Difference between Statement and PreparedStatement?

| Statement | PreparedStatement |
|------------|-------------------|
| Dynamic SQL | Precompiled SQL |
| Slower | Faster |
| SQL Injection Possible | SQL Injection Prevented |
| No Parameters | Supports Parameters |

---

### Q5. What is ResultSet?

**Answer**

ResultSet stores the data returned by a **SELECT** query.

---

# 🎤 Intermediate Questions

### Q6. Difference between executeQuery() and executeUpdate()?

| executeQuery() | executeUpdate() |
|----------------|-----------------|
| SELECT | INSERT, UPDATE, DELETE |
| Returns ResultSet | Returns affected row count |

---

### Q7. What is SQL Injection?

**Answer**

SQL Injection is a security attack where malicious SQL code is injected through user input.

Solution

```java
PreparedStatement
```

---

### Q8. What is Connection Pooling?

**Answer**

Connection Pooling maintains reusable database connections to improve application performance.

---

### Q9. What is CallableStatement?

**Answer**

CallableStatement is used to execute stored procedures.

---

### Q10. What is DatabaseMetaData?

**Answer**

DatabaseMetaData provides information about the connected database, driver, URL, username, and supported features.

---

# 🎓 MCQs

### Q1. JDBC stands for

- A. Java Database Connectivity ✅
- B. Java Data Compiler
- C. Java Driver Connector
- D. Java Dynamic Connection

---

### Q2. Which package contains JDBC?

- A. java.io
- B. java.sql ✅
- C. java.net
- D. java.util

---

### Q3. Which class creates database connections?

- A. DriverManager ✅
- B. ResultSet
- C. Statement
- D. ConnectionPool

---

### Q4. Which interface prevents SQL Injection?

- A. Statement
- B. PreparedStatement ✅
- C. CallableStatement
- D. ResultSet

---

### Q5. Which object stores SELECT query results?

- A. Statement
- B. ResultSet ✅
- C. DriverManager
- D. Connection

---

### Q6. Which method executes SELECT queries?

- A. execute()
- B. executeQuery() ✅
- C. executeUpdate()
- D. executeSQL()

---

### Q7. Which method executes INSERT statements?

- A. executeQuery()
- B. executeUpdate() ✅
- C. executeSelect()
- D. executeInsert()

---

### Q8. Which object executes stored procedures?

- A. PreparedStatement
- B. CallableStatement ✅
- C. Statement
- D. ResultSet

---

### Q9. Which library is the most popular connection pool?

- A. JDBC Bridge
- B. HikariCP ✅
- C. Swing
- D. JPA

---

### Q10. Which metadata class provides database information?

- A. DatabaseMetaData ✅
- B. ResultMeta
- C. DriverMeta
- D. SQLMeta

---

# 💻 Practice Problems

## Beginner

1. Connect Java with MySQL.
2. Insert a student record.
3. Update a student record.
4. Delete a student record.
5. Display all student records.

---

## Intermediate

6. Search a student by ID using PreparedStatement.
7. Implement login authentication using PreparedStatement.
8. Display database metadata.
9. Display ResultSet metadata.
10. Execute a stored procedure.

---

## Advanced

11. Implement transaction management.
12. Perform batch inserts using PreparedStatement.
13. Create a Student Management System using JDBC.
14. Build an Employee Payroll Management System.
15. Implement Connection Pooling using HikariCP.

---

# 🌍 Real-World Applications

JDBC is widely used in

- Banking Applications
- Student Management Systems
- Hospital Management Systems
- Inventory Management Systems
- ERP Software
- Payroll Systems
- Spring Boot Applications
- Financial Software
- E-Commerce Platforms
- Enterprise Java Applications

---

# 📚 References

- Oracle JDBC Documentation
- MySQL Connector/J Documentation
- OpenJDK Documentation
- Effective Java – Joshua Bloch
- Head First Java
- Java: The Complete Reference

---

# 🎉 Chapter Summary

Congratulations! 🎉

You have successfully completed **08-JDBC.md**

### ✔️ Concepts Covered

- JDBC Introduction
- JDBC Architecture
- JDBC Drivers
- DriverManager
- Connection
- Statement
- PreparedStatement
- CallableStatement
- ResultSet
- CRUD Operations
- Transactions
- Batch Processing
- DatabaseMetaData
- ResultSetMetaData
- Connection Pooling
- Interview Questions
- MCQs
- Practice Problems

---

# 📌 Key Takeaways

- ✅ JDBC is the standard API for connecting Java applications to relational databases.
- ✅ Always use **PreparedStatement** for user input to improve security and prevent SQL Injection.
- ✅ Use `executeQuery()` for **SELECT** statements and `executeUpdate()` for **INSERT**, **UPDATE**, and **DELETE** operations.
- ✅ Manage transactions using `commit()` and `rollback()` to maintain data consistency.
- ✅ Use **Connection Pooling** (such as HikariCP) in production applications for better performance.
- ✅ JDBC is the foundation of higher-level frameworks like **Hibernate** and **Spring Data JPA**.

---

# 🚀 Next Chapter

➡️ **09-Sorting-Searching.md**

### Topics Covered

## Topics Covered

- Introduction to Searching
- Why Searching is Important
- Types of Searching
- Linear Search
- Binary Search
- Iterative Binary Search
- Recursive Binary Search
- Linear Search vs Binary Search
- Arrays.binarySearch()
- Collections.binarySearch()
- Searching Objects
- Searching using Comparator
- Searching in Arrays
- Searching in Collections
- Searching in Sorted vs Unsorted Data
- Time Complexity Analysis
- Best Practices
- Common Mistakes
- Real-World Applications
- Interview Questions
- MCQs
- Practice Problems