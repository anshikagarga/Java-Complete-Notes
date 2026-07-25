# 📘 Chapter 08: JDBC (Java Database Connectivity) (Part 1)

> *"JDBC (Java Database Connectivity) is the standard Java API used to connect Java applications with relational databases like MySQL, Oracle, PostgreSQL, SQL Server, and SQLite. Almost every Java backend application uses JDBC directly or indirectly (through Hibernate or Spring Data JPA)."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand JDBC
- Learn JDBC Architecture
- Understand JDBC Drivers
- Connect Java with MySQL Database
- Learn JDBC API Components
- Execute SQL Queries using Java
- Understand JDBC Workflow

---

# 📚 Table of Contents

1. Introduction to JDBC
2. Why JDBC?
3. JDBC Architecture
4. JDBC Drivers
5. JDBC API Components
6. JDBC Workflow
7. Steps to Connect Java with Database
8. First JDBC Program
9. Best Practices
10. Common Mistakes

---

# 📖 What is JDBC?

JDBC (Java Database Connectivity) is a standard Java API that allows Java applications to communicate with relational databases.

Using JDBC, Java programs can:

- Insert data
- Update data
- Delete data
- Retrieve data
- Execute SQL queries
- Execute Stored Procedures

---

# 🌍 Databases Supported by JDBC

JDBC works with almost every relational database.

Examples

- MySQL
- Oracle Database
- PostgreSQL
- Microsoft SQL Server
- SQLite
- MariaDB
- IBM DB2

---

# 💡 Why Do We Need JDBC?

Suppose we have

```text
Java Application
```

and

```text
MySQL Database
```

Java cannot directly communicate with MySQL.

JDBC acts as a bridge.

```text
Java Application

↓

JDBC API

↓

JDBC Driver

↓

Database
```

---

# 📖 JDBC Architecture

```text
Java Application

↓

JDBC API

↓

DriverManager

↓

JDBC Driver

↓

Database
```

Explanation

### Java Application

Contains business logic.

↓

### JDBC API

Provides Java interfaces and classes.

↓

### DriverManager

Loads the appropriate database driver.

↓

### JDBC Driver

Converts Java calls into database-specific commands.

↓

### Database

Executes SQL queries.

---

# 📖 JDBC Drivers

A JDBC Driver is software that enables Java to communicate with a database.

Without a JDBC Driver,

Java cannot connect to the database.

---

## Types of JDBC Drivers

### Type 1 Driver

JDBC-ODBC Bridge Driver

```text
Java

↓

JDBC

↓

ODBC

↓

Database
```

- Old technology
- Removed from Java 8
- Not used today

---

### Type 2 Driver

Native API Driver

```text
Java

↓

Native Library

↓

Database
```

Advantages

- Faster than Type 1

Disadvantages

- Platform dependent

---

### Type 3 Driver

Network Protocol Driver

```text
Java

↓

Middleware Server

↓

Database
```

Advantages

- Platform independent

Disadvantages

- Requires middleware server

---

### Type 4 Driver ⭐ (Most Important)

Thin Driver

```text
Java

↓

JDBC Driver

↓

Database
```

Examples

- MySQL Connector/J
- PostgreSQL JDBC Driver
- Oracle JDBC Driver

Advantages

- Fast
- Platform independent
- Most widely used
- No native library required

---

# 📖 JDBC API Components

The `java.sql` package provides the main JDBC classes and interfaces.

| Class / Interface | Purpose |
|-------------------|----------|
| DriverManager | Manages database drivers |
| Connection | Represents a database connection |
| Statement | Executes SQL queries |
| PreparedStatement | Executes parameterized SQL queries |
| CallableStatement | Executes stored procedures |
| ResultSet | Stores query results |
| SQLException | Handles database errors |

---

# 📖 JDBC Workflow

```text
Load Driver

↓

Create Connection

↓

Create Statement

↓

Execute SQL Query

↓

Process Result

↓

Close Resources
```

---

# 📖 Steps to Connect Java with Database

### Step 1

Import package

```java
import java.sql.*;
```

---

### Step 2

Load Driver

```java
Class.forName(

"com.mysql.cj.jdbc.Driver"

);
```

> **Note:** In JDBC 4.0 and later, explicit driver loading is often optional because drivers are auto-loaded when present on the classpath.

---

### Step 3

Create Connection

```java
Connection con =

DriverManager.getConnection(

"url",

"username",

"password"

);
```

Example

```java
Connection con =

DriverManager.getConnection(

"jdbc:mysql://localhost:3306/studentdb",

"root",

"password"

);
```

---

### Step 4

Create Statement

```java
Statement st =

con.createStatement();
```

---

### Step 5

Execute Query

```java
ResultSet rs =

st.executeQuery(

"SELECT * FROM student"

);
```

---

### Step 6

Process Result

```java
while(rs.next()){

    System.out.println(

    rs.getInt("id")

    );

}
```

---

### Step 7

Close Connection

```java
rs.close();

st.close();

con.close();
```

---

# 💻 First JDBC Program

```java
import java.sql.*;

public class Demo {

    public static void main(String[] args) {

        try {

            Connection con = DriverManager.getConnection(

                "jdbc:mysql://localhost:3306/studentdb",

                "root",

                "password"

            );

            System.out.println("Connected Successfully!");

            con.close();

        }

        catch(SQLException e) {

            e.printStackTrace();

        }

    }

}
```

Output

```text
Connected Successfully!
```

---

# 📦 Internal Working

```text
Java Program

↓

DriverManager

↓

Connection

↓

Statement

↓

SQL Query

↓

Database

↓

ResultSet

↓

Java Program
```

---

# 💡 Best Practices

- Use **PreparedStatement** instead of Statement for user input.
- Always close database resources after use.
- Use **try-with-resources** whenever possible.
- Store database credentials securely (e.g., configuration files or environment variables).
- Handle `SQLException` properly.

---

# ⚠️ Common Mistakes

## ❌ Forgetting JDBC Driver Dependency

Without the JDBC driver JAR (or Maven/Gradle dependency), the application cannot connect to the database.

---

## ❌ Hardcoding Credentials

Wrong

```java
String password = "root123";
```

Better

Read credentials from a configuration file or environment variables.

---

## ❌ Not Closing Resources

Wrong

```java
Connection con = DriverManager.getConnection(...);

// Never closed
```

Correct

```java
con.close();
```

or use try-with-resources.

---

## ❌ Using Statement for User Input

Wrong

```java
Statement st = con.createStatement();
```

For dynamic values, prefer `PreparedStatement` to improve security and avoid SQL Injection.

---

# 🎯 Interview Tip

### Question

What are the basic steps to connect a Java application with a database using JDBC?

### Answer

1. Import `java.sql` package.
2. Load the JDBC Driver (optional in modern JDBC if auto-loaded).
3. Create a `Connection`.
4. Create a `Statement` or `PreparedStatement`.
5. Execute SQL queries.
6. Process the `ResultSet`.
7. Close all resources.

---

# 🚀 Next: Part 2

In **Part 2**, we'll cover:

- Statement vs PreparedStatement
- PreparedStatement
- ResultSet
- CRUD Operations
- ExecuteQuery vs ExecuteUpdate
- SQL Injection
- Batch Processing
- Transactions