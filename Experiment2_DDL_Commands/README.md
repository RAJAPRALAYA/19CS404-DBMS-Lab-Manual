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
<img width="992" height="349" alt="image" src="https://github.com/user-attachments/assets/7757da0c-7cb4-4e95-89e7-2a6c578a99ed" />


```sql
INSERT INTO Employee (EmployeeID, Name, Position)
VALUES (4, 'Emily White', 'Analyst');
```

**Output:**

<img width="1255" height="363" alt="image" src="https://github.com/user-attachments/assets/16c047b9-b519-4b98-9454-b1bebb947548" />


**Question 2**
---
<img width="925" height="415" alt="image" src="https://github.com/user-attachments/assets/82d83669-b376-4db6-b84d-6608fd83439b" />


```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id)
    REFERENCES company(com_id)
    ON UPDATE SET NULL
    ON DELETE SET NULL
);
```

**Output:**

<img width="1253" height="375" alt="image" src="https://github.com/user-attachments/assets/f151c284-f5ee-4aa4-9d73-4c9b4fc8ad0f" />


**Question 3**
---
<img width="864" height="333" alt="image" src="https://github.com/user-attachments/assets/3929f6a1-846d-4c7a-804c-651d873e33b0" />


```sql
INSERT INTO Customers (CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```

**Output:**

<img width="1262" height="315" alt="image" src="https://github.com/user-attachments/assets/c88a0aa0-f1e3-4115-b472-58fbca5945e8" />


**Question 4**
---
<img width="1036" height="320" alt="image" src="https://github.com/user-attachments/assets/66d4b040-6ef1-4cae-8ec6-7099862b9e5a" />


```sql
CREATE TABLE Departments (
    DepartmentID INTEGER,
    DepartmentName TEXT
);
```

**Output:**

<img width="1270" height="374" alt="image" src="https://github.com/user-attachments/assets/e05130d9-8d2a-49e0-96e4-2826b513324f" />


**Question 5**
---
<img width="1261" height="459" alt="image" src="https://github.com/user-attachments/assets/03e60b88-b04b-4639-9e1b-f0a27e511090" />


```sql
ALTER TABLE Companies
ADD designation varchar(50);
ALTER TABLE Companies
ADD net_salary number;
```

**Output:**

<img width="1257" height="422" alt="image" src="https://github.com/user-attachments/assets/58b847d6-84e5-4f3b-a488-2ecee1e4b47e" />


**Question 6**
---
<img width="932" height="364" alt="image" src="https://github.com/user-attachments/assets/c75dade6-260a-483b-966a-e0bd8fc762cb" />


```sql
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES
(2, 'John Smith', 'Developer', 'IT', 75000),
(3, 'Anna Bell', 'Designer', 'Marketing', 68000);
```

**Output:**

<img width="1263" height="400" alt="image" src="https://github.com/user-attachments/assets/279de2fe-a9f7-4944-9bfd-521e03d90b63" />


**Question 7**
---
<img width="1251" height="375" alt="image" src="https://github.com/user-attachments/assets/720c2ea6-c96d-4fdf-a4da-24e09839dfff" />


```sql
CREATE TABLE Attendance (
    AttendanceID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    AttendanceDate DATE,
    Status TEXT CHECK (Status IN ('Present', 'Absent', 'Leave')),
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1257" height="324" alt="image" src="https://github.com/user-attachments/assets/552efea9-c462-4b42-9f9c-60ed1cd06325" />


**Question 8**
---
<img width="1246" height="402" alt="image" src="https://github.com/user-attachments/assets/3d37add6-edb3-46cc-8877-abffbd2e4c98" />


```sql
CREATE TABLE Bonuses (
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK (BonusAmount > 0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1263" height="336" alt="image" src="https://github.com/user-attachments/assets/d97eb9eb-f6b6-4322-af6b-cba3eb8b2426" />


**Question 9**
---
<img width="1023" height="436" alt="image" src="https://github.com/user-attachments/assets/a553998d-fea2-4d9a-a03e-22e054bd224b" />


```sql
ALTER TABLE books
ADD ISBN varchar(30);

ALTER TABLE books
ADD domain_dept varchar(30);
```

**Output:**

<img width="1251" height="415" alt="image" src="https://github.com/user-attachments/assets/99e1dad0-801b-4c4b-9013-72215580df06" />


**Question 10**
---
<img width="1247" height="403" alt="image" src="https://github.com/user-attachments/assets/8010d892-678f-4e4c-9f74-1c4c0bb5fee6" />


```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    Amount REAL CHECK (Amount > 0),
    DueDate DATE CHECK (DueDate > InvoiceDate),
    OrderID INTEGER,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1249" height="338" alt="image" src="https://github.com/user-attachments/assets/00bcb5e5-183c-4cb5-9fc5-64606793a61c" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
