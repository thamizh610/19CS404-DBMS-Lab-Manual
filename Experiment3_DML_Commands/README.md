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
Write a SQL statement to Increase the selling price per unit by 5% for product ID 15 who's sale is on '2023-01-31'.

sales(sale_id,sale_date,product_id,quantity,sell_price,total_sell_price)

```
UPDATE sales
SET sell_price = sell_price * 1.05
WHERE product_id = 15
  AND sale_date = '2023-01-31';
```
**Output:**
<img width="1271" height="344" alt="image" src="https://github.com/user-attachments/assets/30eed76e-e0fa-489c-8d5f-1d9c926caec9" />


**Question 2**
---
Increase the reorder level by 30% for products from 'Food' category having quantity in stock less than 50% of existing reorder level in the products table
name               type
--------------  ----------
product_id         INT
product_name       VARCHAR(10)
category           VARCHAR(50)
cost_price         DECIMAL(10)
sell_price         DECIMAL(10)
reorder_lvl        INT
quantity              INT
supplier_id           INT
```
UPDATE products
SET reorder_lvl = CAST(reorder_lvl * 1.3 AS INT)
WHERE category = 'Food'
  AND quantity < (reorder_lvl * 0.5);
```

**Output:**
<img width="1273" height="303" alt="image" src="https://github.com/user-attachments/assets/14df4ae9-ffd1-4539-ac77-fbba18587581" />


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

```
UPDATE Products
SET sell_price = CAST(cost_price * 1.35 AS INT)
WHERE ((sell_price - cost_price) / sell_price) < 0.30;
```

**Output:**
<img width="1272" height="371" alt="image" src="https://github.com/user-attachments/assets/9f14b6be-8d66-4b04-acef-178c3c31014d" />

**Question 4**
---
Write a SQL query to delete a specific doctor from Doctors table whose ID is 1.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```
DELETE FROM Doctors
WHERE doctor_id = 1;
```

**Output:**
<img width="1030" height="175" alt="image" src="https://github.com/user-attachments/assets/e896efdb-6514-4f2c-81af-1e391e5ac984" />

**Question 5**
---
Write a SQL query to delete a doctor from Doctors table whos specialization is 'Cardiology'

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization

```
DELETE FROM Doctors
WHERE specialization = 'Cardiology';
```

**Output:**
<img width="948" height="265" alt="image" src="https://github.com/user-attachments/assets/3a371bff-00ad-45d6-a99f-04eb19148746" />

**Question 6**
---
Write a SQL statement to Find the salesmen with all information who gets the commission within a range of 0.12 and 0.14.

salesman table

cid         name         type        notnull     dflt_value  pk
----------  -----------  ----------  ----------  ----------  ----------
0           salesman_id  numeric(5)    0                       1
1           name         varchar(30)   0                       0
2           city         varchar(15)   0                       0
3           commission   decimal(5,2)  0                       0

```
SELECT *
FROM salesman
WHERE commission BETWEEN 0.12 AND 0.14;
```

**Output:**
<img width="744" height="350" alt="image" src="https://github.com/user-attachments/assets/510b77c1-2ec9-4e05-a4dd-fd61fbd470b4" />


**Question 7**
---
Write a query to find all the employees whose salary is between 50000 to 100000 from employeeposition table.

EmpID

EmpPosition

DateOfJoining

Salary

1

Manager

01/05/2024

500000

2

Executive

02/05/2024

75000

```
SELECT *
FROM employeeposition
WHERE Salary BETWEEN 50000 AND 100000;
```

**Output:**
<img width="803" height="204" alt="image" src="https://github.com/user-attachments/assets/fa6033c5-99e2-4163-85a6-620c5f707da0" />


**Question 8**
---
Write a SQL query to find customers who are either from the city 'New York' or who have a grade greater than 200. Return customer_id, cust_name, city, grade, and salesman_id.

Sample table: customer

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002

```
SELECT customer_id, cust_name, city, grade, salesman_id
FROM customer
WHERE city = 'New York'
   OR grade > 200;
```

**Output:**
<img width="1087" height="192" alt="image" src="https://github.com/user-attachments/assets/e6639454-ca6b-490d-8083-44230c6e2426" />


**Question 9**
---
Write a SQL query to calculate the final price after applying both the discount and the tax. Return product_id, original_price, discount_percentage, tax_rate, and final_price.

Sample table: Products

product_id | original_price | discount_percentage | tax_rate

 ------------+----------------+---------------------+--------- 

101 | 50.00 | 0.10 | 0.08 

102 | 75.00 | 0.15 | 0.05 

103 | 100.00 | 0.20 | 0.10
```
SELECT 
    product_id,
    original_price,
    discount_percentage,
    tax_rate,
    (original_price * (1 - discount_percentage) * (1 + tax_rate)) AS final_price
FROM Products;
```

**Output:**
<img width="957" height="316" alt="image" src="https://github.com/user-attachments/assets/1dc3d06d-58a6-49ce-94ac-60e20372a64b" />

**Question 10**
---
Find Products with a Discounted Price Greater than a Given Amount:

Write a query to list all products that have a discounted price greater than $100. Return product_id, original_price, discount_percentage, and discounted_price.

Sample table: Products

product_id | original_price | discount_percentage

-----------------------------------------------------------

"101" "50" "0.1"

"102" "150" "0.15"

"103" "200" "0.2"

"104" "300" "0.25"

```
SELECT 
    product_id,
    original_price,
    discount_percentage,
    (original_price * (1 - discount_percentage)) AS discounted_price
FROM Products
WHERE (original_price * (1 - discount_percentage)) > 100;
```

**Output:**
<img width="991" height="193" alt="image" src="https://github.com/user-attachments/assets/e1a60c6b-76b0-4a33-a62d-b8742b3ad33d" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
