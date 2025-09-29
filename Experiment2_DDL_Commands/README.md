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
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)
```sql
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';
```

**Output:**

<img width="1254" height="522" alt="image" src="https://github.com/user-attachments/assets/0cc9c2ca-72d3-4072-af06-34680dc3c49a" />

**Question 2**
---
Write a SQL statement to Update the address to '58 Lakeview, Magnolia' where supplier ID is 5 in the suppliers table.

Suppliers Table 

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

<img width="1239" height="494" alt="image" src="https://github.com/user-attachments/assets/ef17d03e-bb1a-4962-ae4a-370c9935d722" />


**Question 3**
---
For products with a profit % less than 30% of selling price, update the selling price to provide a profit margin of 35% over cost price of the product in the products table.

PRODUCTS TABLE

name               type
-----------------  ---------------
product_id         INT
product_name       VARCHAR(100)
category           VARCHAR(50)
cost_price         DECIMAL(10,2)
sell_price         DECIMAL(10,2)
reorder_lvl        INT
quantity           INT
supplier_id        INT

```sql
UPDATE Products
SET sell_price = CAST(cost_price * 1.35 AS INT)
WHERE ((sell_price - cost_price) / sell_price) < 0.30;
```

**Output:**

<img width="1239" height="588" alt="image" src="https://github.com/user-attachments/assets/655600eb-f206-4843-817e-34d6ce07743e" />


**Question 4**
---
Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
UPDATE Products
SET quantity = quantity * 1.10;
```

**Output:**

<img width="1239" height="688" alt="image" src="https://github.com/user-attachments/assets/b362e98c-1e43-45b9-983b-653423837b5f" />

**Question 5**
---
Write a SQL query to Delete All Doctors with a NULL Specialization

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
DELETE FROM Doctors
WHERE specialization IS NULL;
```

**Output:**
<img width="932" height="556" alt="Screenshot 2025-09-29 140249" src="https://github.com/user-attachments/assets/e9fd8459-3537-440e-b40b-2b6b2889802f" />

**Question 6**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
DELETE FROM Doctors
WHERE doctor_id = 1;
```

**Output:**


<img width="671" height="157" alt="image" src="https://github.com/user-attachments/assets/71aeec8c-ea0a-4a62-a9d2-ada61c9593ed" />

**Question 7**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```sql
DELETE FROM Doctors
WHERE specialization = 'Cardiology';
```

**Output:**

<img width="688" height="227" alt="image" src="https://github.com/user-attachments/assets/bb55cfc2-0b59-4c9e-b891-794411b9dad9" />

**Question 8**
---
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.

salesman table

cid         name         type        notnull     dflt_value  pk
----------  -----------  ----------  ----------  ----------  ----------
0           salesman_id  numeric(5)    0                       1
1           name         varchar(30)   0                       0
2           city         varchar(15)   0                       0
3           commission   decimal(5,2)  0                       0

```sql
SELECT *
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**

<img width="569" height="291" alt="image" src="https://github.com/user-attachments/assets/d8b91b63-e042-4835-92d2-fda4d6377372" />


**Question 9**
---
Write a SQL query to evaluate the status of rows in the Calculations table based on whether value1 is positive, negative, or zero.

cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           value1      REAL        0                       0
2           value2      REAL        0                       0
3           base        INTEGER     0                       0
4           exponent    INTEGER     0                       0
5           number      REAL        0                       0
6           decimal     REAL        0                       0

```sql
SELECT 
    id,
    value1,
    CASE
        WHEN value1 > 0 THEN 'Positive'
        WHEN value1 < 0 THEN 'Negative'
        ELSE 'Zero'
    END AS value_status
FROM Calculations;
```

**Output:**

<img width="478" height="287" alt="image" src="https://github.com/user-attachments/assets/a4017912-69f5-4fa1-aad3-22ed647c35da" />


**Question 10**
---
Write a SQL query to find customers who are either from the city 'New York' or who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
```sql
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'New York'
   OR grade > 200;
```

**Output:**

<img width="677" height="259" alt="image" src="https://github.com/user-attachments/assets/3e480e0a-e083-41bb-82aa-c1e7868092e5" />

RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
