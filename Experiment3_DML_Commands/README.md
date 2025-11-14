# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
<img width="1290" height="310" alt="image" src="https://github.com/user-attachments/assets/6531a12f-bd81-4c94-a062-74ebd1c4ee3b" />

```sql
SELECT c.cust_name
FROM customer c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.purch_amt < 100;
```

**Output:**

<img width="661" height="375" alt="image" src="https://github.com/user-attachments/assets/66b66479-1593-4a70-9943-745b3ef64f8a" />


**Question 2**
---
SQL statement to generate a report with customer name, city, order number, order date, order amount, salesperson name, and commission to determine if any of the existing customers have not placed orders or if they have placed orders through their salesman or by themselves.

Sample table: customer

| customer_id | cust_name      | city       | grade | salesman_id |
| ----------- | -------------- | ---------- | ----- | ----------- |
| 3002        | Nick Rimando   | New York   | 100   | 5001        |
| 3007        | Brad Davis     | New York   | 200   | 5001        |
| 3005        | Graham Zusi    | California | 200   | 5002        |
| 3008        | Julian Green   | London     | 300   | 5002        |
| 3004        | Fabian Johnson | Paris      | 300   | 5006        |
| 3009        | Geoff Cameron  | Berlin     | 100   | 5003        |
| 3003        | Jozy Altidor   | Moscow     | 200   | 5007        |
| 3001        | Brad Guzan     | London     |       | 5005        |

Sample table: orders

| ord_no | purch_amt | ord_date   | customer_id | salesman_id |
| ------ | --------- | ---------- | ----------- | ----------- |
| 70001  | 150.50    | 2012-10-05 | 3005        | 5002        |
| 70009  | 270.65    | 2012-09-10 | 3001        | 5005        |
| 70002  | 65.26     | 2012-10-05 | 3002        | 5001        |
| 70004  | 110.50    | 2012-08-17 | 3009        | 5003        |
| 70007  | 948.50    | 2012-09-10 | 3005        | 5002        |
| 70005  | 2400.60   | 2012-07-27 | 3007        | 5001        |
| 70008  | 5760.00   | 2012-09-10 | 3002        | 5001        |
| 70010  | 1983.43   | 2012-10-10 | 3004        | 5006        |
| 70003  | 2480.40   | 2012-10-10 | 3009        | 5003        |
| 70012  | 250.45    | 2012-06-27 | 3008        | 5002        |
| 70011  | 75.29     | 2012-08-17 | 3003        | 5007        |
| 70013  | 3045.60   | 2012-04-25 | 3002        | 5001        |

Sample table: salesman

| salesman_id | name       | city     | commission |
| ----------- | ---------- | -------- | ---------- |
| 5001        | James Hoog | New York | 0.15       |
| 5002        | Nail Knite | Paris    | 0.13       |
| 5005        | Pit Alex   | London   | 0.11       |
| 5006        | Mc Lyon    | Paris    | 0.14       |
| 5007        | Paul Adam  | Rome     | 0.13       |
| 5003        | Lauson Hen | San Jose | 0.12       |

For example:

<img width="775" height="335" alt="image" src="https://github.com/user-attachments/assets/5c53cfc2-7fe5-4cc3-89c1-7b55b892525e" />


```sql
SELECT
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt       AS 'Order Amount',
    s.name            AS name,
    s.commission
FROM
    customer c
LEFT JOIN
    orders o
    ON c.customer_id = o.customer_id
LEFT JOIN
    salesman s
    ON o.salesman_id = s.salesman_id```

**Output:**

<img width="1331" height="765" alt="image" src="https://github.com/user-attachments/assets/436d908f-f4ab-47ca-96de-93637eecdb8f" />

**Question 3**
---
<img width="1076" height="657" alt="image" src="https://github.com/user-attachments/assets/373287f1-6e75-4fa7-bed3-aacf0ec4dfcb" />


```sql
SELECT 
    c.cust_name,
    c.city AS city,
    c.grade,
    s.name AS Salesman,
    s.city AS city
FROM 
    customer c
JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
ORDER BY 
    c.customer_id ASC;

```

**Output:**

<img width="1041" height="602" alt="image" src="https://github.com/user-attachments/assets/33b7b23c-9fe3-4135-bc66-0266df6137a7" />

**Question 4**
---
<img width="1320" height="462" alt="image" src="https://github.com/user-attachments/assets/e37e2851-595d-49d4-8925-8f72a017c2dd" />


```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    appointments a
ON 
    p.patient_id = a.patient_id
WHERE 
    a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';
```

**Output:**

<img width="1335" height="222" alt="image" src="https://github.com/user-attachments/assets/4b0c04b2-d4a3-475b-9f14-ca8bfade9d54" />

**Question 5**
---
<img width="1350" height="792" alt="image" src="https://github.com/user-attachments/assets/b3a70d4f-6987-47fe-a5b4-c7beb31d5702" />


```sql
SELECT
    c.cust_name,
    c.city,
    o.ord_no,
    o.ord_date,
    o.purch_amt AS 'Order Amount'
FROM
    customer c
LEFT JOIN
    orders o
ON
    c.customer_id = o.customer_id
ORDER BY
    o.ord_date ASC;```

**Output:**

<img width="1062" height="760" alt="image" src="https://github.com/user-attachments/assets/72093fc7-338e-4e37-9fae-621d47b66410" />

**Question 6**
---
<img width="1311" height="455" alt="image" src="https://github.com/user-attachments/assets/fe955111-be9e-4cec-963a-58e7844b42ca" />

```sql
SELECT
    p.*
FROM
    patients p
INNER JOIN
    appointments a
ON
    p.patient_id = a.patient_id
WHERE
    a.appointment_date BETWEEN '2024-02-01' AND '2024-02-28';
```

**Output:**

<img width="1330" height="223" alt="image" src="https://github.com/user-attachments/assets/14283785-968e-4cd2-8d87-378e4438d31e" />

**Question 7**
---
<img width="1061" height="744" alt="image" src="https://github.com/user-attachments/assets/933a4ea0-3567-4d00-ab37-cf2a7636a867" />
<img width="951" height="349" alt="image" src="https://github.com/user-attachments/assets/f9e847d3-f229-4e68-ba4b-123ced174563" />


```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM
    orders o
INNER JOIN
    customer c
ON
    o.customer_id = c.customer_id
INNER JOIN
    salesman s
ON
    o.salesman_id = s.salesman_id;```

**Output:**

<img width="1337" height="766" alt="image" src="https://github.com/user-attachments/assets/d7860668-58d6-43c2-8775-1e92c9c0f9b6" />


**Question 8**
---
<img width="935" height="649" alt="image" src="https://github.com/user-attachments/assets/9c9c3ee7-ca14-4edc-9f62-4a2a8566dfd5" />

```sql
SELECT
    o.ord_no,
    o.purch_amt,
    c.cust_name,
    c.city
FROM
    orders o
INNER JOIN
    customer c
ON
    o.customer_id = c.customer_id
WHERE
    o.purch_amt BETWEEN 500 AND 2000;
```

**Output:**

<img width="891" height="278" alt="image" src="https://github.com/user-attachments/assets/a338cc29-48aa-4cbb-87bc-48c3996bd5a4" />

**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "patients" table (aliased as "p"), with an inner join on the "patient_id" column and conditions filtering for test results with the test names 'Blood Test' or 'Blood Pressure' and results not containing the substring 'Normal'.

PATIENTS TABLE:

ATTRIBUTES - patient_id, first_name, last_name, date_of_birth, admission_date, discharge_date, doctor_id

<img width="1052" height="172" alt="unnamed" src="https://github.com/user-attachments/assets/819d591c-7292-4556-8320-7b6eed138dd2" />


TEST_RESULT TABLES:

ATTRIBUTES - result_id, patient_id, test_name, result, test_date

<img width="1060" height="171" alt="unnamed" src="https://github.com/user-attachments/assets/311fdcbd-88b5-475e-b35d-00226ec0a7e1" />


```sql
SELECT 
    p.*
FROM 
    patients p
INNER JOIN 
    test_results t
ON 
    p.patient_id = t.patient_id
WHERE 
    (t.test_name = 'Blood Test' OR t.test_name = 'Blood Pressure')
    AND t.result NOT LIKE '%Normal%';

```

**Output:**

<img width="1365" height="405" alt="image" src="https://github.com/user-attachments/assets/19d7d78a-1a03-422f-8ad7-d2a8c1224433" />


**Question 10**
---
Write the SQL query that achieves the selection of all columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for salesman with the name 'Mc Lyon'.

Customer Table: (customer_id, cust_name, city, grade, salesman_id)

Salesman Table: (salesman_id, name, city, commission)

```sql
SELECT 
    c.*
FROM 
    customer c
LEFT JOIN 
    salesman s
ON 
    c.salesman_id = s.salesman_id
WHERE 
    s.name = 'Mc Lyon';

```

**Output:**

<img width="1281" height="374" alt="image" src="https://github.com/user-attachments/assets/5d98c74b-21a6-437f-a618-329cd97efe48" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
