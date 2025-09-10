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
   - Identified by the primary key.  
   - Example: Customer–Order.  
2. **Weak Relationship**  
   - Cannot be uniquely identified by only a primary key.  
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
- Involves **abstraction** where a relationship is treated as a **higher-level entity set** (abstract entity).  

✅ Example:  
- If `Employee` works on a `Project`, and `Manager` manages that relationship, then "works_on" can be aggregated into a higher-level entity.  

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
