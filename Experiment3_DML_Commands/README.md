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
How many appointments are scheduled for each doctor?
Sample table:Appointments Table
```sql
select
     DoctorID,
     COUNT(AppointmentID) as
TotalAppointments
from
    Appointments
group by
    DoctorID
```
**Output:**
<img width="841" height="791" alt="image" src="https://github.com/user-attachments/assets/158b289b-37f1-4ece-8df9-4a958c6eaf4a" />

**Question 2**
How many medical records were created in each month?
Sample table:MedicalRecords Table
```sql
select
     strftime('%Y-%m', Date) as Month,
     COUNT(RecordID) as TotalRecords
from
   MedicalRecords
group by
   Month
order by
   Month;
```
**Output:**
<img width="824" height="618" alt="image" src="https://github.com/user-attachments/assets/beabfc68-d04c-45c5-bf47-f8818dfa87a0" />

**Question 3**
How many patients are covered by each insurance company?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT
```sql
select
     InsuranceCompany,
     COUNT(PatientID) as TotalPatients
from
     Insurance
group by
     InsuranceCompany
```
**Output:**
<img width="820" height="810" alt="image" src="https://github.com/user-attachments/assets/0bd379e8-ed8c-4a67-a50f-07a6a0f8056f" />


**Question 4**
Write a SQL query to determine the number of customers who received at least one grade for their activity.

Sample table: customer

customer_id |   cust_name    |    city    | grade | salesman_id 

-------------+----------------+------------+-------+-------------

        3002 | Nick Rimando   | New York   |   100 |        5001

        3007 | Brad Davis     | New York   |   200 |        5001

        3005 | Graham Zusi    | California |   200 |        5002

 ```sql
select COUNT(grade) as "COUNT"
from customer;
```
**Output:**
<img width="854" height="470" alt="image" src="https://github.com/user-attachments/assets/e92d441b-281a-4b0c-a142-7a31bcd26369" />

**Question 5**
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
```sql
select
     COUNT(DISTINCT city) as unique_cities
from
     customer;
```
**Output:**
<img width="836" height="465" alt="image" src="https://github.com/user-attachments/assets/0233c331-941a-47e1-b550-0233668c2ed0" />

**Question 6**
Write a SQL query to calculate the total number of working hours of all employees
Sample table: employee1
```sql
select
     sum(workhour) as "Total working hours"
from
     employee1;
```
**Output:**
<img width="807" height="461" alt="image" src="https://github.com/user-attachments/assets/e29c0881-901c-4fc9-a7f5-e5ea44295162" />


**Question 7**
Write a SQL query to Calculate the average email length (in characters) for people who lives in Mumbai city

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT   
city        TEXT
email       TEXT
phone       INTEGER
```sql
select
     avg(LENGTH(email)) as
avg_email_length_below_30
from customer
where city = 'Mumbai';
```
**Output:**

<img width="871" height="499" alt="image" src="https://github.com/user-attachments/assets/4998edc6-ab74-4ced-ad4e-d2e6efeb1743" />

**Question 8**
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the maximum work hours for each date, and excludes dates where the maximum work hour is not greater than 12.
Sample table: employee1
```sql
select
    jdate,
    MAX(workhour) AS "MAX(workhour)"
from
    employee1
group by
    jdate
having
    MAX(workhour) > 12;
```
**Output:**
<img width="827" height="547" alt="image" src="https://github.com/user-attachments/assets/63462e15-2ee5-4b60-baa0-3b3c64775e54" />

**Question 9**
Write an SQL query that groups the customer data into 5-year age intervals, calculates the minimum salary for each group, and excludes groups where the minimum salary is not less than 2000.
Table: customer1
```sql
select
    (age / 5) * 5 AS age_group,
    MIN(salary) AS "MIN(salary)"
from
    customer1
group by
    age_group
having
    min(salary) < 2000;
```
**Output:**
<img width="792" height="471" alt="image" src="https://github.com/user-attachments/assets/1d6ead21-75db-4535-84e9-32bb70af1e48" />

**Question 10**
Write the SQL query that accomplishes the grouping of data by age, calculates the total income for each age group, and includes only those age groups where the total income sum is greater than 1,000,000.
Sample table: employee
```sql
select
     age,
     SUM(income) AS "SUM(income)"
from
    employee
group by
    age
having
    sum(income) > 1000000;
```
**Output:**
<img width="838" height="595" alt="image" src="https://github.com/user-attachments/assets/601dfe2f-ee48-4323-9eb1-46adbc4960f6" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
