# Java JDBC & JPA Practice

## Overview
An educational project demonstrating two approaches to interacting with a relational database (MySQL) in a Java application: classic JDBC with manual mapping and Object-Relational Mapping (ORM) using JPA/Hibernate with context management.

## Tech Stack
* **Language:** Java
* **Database Interaction:** JDBC API, JPA (Jakarta Persistence), Hibernate
* **Database:** MySQL

## Key Features
The project is divided into two architectural approaches for clear comparison:

### 1. Raw JDBC Implementation
* Management of `Connection`, `Statement`, and `PreparedStatement`.
* Execution of native SQL queries (INSERT, SELECT).
* Protection against SQL injections using parameterized queries (`PreparedStatement`).
* Data extraction from `ResultSet` and manual mapping to Java objects (`Student`).

### 2. JPA (Hibernate) Implementation
* Initialization of `EntityManagerFactory` and `EntityManager`.
* Object-level CRUD operations: `find()`, `remove()`, and field modification (dirty checking).
* Manual transaction management via `EntityTransaction` (`begin()`, `commit()`).
* Safe exception handling with mandatory transaction rollback (`rollback`) and resource closing in a `finally` block[cite: 6].

## Code Snippet: Approach Comparison

**JDBC (Manual Extraction):**
```java
PreparedStatement statement = connection.prepareStatement("SELECT * FROM students WHERE avg_grade > ?");
statement.setDouble(1, 9.0);
ResultSet resultset = statement.executeQuery();
// Requires manual parsing via resultset.next()
