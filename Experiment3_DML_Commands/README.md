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

Write a SQL statement to Display the order number, orderdate and the purchase amount of orders table which will be delivered by the salesman with ID 5001.

```
SELECT order_no,order_date,purch_amt FROM orders
WHERE salesman_id = 5001;

```

**Output:**

<img width="700" height="348" alt="638865278-f348945b-abd7-46a6-ac72-fc461d96e132" src="https://github.com/user-attachments/assets/2c6d67c1-65b4-401b-b4d6-56f69f9a3ff2" />




**Question 2**

Write a SQL query to retrieve the details of all customers whose ID belongs to any of the values 3007, 3008 or 3009. Return customer_id, cust_name, city, grade, and salesman_id.


```
SELECT customer_id,cust_name,city,grade,salesman_id
FROM customer
WHERE customer_id IN (3007,3008,3009);
```

**Output:**

<img width="1164" height="331" alt="638865726-a4ce9b21-4185-4ead-bd84-274bd6128c8b" src="https://github.com/user-attachments/assets/e4421068-9826-4204-b7f9-8357e927033d" />




**Question 3**

Write a SQL query to Delete customers from 'customer' table where 'CUST_NAME' has exactly 6 characters.

```
DELETE FROM customer
WHERE LENGTH(CUST_NAME) = 6;
```

**Output:**

<img width="1823" height="434" alt="638866359-32f5baf5-e102-46e9-92e0-853e67f61c7f" src="https://github.com/user-attachments/assets/145f40d8-c359-4fcf-b03c-e99e18a28a5f" />




**Question 4**


Write a SQL query to locate the details of customers with grade values above 100. Return customer_id, cust_name, city, grade, and salesman_id.

```
SELECT customer_id,cust_name,city,grade,salesman_id
FROM customer
WHERE grade > 100;
```

**Output:**


<img width="1041" height="330" alt="638866807-dfc150c2-aa4e-4fa3-99d1-79fb8789ff3a" src="https://github.com/user-attachments/assets/d7d9e821-ad5a-4851-a253-0ecc901e5db7" />



**Question 5**


Write a SQL query to find all employees who were hired in the last 6 months from the emp table.


```

SELECT * FROM emp
WHERE hiredate >= '2024-03-01' AND hiredate <= '2024-09-01';
```

**Output:**

<img width="1236" height="219" alt="638867257-6996d154-559f-440f-b18a-b1feb30d68f9" src="https://github.com/user-attachments/assets/85c215e4-9f7d-478e-be79-449441ec286c" />



**Question 6**


Write a SQL statement to Update the grade of all customers in Chennai city as 5.

```
UPDATE customer
SET grade = 5
WHERE city = 'Chennai';

```

**Output:**

<img width="1273" height="333" alt="638867772-678d4666-e40a-4fc3-9716-7a5467cf0efb" src="https://github.com/user-attachments/assets/821ca31f-e4b2-413c-9007-70f9ca8e4f48" />




**Question 7**

Write a SQL statement to Increase quantity of all products by 10% to adjust for surplus stock counted.

```
UPDATE Products
SET quantity = quantity * 1.10;

```

**Output:**

<img width="1810" height="499" alt="638868342-a3fc56ec-d478-40a7-82fe-7ef7136ed71d" src="https://github.com/user-attachments/assets/509432b5-869d-46a9-9f27-be1f3f1c71bb" />



**Question 8**


Write a SQL query to Delete customers from 'customer' table where 'CUST_COUNTRY' is neither 'India' nor 'USA'.


```
DELETE FROM customer
WHERE CUST_COUNTRY NOT IN ('India','USA');

```

**Output:**


<img width="1836" height="325" alt="638868972-e7265e58-9748-4a54-8b58-38b5def3b312" src="https://github.com/user-attachments/assets/713c6b55-7de2-4e3e-be68-25b04ef18aa3" />




**Question 9**

Write a SQL statement to double the availability of the product with product_id 1.

```
UPDATE products
SET availability = availability * 2
WHERE product_id = 1;
```

**Output:**


<img width="1058" height="169" alt="638869348-490ac362-f3df-43d6-af59-95222336ffb3" src="https://github.com/user-attachments/assets/f16bfe22-63a5-4c27-b99f-4c54bca46e72" />



**Question 10**

Write a SQL query to calculate the original price using the discount percentage and the given discounted price. Return product_id, discounted_price, discount_percentage, and original_price.


```
SELECT product_id,discounted_price,discount_percentage,(discounted_price / (1-discount_percentage)) AS original_price
FROM Products;

```

**Output:**


<img width="1121" height="214" alt="638869755-37e0d3dc-28a5-46af-9aca-ea00ee0a6c2b" src="https://github.com/user-attachments/assets/5d3ba360-d761-49fd-9291-f35b079c4469" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
