# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--

  
```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE CHECK (DueDate > InvoiceDate),
    Amount REAL CHECK (Amount > 0)
    )
```

**Output:**

![Output1](output.png)

**Question 2**
---
  <img width="999" height="444" alt="image" src="https://github.com/user-attachments/assets/33444fa4-0fcc-4bce-b159-b69de63b44b8" />


```sql
CREATE TABLE Customers (
    CustomerID INTEGER,
    Name TEXT,
    Email TEXT,
    JoinDate DATETIME
)
```

**Output:**

![Output2](output.png)

**Question 3**
---
<img width="1055" height="604" alt="image" src="https://github.com/user-attachments/assets/888a3530-fe9d-4b42-b23d-aeb869376a3f" />


```sql
CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER ,
    OrderID INTEGER,
    FOREIGN KEY(SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
    );
```

**Output:**

![Output3](output.png)

**Question 4**
---
<img width="1226" height="345" alt="image" src="https://github.com/user-attachments/assets/8b54b234-23b5-44ab-909c-bf61e07f8820" />


```sql
ALTER TABLE Student_details ADD COLUMN Mobilenumber number;
```

**Output:**

![Output4](output.png)

**Question 5**
---
<img width="1039" height="363" alt="image" src="https://github.com/user-attachments/assets/3f882ed0-201f-4d94-8c56-22c6c3dffd2b" />


```sql
ALTER TABLE Student_details ADD column Date_of_birth Date;
```

**Output:**

![Output5](output.png)

**Question 6**
---
<img width="974" height="487" alt="image" src="https://github.com/user-attachments/assets/c6b20842-e2ea-4374-8a67-dc989343c567" />


```sql
INSERT INTO Books (ISBN, Title, Author) VALUES ('978-6655443321', 'Big Data Analytics', 'Karen Adams');
```

**Output:**

![Output6](output.png)

**Question 7**
---
<img width="1221" height="367" alt="image" src="https://github.com/user-attachments/assets/915530de-ea4f-4d90-b771-9407cf94e537" />


```sqlCREATE TABLE Department (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**

![Output7](output.png)

**Question 8**
---
<img width="1219" height="425" alt="image" src="https://github.com/user-attachments/assets/0cc5f15e-c4b8-404c-8c34-eacf621f3e40" />


```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate dATE,
    Amount REAL CHECK(Amount > 0),
    DueDate DATE CHECK(DueDate > InvoiceDate),
    OrderID INTEGER,
    FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
    );
```

**Output:**

![Output8](output.png)

**Question 9**
---
<img width="1210" height="498" alt="image" src="https://github.com/user-attachments/assets/c730cc5c-4c87-4815-99e4-c98d4be516f7" />


```sql
INSERT INTO Products (ProductID, Name, Category, Price, Stock) VALUES 
(106, 'Fitness Tracker', 'Wearables', NULL, NULL),
(107, 'Laptop', 'Electronics', 999.99, 50),
(108, 'Wireless Earbud', 'Accessories', NULL, 100);
```

**Output:**

![Output9](output.png)

**Question 10**
---
<img width="838" height="367" alt="image" src="https://github.com/user-attachments/assets/452b9c67-0d73-4eb5-9df5-977ccc9c5488" />


```sql
INSERT INTO Products (ProductID, ProductName, Price, Stock)

SELECT ProductID, ProductName, Price, Stock FROM Discontinued_products;
```

**Output:**
# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--

  
```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE CHECK (DueDate > InvoiceDate),
    Amount REAL CHECK (Amount > 0)
    )
```

**Output:**

<img width="1286" height="275" alt="image" src="https://github.com/user-attachments/assets/fa5c67bd-ad7a-4bd7-a6a2-6863dfc1f733" />


**Question 2**
---
  <img width="999" height="444" alt="image" src="https://github.com/user-attachments/assets/33444fa4-0fcc-4bce-b159-b69de63b44b8" />


```sql
CREATE TABLE Customers (
    CustomerID INTEGER,
    Name TEXT,
    Email TEXT,
    JoinDate DATETIME
)
```

**Output:**

<img width="1882" height="407" alt="image" src="https://github.com/user-attachments/assets/b88d0b88-70c1-4ecd-80cb-f50857f5783c" />


**Question 3**
---
<img width="1055" height="604" alt="image" src="https://github.com/user-attachments/assets/888a3530-fe9d-4b42-b23d-aeb869376a3f" />


```sql
CREATE TABLE Shipments (
    ShipmentID INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID INTEGER ,
    OrderID INTEGER,
    FOREIGN KEY(SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
    );
```

**Output:**

<img width="1299" height="243" alt="image" src="https://github.com/user-attachments/assets/9de95a74-1c88-40ad-9a2a-db4719f5bf9b" />


**Question 4**
---
<img width="1226" height="345" alt="image" src="https://github.com/user-attachments/assets/8b54b234-23b5-44ab-909c-bf61e07f8820" />


```sql
ALTER TABLE Student_details ADD COLUMN Mobilenumber number;
```

**Output:**

<img width="1299" height="337" alt="image" src="https://github.com/user-attachments/assets/435875ff-7df8-4d34-9cb0-9c81bbf43911" />


**Question 5**
---
<img width="1039" height="363" alt="image" src="https://github.com/user-attachments/assets/3f882ed0-201f-4d94-8c56-22c6c3dffd2b" />


```sql
ALTER TABLE Student_details ADD column Date_of_birth Date;
```

**Output:**

<img width="1302" height="333" alt="image" src="https://github.com/user-attachments/assets/049746af-3317-4d25-87b3-00f48020f54d" />


**Question 6**
---
<img width="974" height="487" alt="image" src="https://github.com/user-attachments/assets/c6b20842-e2ea-4374-8a67-dc989343c567" />


```sql
INSERT INTO Books (ISBN, Title, Author) VALUES ('978-6655443321', 'Big Data Analytics', 'Karen Adams');
```

**Output:**

<img width="1289" height="315" alt="image" src="https://github.com/user-attachments/assets/919a9546-10bb-4497-a18b-657a696cc731" />


**Question 7**
---
<img width="1221" height="367" alt="image" src="https://github.com/user-attachments/assets/915530de-ea4f-4d90-b771-9407cf94e537" />


```sqlCREATE TABLE Department (
    DepartmentID INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location TEXT
);
```

**Output:**

<img width="1316" height="249" alt="image" src="https://github.com/user-attachments/assets/d36cf4f6-7c4d-48f2-aa66-adb38e997c81" />


**Question 8**
---
<img width="1219" height="425" alt="image" src="https://github.com/user-attachments/assets/0cc5f15e-c4b8-404c-8c34-eacf621f3e40" />


```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate dATE,
    Amount REAL CHECK(Amount > 0),
    DueDate DATE CHECK(DueDate > InvoiceDate),
    OrderID INTEGER,
    FOREIGN KEY(OrderID) REFERENCES Orders(OrderID)
    );
```

**Output:**

<img width="1326" height="245" alt="image" src="https://github.com/user-attachments/assets/2b55c388-e6ba-40d1-8b0d-11ae9bb7db26" />


**Question 9**
---
<img width="1210" height="498" alt="image" src="https://github.com/user-attachments/assets/c730cc5c-4c87-4815-99e4-c98d4be516f7" />


```sql
INSERT INTO Products (ProductID, Name, Category, Price, Stock) VALUES 
(106, 'Fitness Tracker', 'Wearables', NULL, NULL),
(107, 'Laptop', 'Electronics', 999.99, 50),
(108, 'Wireless Earbud', 'Accessories', NULL, 100);
```

**Output:**

<img width="1275" height="281" alt="image" src="https://github.com/user-attachments/assets/c6d80a83-8b34-49f4-9c97-f1cd5b32baab" />


**Question 10**
---
<img width="838" height="367" alt="image" src="https://github.com/user-attachments/assets/452b9c67-0d73-4eb5-9df5-977ccc9c5488" />


```sql
INSERT INTO Products (ProductID, ProductName, Price, Stock)

SELECT ProductID, ProductName, Price, Stock FROM Discontinued_products;
```

**Output:**
<img width="1165" height="226" alt="image" src="https://github.com/user-attachments/assets/96a2790b-2dd0-4720-a935-163a1133bc90" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
