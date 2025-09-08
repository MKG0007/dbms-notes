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
- **Note**: Structure at the **physical level** affects the structure at the **logical level**.  

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
