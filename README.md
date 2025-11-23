# Database Management System (DBMS) Notes  

This repository contains concise notes on **DBMS fundamentals**, architecture, and concepts.  

---

## 📌 Data vs Information  
- **Data** → Collection of raw bytes (stored in bits and bytes).  
  - Unorganized, meaningless until processed.  
- **Information** → Processed, meaningful data.  

---

## 📌 Database  
- A **database** is an electronic place/system where data is stored in a way that it can be **easily accessed, managed, and updated**.  

---

## 📌 DBMS (Database Management System)  
- A collection of **interrelated data (database)** and a set of **programs to access those data**.
- A Database Management System (DBMS) is software that allows users to create, store, manage, and retrieve data efficiently from a database while ensuring data integrity, security, and consistency. 

---

## 📌 File System vs DBMS  

| Issue | File System | DBMS |
|-------|-------------|------|
| Data Redundancy | High (duplication, inconsistency) | Reduced |
| Data Access | Difficult | Easy |
| Data Isolation | Stored in different formats | Centralized |
| Integrity | Constraint handling issues | Enforced constraints |
| Atomicity | Hard to control processes (e.g., payment) | Transactions ensure atomicity |
| Concurrent Access | Anomalies possible | Handled by DBMS |
| Security | Weak | Strong, centralized |

---

## 📌 Data Abstraction  
- **Definition**: Hides unnecessary details and shows only relevant data to the user.  
- **Note**: Structure at the **physical level** does not affects the structure at the **logical level**.  

### Three-Schema Architecture  
1. **Physical Level** (lowest abstraction)  
   - Database storage details.  
   - **Physical Schema** → Describes physical structure of data storage.  

2. **Logical/Conceptual Level**  
   - Organized representation of data and relationships.  
   - **Logical Schema** → Describes the design of database at conceptual level.  

3. **View Level** (highest abstraction)  
   - Custom view for users.  
   - **View Schema** → Describes the part of the database relevant to a particular user/group.  

---

## 📌 Database Instance  
- **Instance** → Data stored in the database **at a particular moment of time**.  

---

## 📌 Structure of Logical Schema  
- Attributes of tables  
- Consistency constraints (rules & checks)  
- Relationships  

---

## 📌 Data Models  
- Tools for describing data, relationships, semantics, and constraints.  
- Examples:  
  - ER Model  
  - Relational Model  
  - Object-Oriented Model  
  - Object-Relational Model  

---

## 📌 Database Languages  
1. **DDL (Data Definition Language)** → Defines database schema.  
2. **DML (Data Manipulation Language)** → Queries and updates data.  

➡️ Example: **SQL** (provides both DDL & DML).  

- **Use Case**:  
  - Defining schema → Use **DDL**.  
  - Making changes to stored data → Use **DML**.  

---

## 📌 Application Access to Database  
- Applications are written in different programming languages (**Java, C, C++**).  
- But databases only understand **DDL/DML**.  
- To bridge this gap → **API** converts programming code into database queries.  

| Language | API |
|----------|-----|
| Java     | JDBC (Java Database Connectivity) |
| C/C++    | ODBC (Open Database Connectivity) |

---

## 📌 Database Administrator (DBA)  
A **DBA** is a person who has central control over both data and programs accessing that data.  

### Responsibilities:  
- Works at **logical level**.  
- Authorization control.  
- Schema definition and manipulation.  
- Routine maintenance (backups, security patches, upgrades).  

---

## 📌 DBMS Application Architecture  

### 🔹 Tier-1 (T-1)  
- Client, server, and database on the **same system**.  
- Example: Running SQL locally.  

### 🔹 Tier-2 (T-2)  
- Client (**P1**) → API connection → Database Server (**P2**).  
- Direct client-server call.  

### 🔹 Tier-3 (T-3)  
- Client (**P1**) → Application Server (**P2**) → Database Server (**P3**).  
- **Advantages**:  
  - Scalability  
  - Security  
  - Data Integrity  

---

## ✅ Summary  
- Data → Information (after processing).  
- DBMS overcomes file system limitations.  
- Abstraction = physical, logical, view levels.  
- SQL = DDL + DML.  
- APIs like **JDBC/ODBC** connect applications with databases.  
- DBA ensures smooth functioning of database systems.  
- DBMS architectures: T-1, T-2, T-3 (for different scales of applications).  

---

# Entity-Relationship (ER) Model  

The **Entity-Relationship (ER) Model** is a **high-level data model** based on the real-world perception of entities and the relationships among them.  
- Acts as a **blueprint of the database**.  
- Consists of **entities**, their **attributes**, and **relationships**.  

---

## 📌 Key Concepts  

### 🔹 Entity  
- **Definition**: A basic object that exists in the real world and is distinguishable from other objects.  
- **Entity Set**: Collection of entities of the same type with the same properties or attributes.  
- **Example**:  
  - Customer  
  - Order  
  - Loan  

### 🔹 Attributes  
Attributes describe the properties of an entity.  
Among them, one attribute is chosen as the **primary key** to uniquely identify the entity.  

#### Types of Attributes  
1. **Simple Attribute** → Cannot be divided further.  
   - Example: `Student_ID`  
2. **Composite Attribute** → Can be subdivided.  
   - Example: `Name (First, Middle, Last)`  
3. **Single-Valued Attribute** → Only one value per entity.  
   - Example: `Student_ID`  
4. **Multi-Valued Attribute** → Can have multiple values.  
   - Example: `Phone Numbers`  
5. **Derived Attribute** → Derived from other attributes.  
   - Example: `Age` (derived from DOB), `Loan Duration`  
6. **Null Value** → Attribute may have no value.  
   - Example: `Middle Name` (missing or not known)  

---

## 📌 Relationships  

- **Definition**: Association among two or more entities.  
- **Examples**:  
  - Customer places Order → `(Customer, Order)`  
  - Customer borrows Loan → `(Customer, Loan)`  

### Types of Relationships  
1. **Strong Relationship**  
   - A relationship where the child entity CAN be uniquely identified by its own primary key, without depending on another entity.  
   - Example: Customer–Order.
   - Order exists independently. Even if the customer leaves, the order record still stays.
2. **Weak Relationship**  
   - A relationship where the child entity CANNOT be uniquely identified without the parent entity.  
   - Example: Loan–Payment (payment exists only if loan exists).  

---

## 📌 Degree of Relationship  
Defines how many entities participate in a relationship:  
1. **Unary Relationship** → Involves one entity type.  
2. **Binary Relationship** → Involves two entities (most common).  
3. **Ternary Relationship** → Involves three entities.  

---

## 📌 Relationship Constraints  

### 1. Mapping Cardinality  
Specifies the number of entities that can participate in a relationship:  
- **One-to-One (1:1)** → One entity relates with only one other.  
- **One-to-Many (1:N)** → One entity can relate to many others, but the reverse is one-to-one.  
- **Many-to-One (N:1)** → Reverse of one-to-many.  
- **Many-to-Many (M:N)** → Entities on both sides can have multiple associations.  
  - Example: `Customer ↔ Product` (a customer can buy many products, and a product can be bought by many customers).  

### 2. Participation Constraints  
- **Partial Participation** → Not all entities are involved.  
- **Total Participation** → Every entity must participate.  

👉 **Note**: A **Weak Entity** always has **Total Participation** in its identifying relationship.  

---

## ✅ Summary  
- **ER Model** provides a conceptual design of the database.  
- **Entities** represent real-world objects.  
- **Attributes** define properties of entities.  
- **Relationships** capture associations between entities.  
- **Constraints** (Mapping & Participation) refine how entities interact.  

---


## 🔹 Extended ER Features  

When building real-world projects, databases often become complex. To handle this, we use **Extended ER (EER) features** such as **Specialization, Generalization, and Aggregation**.  

### 1. Specialization  
- A process of dividing an entity into **sub-entities** based on their attributes.  
- Helps make the database more **understandable**.  
- Works like **inheritance** in OOP.  
- **Approach** → Top-down.  

✅ Example:  
- `Employee` entity can be specialized into `Teacher`, `Engineer`, `Doctor`, etc.  

---

### 2. Generalization  
- The **reverse** of specialization.  
- Combines two or more entities having common features into a **generalized entity set**.  
- **Approach** → Bottom-up.  

✅ Example:  
- `Car`, `Motorbike`, and `Cycle` can be generalized into a single `Vehicle` entity.  

---

### 3. Aggregation  
- Used to represent **relationships among relationships**.
- It allows us to treat an entire relationship as a higher-level entity.  
- Involves **abstraction** where a relationship is treated as a **higher-level entity set** (abstract entity).  

✅ Example:  
- A Manager supervises the work that an Employee does on a Project.
- The manager does NOT supervise the Employee directly . The manager supervises the work relationship between Employee and Project.
- We combine the relationship works_on with its two entities (Employee + Project) and treat it as a single higher-level entity.
```sql
 [Employee — works_on — Project]   →  aggregated into a box
``` 

---

### 📝 Steps to Create an ER Diagram  
1. Identify **entity sets**.  
2. Identify their **attributes**.  
3. Identify **constraints and relationships**.  
4. Specify **mapping cardinality** and **participation**.  

---

## 🔹 Relational Model  

In the relational model, data is represented in the form of **tables (relations)**.  

- **Structure:**  
  - **Entity → Table**  
  - **Attributes → Columns**  
  - Values in attributes must be **atomic** (indivisible).  
  - Sequence of columns **does not matter**.  

- **Relation Schema:**  
  - Describes the **design and structure** of a relation.  
  - Includes the **relation name** and all attributes.  

✅ Example:  
```sql
Customer(Customer_ID, Name, Address, Contact_No)  
Order(Order_ID, Timestamp, Delivery)

```

# 🔑 Relational Model Keys & Integrity Constraints  

This section covers different types of **keys** in the relational model and the **integrity constraints** that ensure consistency in a database.  

---

## 🔹 Relational Model Keys  

Keys are always defined on **attributes**. They are used to uniquely identify tuples (rows) in a table.  
- tuple(row in the table)

### 1. Super Key  
- Any combination of attributes that can **uniquely identify a tuple** in a table.  

---

### 2. Candidate Key  
- A **minimal subset** of a super key.  
- Can uniquely identify a tuple but does not contain **redundant attributes**.  
- **Cannot be NULL**.  

---

### 3. Primary Key  
- Chosen from the candidate keys.  
- Has the **least number of attributes**.  
- Every relation can have **only one primary key**.


### note-->
- combination of the primary key
--> combination of two or more cols 
-> in this both can have duplicate values but together it will always have unique combination
```sql
primary key ( col1 , col2 );

```

---

### 4. Alternate Key  
- Candidate keys that are **not selected** as the primary key.  

---

### 5. Foreign Key  
- Used to establish **relationships between entities**.  
- Works by taking the **primary key of one table** and adding it into another table.  

**Terms:**  
- **Referenced Relation / Parent Table** → The table whose primary key is used.  
- **Referencing Relation / Child Table** → The table where the foreign key is placed.  

✅ Example:  
```sql
CREATE TABLE Orders (
    Order_ID INT PRIMARY KEY,
    Customer_ID INT,
    FOREIGN KEY (Customer_ID) REFERENCES Customer(Customer_ID)
        ON DELETE CASCADE
);
```









---
---
# 📘 SQL Notes  

This document contains concise notes on **SQL fundamentals**, data types, commands, and examples.  

---

## 🔹 What is SQL?  
**SQL (Structured Query Language)** is a database language used to **interact with relational databases**.  
It helps perform CRUD operations (**Create, Read, Update, Delete**) on data.  

- Example:  
  - **MySQL** → An RDBMS (Relational Database Management System) that uses SQL.
  
---

## 🗃️ Example of RDBMS

**MySQL** → A popular Relational Database Management System (RDBMS) that uses SQL for CRUD operations  
(CRUD → Create, Read, Update, Delete)

---

## 📊 SQL Data Types

### 🔢 Numeric Types
| Type | Description |
|------|--------------|
| `INT` | Integer value (normal range) |
| `BIGINT` | Larger range of integer |
| `FLOAT` | Decimal with precision of up to 23 digits |
| `DOUBLE` | Decimal with precision between 24–53 digits |

---

### 🔤 String Types
| Type | Description |
|------|--------------|
| `CHAR(n)` | Fixed-length string. Even if data is smaller, storage size remains constant |
| `VARCHAR(n)` | Variable-length string |
| `TEXT` | Like `VARCHAR` but supports longer text (0–65535 characters) |
| `BLOB` | Binary Large Object — used to store files like images, videos, and audio |

---

### ⚙️ Other Data Types
| Type | Description |
|------|--------------|
| `BOOLEAN` | Stores `0` (false) or `1` (true) |
| `DATE` | Format: `YYYY-MM-DD` |
| `TIME` | Format: `HH:MM:SS` |
| `DATETIME` | Combination of date and time |
| `JSON` | Advanced datatype for storing JSON (JavaScript Object Notation) |

📝 **Note:**  
MySQL supports **signed** and **unsigned** numeric types.  
Unsigned types increase the positive range (no negative values).
```sql
CREATE TABLE signed_example (
    num1 INT SIGNED, //default
    num2 INT UNSIGNED
);

```

---

## 🧩 Types of SQL Commands

| Type | Full Form | Description | Commands |
|------|------------|--------------|---------------|
| **DDL** | Data Definition Language | Define or modify database structure | CREATE , ALTER , RENAME , TRUNCATE and DROP |
| **DML** | Data Manipulation Language | Manipulate data inside tables | INSERT , UPDATE and DELETE |
| **DQL** | Data Query Language | Query and fetch data | SELECT |
| **DCL** | Data Control Language | Manage access and permissions | not important for now |
| **TCL** | Transaction Control Language | Manage transactions | not important for now |

---

## 🧱 DDL — Data Definition Language

### 1️⃣ Create a Database
```sql

CREATE DATABASE company;

//better and professional way
CREATE DATABASE IF NOT EXISTS company;
```

### 2️⃣ Use a Database
```sql
USE company;
```

### 3️⃣ Delete a Database
```sql
DROP DATABASE IF EXISTS company;
```

### 4️⃣ Show Databases
```sql
SHOW DATABASES;
```

### 5️⃣ Show Tables
```sql
SHOW TABLES;
```

---

## 🔍 DQL — Data Query Language

### Fetch Data(Select)
```sql
SELECT * FROM employee;  -- Fetch all columns
SELECT name, salary FROM employee;  -- Fetch specific columns
```

### Using the DUAL Table
- we can use "SELECT" without useing "FORM" with the help of dual table
```sql
SELECT 55 + 1;
SELECT NOW();  -- Current server time
SELECT UCASE('mayank');  -- Convert to uppercase
```

---

### Filter Data — `WHERE`
```sql
SELECT * FROM worker WHERE salary > 1000;
```

#### Using Operators
- `BETWEEN a AND b` → includes both endpoints  
- `IN()` → multiple OR conditions  
- `NOT` → negates a condition  
- `IS NULL` → checks for NULL values

```sql

SELECT * FROM Worker WHERE Salary BETWEEN 1000 AND 2000;
SELECT * FROM Worker WHERE NOT City = 'Delhi';
SELECT * FROM Worker WHERE Bonus IS NULL;
SELECT * FROM worker WHERE department IN ('HR', 'Admin');
SELECT * FROM worker WHERE department NOT IN ('Finance', 'IT');
SELECT * FROM worker WHERE salary IS NOT NULL;
```

---

### 🪄 Wildcards — `LIKE`
```sql
SELECT * FROM worker WHERE name LIKE '%i%';   -- contains 'i'
SELECT * FROM worker WHERE name LIKE '_i%';   -- 'i' is second letter
```
🔸 Case-insensitive by default.

---

### 🧭 Sorting — `ORDER BY`
```sql
SELECT * FROM worker ORDER BY salary;         -- Ascending
SELECT * FROM worker ORDER BY salary DESC;    -- Descending
```

---

### 🧬 Distinct Records
```sql
SELECT DISTINCT department FROM worker;
```
If two rows are completely identical, only one appears in results.

---

### 📊 Grouping Data — `GROUP BY`
```sql
SELECT department, COUNT(*) FROM worker GROUP BY department;
SELECT department, AVG(salary) FROM worker GROUP BY department;
```
Aggregate functions: `SUM()`, `AVG()`, `MIN()`, `MAX()`, `COUNT()`

---

### 🔎 Filtering Groups — `HAVING`
```sql
SELECT department, COUNT(*) 
FROM worker 
GROUP BY department 
HAVING COUNT(*) > 2;
```

### CONCAT — 
- use to represent the column in the combine column with alias name assigned by the 'as'
```sql

SELECT CONCAT(FirstName, ' ', LastName) AS FullName FROM Students;

```

### node:-
- LIMIT num  --> it will give the defined number of tuple form the database.

#### 🧩 WHERE vs HAVING
| Clause | Works On | Used With |
|--------|-----------|------------|
| `WHERE` | Rows | `SELECT`, `UPDATE`, `DELETE` |
| `HAVING` | Groups | `SELECT` with `GROUP BY` |

---

## 🔐 Constraints (DDL Level)

### Primary Key
```sql
CREATE TABLE account (
  id INT PRIMARY KEY,
  name VARCHAR(255)
);
```

or

```sql
PRIMARY KEY(id)
```

---

### Foreign Key
```sql
CREATE TABLE orders (
  id INT PRIMARY KEY,
  delivery DATE,
  cust_id INT,
  FOREIGN KEY (cust_id) REFERENCES customer(id)
);
```

---

### Unique Constraint
```sql
CREATE TABLE customer (
  name VARCHAR(255) UNIQUE
);
```

---

### NOT NULL & DEFAULT
```sql
CREATE TABLE customer (
  money INT NOT NULL DEFAULT 0
);
```

---

### CHECK Constraint
```sql
CREATE TABLE customer (


  age INT,
  CONSTRAINT check_age CHECK(age > 12)

// other way
age INT CHECK (age> 18),
);



```

---

## ⚙️ ALTER TABLE Operations

| Operation | Example |
|------------|----------|
| **Add Column** | `ALTER TABLE account ADD interest FLOAT NOT NULL DEFAULT 0;` |
| **Modify Column** | `ALTER TABLE account MODIFY interest DOUBLE;` |
| **Rename Column** | `ALTER TABLE account CHANGE COLUMN interest saving_interest FLOAT;` |
| **Drop Column** | `ALTER TABLE account DROP COLUMN saving_interest;` |
| **Rename Table** | `ALTER TABLE account RENAME TO account_details;` |

### note-->imp
- **delete -->** it is use to dalete the rows of the table according the given condition.
- **drop -->** it is use to delete the databases and tables with there structure.
- **turncate -->** it is use to empty the table but the structure of the table remain same.

---

## ✍️ DML — Data Manipulation Language

### Insert Data
```sql
INSERT INTO customer VALUES (1, 'Mayank', 'Agra');
```

Multiple Rows:
```sql
INSERT INTO customer (id, name, city)
VALUES (1, 'Mayank', 'Agra'),
       (2, 'Raj', 'Delhi'),
       (3, 'Simran', 'Mumbai');
```

Partial Columns:
```sql
INSERT INTO customer (name, city) VALUES ('Amit', 'Jaipur');
```

---

### Update Data
```sql
UPDATE customer SET address = 'Agra', gender = 'M' WHERE id = 123;
```

Update All Rows (unsafe mode):
```sql
SET SQL_SAFE_UPDATES = 0;
UPDATE customer SET city = 'Unknown';
```

---

### Delete Data(it is use to delete the data 
```sql
DELETE FROM customer WHERE id = 1;
```

Delete All Rows:
```sql
SET SQL_SAFE_UPDATES = 0;
DELETE FROM customer;
```

🧩 **Foreign Key Handling**
- `ON DELETE CASCADE` → delete dependent rows automatically  
- `ON DELETE SET NULL` → set foreign key to NULL on deletion
- `ON UPDATE CASCADE` → update the dependent rows automatically

---

### Replace Command
```sql
REPLACE INTO customer (id, name) VALUES (1, 'Mayank');
REPLACE INTO customer SET id = 1300, name = 'Mayank';
```

| Situation | Behavior |
|------------|-----------|
| Row Exists | Replaces the row |
| Row Missing | Inserts new row |

🆚 **Replace vs Update**
- `REPLACE` inserts new data if not found  
- `UPDATE` does nothing if row not found

---

## 🔗 SQL Joins

| Join Type | Description |
|------------|-------------|
| **INNER JOIN** | Returns rows with matching values in both tables |
| **LEFT JOIN** | Returns all rows from left table + matched rows from right |
| **RIGHT JOIN** | Returns all rows from right table + matched rows from left |
| **FULL JOIN** | Union of left and right join results |
| **CROSS JOIN** | Cartesian product of both tables |
| **SELF JOIN** | A table joins with itself |

---

### Inner Join Example
```sql
SELECT c.*, o.*
FROM customer AS c
INNER JOIN orders AS o
ON c.id = o.cust_id;
```

---

### Left Join Example
```sql
SELECT c.*, o.*
FROM customer AS c
LEFT JOIN orders AS o
ON c.id = o.cust_id;
```

---

### Right Join Example
```sql
SELECT c.*, o.*
FROM customer AS c
RIGHT JOIN orders AS o
ON c.id = o.cust_id;
```

---

### Full Join Example
```sql
SELECT c.*, o.* 
FROM customer AS c LEFT JOIN orders AS o ON c.id = o.cust_id
UNION
SELECT c.*, o.* 
FROM customer AS c RIGHT JOIN orders AS o ON c.id = o.cust_id;
```

---

### Cross Join Example
```sql
SELECT * FROM customer CROSS JOIN orders;
```

---

### Self Join Example
```sql
SELECT e1.id, e2.name
FROM employee AS e1
INNER JOIN employee AS e2
ON e1.manager_id = e2.id;
```

---

### Alternative Join Without `JOIN` Keyword
```sql
SELECT * 
FROM customer c, orders o 
WHERE c.id = o.cust_id;
```


---

## ✅ Summary

- SQL is used for managing and querying relational databases.
- Key operations include:
  - **DDL** → Define structure  
  - **DML** → Modify data  
  - **DQL** → Query data  
  - **DCL** → Manage permissions  
  - **TCL** → Handle transactions
- Includes constraints, joins, grouping, and filtering mechanisms for data efficiency.

---


### Union
- it is use d to combine the result set of two or more selected statements gives unique records.
- **union all** it will also give duplicate.
  
#### condition to use:-
- every table should have same number of column
- columns must similar data types
- it should we in same order

---

### sql sub queries
- a inner or nested query within another sql query.
- it involves two statements

**there is a three ways to right the sub-query**
- inside Select
- inside from
- inside where clause


**example of sub-query inside where**  
```sql

select colname form table_name where condition (subquery);

```




# Database Management System (DBMS) Notes

## 1. Functional Dependencies (FD)

Functional Dependency is the mathematical representation of the relationship between attributes in a relation (table). It describes how one attribute determines the value of another.

**Definition:**
If we are given the value of attribute **'A'**, and attribute **'B'** depends on it, we can uniquely determine the value of 'B'.

* **Notation:** `A -> B`
* **A (Determinant):** The attribute that identifies the other.
* **B (Dependent):** The attribute that is determined by A.



[Image of functional dependency diagram example]


### Types of Dependencies

#### 1. Trivial Functional Dependency
A dependency `A -> B` is **trivial** if `B` is a subset of `A`.
* *Example:* If `A = {Student_ID, Name}` and `B = {Name}`, then `A -> B` is trivial because `Name` is already inside `A`.

#### 2. Non-Trivial Functional Dependency
A dependency `A -> B` is **non-trivial** if `B` is **not** a subset of `A`.
* *Strictly Non-Trivial:* If the intersection of A and B is NULL (they share no common attributes).
* *Example:* `Student_ID -> Name` (Name is not part of Student_ID).

---

## 2. Armstrong's Axioms (Rules of FD)

These are the fundamental inference rules used to derive new functional dependencies.

1.  **Reflexivity:** If `Y` is a subset of `X`, then `X -> Y`.
2.  **Augmentation:** If `X -> Y`, then `XZ -> YZ` (adding the same attribute to both sides doesn't change the dependency).
3.  **Transitivity:** If `A -> B` and `B -> C`, then `A -> C`.

---

## 3. Database Anomalies

Anomalies are problems caused by **data redundancy** (repetition of data) in an un-normalized database. We normalize tables to fix these three specific issues:

1.  **Insertion Anomaly:**
    * The inability to add data to the database because some data is missing.
    * *Example:* You cannot add a new "Course" if there is no "Student" enrolled in it yet (if Student_ID is the primary key).

2.  **Deletion Anomaly:**
    * The unintended loss of important data when deleting other data.
    * *Example:* If a student drops a class and you delete the student's row, you might accidentally delete the only record of that class description.

3.  **Update (Updation) Anomaly:**
    * A situation where updating a single data value requires updating multiple rows. If one row is missed, the data becomes inconsistent.
    * *Example:* If a professor's phone number changes, and they teach 10 classes, you must update all 10 rows.

> **Note:** As the size of the database increases, these anomalies become harder to manage. Normalization helps us avoid this.

---

## 4. Normalization

**Goal:** Decompose a large table into multiple smaller tables to reduce redundancy until the database satisfies the **Single Responsibility Principle** (each table deals with one entity).



### 1st Normal Form (1NF)
**Rules:**
* Every column (attribute) must have an **atomic** (indivisible) value.
* No multi-valued attributes.
* Each record needs to be unique.

**Example (Violation of 1NF):**
| ID | Name | Courses |
| :--- | :--- | :--- |
| 101 | John | Math, Science |

**Example (Converted to 1NF):**
| ID | Name | Course |
| :--- | :--- | :--- |
| 101 | John | Math |
| 101 | John | Science |

---

### 2nd Normal Form (2NF)
**Rules:**
* Must be in **1NF**.
* **No Partial Dependency:** All non-prime attributes must be fully dependent on the *entire* Primary Key.
    * *Partial Dependency Definition:* When a non-prime attribute depends on only a *part* of a composite Primary Key.

**Example (Violation of 2NF):**
*Primary Key is {Student_ID, Course_ID}*

| Student_ID | Course_ID | Student_Name | Grade |
| :--- | :--- | :--- | :--- |
| 1 | C1 | Mayank | A |

* *Problem:* `Student_Name` depends only on `Student_ID`, not on `Course_ID`. This is a partial dependency.
* *Fix:* Split into two tables: one for Student details, one for Grades.

---

### 3rd Normal Form (3NF)
**Rules:**
* Must be in **2NF**.
* **No Transitive Dependency:** Non-prime attributes should not depend on other non-prime attributes.
    * *Formula:* For `A -> B`, `A` must be a Super Key **OR** `B` must be a Prime Attribute.

**Example (Violation of 3NF):**
| Emp_ID | Zip_Code | City |
| :--- | :--- | :--- |
| 101 | 144411 | Phagwara |

* *Dependency:* `Emp_ID -> Zip_Code` and `Zip_Code -> City`.
* *Problem:* `City` depends on `Zip_Code`, and `Zip_Code` is not a primary key. This is transitivity (`Emp_ID -> City` via `Zip_Code`).

---

### Boyce-Codd Normal Form (BCNF)
Also known as "3.5NF," it is a stricter version of 3NF.

**Rules:**
* Must be in **3NF**.
* For every functional dependency `X -> Y`, **X must be a Super Key**.
* *Simplified:* A non-prime attribute cannot determine a prime attribute.

**Difference from 3NF:**
BCNF handles cases where a table is in 3NF but still has redundancy because a Prime Attribute depends on a Non-Prime Attribute.

---

## 5. Advantages of Normalization

1.  **Minimizes Data Redundancy:** Reduces storage space by removing duplicate data.
2.  **Organized Database:** Ensures data is logically stored.
3.  **Data Consistency:** Changes in data need to be made in only one place, preventing anomalies.
4.  **Improved Query Performance:** (In some cases) Smaller, leaner tables can be faster to scan (though joining them requires optimization).



| Normal Form | Requirement | Catchphrase / Memory Aid |
| :--- | :--- | :--- |
| **1NF** | Atomic values only (no lists in cells). | **"Make it Flat"** |
| **2NF** | Must be 1NF + **No Partial Dependency**. | **"The Whole Key"** (Non-keys depend on the full Primary Key). |
| **3NF** | Must be 2NF + **No Transitive Dependency**. | **"Nothing But the Key"** (Non-keys shouldn't depend on other non-keys). |
| **BCNF** | Must be 3NF + LHS of every FD is a **Super Key**. | **"Strictly the Key"** (Even stricter than 3NF). |
