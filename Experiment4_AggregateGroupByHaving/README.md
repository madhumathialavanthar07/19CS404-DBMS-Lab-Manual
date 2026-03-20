# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
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
<img width="790" height="827" alt="image" src="https://github.com/user-attachments/assets/a948559d-bbd3-4eab-a44a-bc4c6f11981e" />

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
<img width="764" height="602" alt="image" src="https://github.com/user-attachments/assets/760a9a89-074e-4cdd-bf36-5b1eff3a5239" />

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
<img width="793" height="811" alt="image" src="https://github.com/user-attachments/assets/55cdb9ef-7692-49e8-b369-1a0dc0e752e5" />

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
<img width="480" height="475" alt="image" src="https://github.com/user-attachments/assets/d57cc591-c431-46cc-8f4e-703ef68aa683" />

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
<img width="640" height="452" alt="image" src="https://github.com/user-attachments/assets/853b425b-91a1-491e-b997-3be29b7c33ec" />

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
<img width="737" height="474" alt="image" src="https://github.com/user-attachments/assets/19eac4b4-b7de-4027-8f47-a6614ffb548b" />

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
<img width="789" height="467" alt="image" src="https://github.com/user-attachments/assets/9f691aa5-1017-4148-add4-141547e35cef" />

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
<img width="791" height="538" alt="image" src="https://github.com/user-attachments/assets/2d832670-8160-41b3-b3e2-b73cf19acf7b" />

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
<img width="726" height="496" alt="image" src="https://github.com/user-attachments/assets/dc40932f-586c-4cb8-aaea-739aecd04359" />

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
<img width="691" height="575" alt="image" src="https://github.com/user-attachments/assets/75c1e58a-84fe-4269-9b6b-9ff3aafad910" />

## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
