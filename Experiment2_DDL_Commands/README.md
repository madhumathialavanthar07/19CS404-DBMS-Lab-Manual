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
Write a SQL query to add birth_date attribute as timestamp (datatype) in the table customer 

Sample table: customer
```

 customer_id |   cust_name    |    city    | grade | salesman_id 
-------------+----------------+------------+-------+-------------
        3002 | Nick Rimando   | New York   |   100 |        5001
        3007 | Brad Davis     | New York   |   200 |        5001
        3005 | Graham Zusi    | California |   200 |        5002
 

For example:

Test	Result
pragma table_info('customer');
cid         name         type                               notnull     dflt_value  pk
----------  -----------  ---------------------------------  ----------  ----------  ----------
0           customer_id  integer primarykey auto increment  0                       0
1           cust_name    varchar2(30)                       0                       0
2           city         varchar(30)                        0                       0
3           grade        number                             0                       0
4           salesman_id  number                             0                       0
5           birth_date   timestamp                          0                       0
```
``` sql
ALTER TABLE customer
ADD birth_date timestamp
```

**Output:**
<img width="1171" height="506" alt="image" src="https://github.com/user-attachments/assets/bb245b3a-fb92-4a69-a139-e032fecdfa1c" />


**Question 2**
Insert all books from Out_of_print_books into Books
Table attributes are ISBN, Title, Author, Publisher, YearPublished
```
For example:

Test	Result
select * from Books;
ISBN            Title           Author              Publisher      YearPublished
--------------  --------------  ------------------  -------------  -------------
978-1234567890  The Lost World  Arthur Conan Doyle  Vintage Books  1912
978-0987654321  Gone with the   Margaret Mitchell   Macmillan      1936
978-1122334455  Moby Dick       Herman Melville     Harper & Brot  1851
```
``` sql
INSERT INTO books
SELECT *FROM Out_of_print_books;
```
**Output:**
<img width="1159" height="424" alt="image" src="https://github.com/user-attachments/assets/5d0a7faf-09c8-4b87-a858-785bf147a081" />

**Question 3**
Create a table named Reviews with the following columns:

ReviewID as INTEGER
ProductID as INTEGER
Rating as REAL
ReviewText as TEXT
```
For example:
Test	Result
pragma table_info('Reviews');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           ReviewID    INTEGER     0                       0
1           ProductID   INTEGER     0                       0
2           Rating      REAL        0                       0
3           ReviewText  TEXT        0                       0
```
``` sql
CREATE TABLE Reviews (
   ReviewID INTEGER,
   ProductID INTEGER,
   Rating REAL,
   ReviewText TEXT
);
```
**Output:**
<img width="1130" height="505" alt="image" src="https://github.com/user-attachments/assets/231eb4ab-4628-4e66-b294-c311cbf61ab8" />


**Question 4**
Create a new table named item with the following specifications and constraints:
item_id as TEXT and as primary key.
item_desc as TEXT.
rate as INTEGER.
icom_id as TEXT with a length of 4.
icom_id is a foreign key referencing com_id in the company table.
The foreign key should cascade updates and deletes.
item_desc and rate should not accept NULL.
```
For example:

Test	Result
INSERT INTO item VALUES("ITM5","Charlie Gold",700,"COM4");
UPDATE company SET com_id='COM5' WHERE com_id='COM4';
SELECT * FROM item;
item_id     item_desc     rate        icom_id
----------  ------------  ----------  ----------
ITM5        Charlie Gold  700         COM5
```
``` sql
CREATE TABLE item (
    item_id text primary key,
    item_desc text not null,
    rate integer not null,
    icom_id text check(length(icom_id) =4),
    foreign key (icom_id) references company(com_id)
    on update cascade
    on delete cascade
);
```

**Output:**
<img width="1147" height="499" alt="image" src="https://github.com/user-attachments/assets/42df8a6b-7349-4957-99fc-762f5f8471ca" />

**Question 5**
In the Books table, insert a record where some fields are NULL, another record where all fields are filled without any NULL values, and a third record where some fields are filled, and others are left as NULL.

ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021
```
For example:

Test	Result
SELECT * FROM Books;
ISBN             Title                      Author           Publisher   Year
---------------  -------------------------  ---------------  ----------  ----------
978-1234567890   Introduction to AI         John Doe
978-9876543210   Deep Learning              Jane Doe         TechPress   2022
978-1122334455   Cybersecurity Essentials   Alice Smith                  2021
```
``` sql
insert into Books (isbn, title, author)
values ('978-1234567890', 'Introduction to AI', 'John Doe');
insert into Books (isbn, title, author, publisher, year)
values ('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', 2022);
insert into Books (isbn, title, author, year)
values ('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', 2021);
```
**Output:**
<img width="1175" height="432" alt="image" src="https://github.com/user-attachments/assets/93e0bc2e-d9a3-46f3-a8be-c4a84efc3348" />

**Question 6**
Insert the below data into the Employee table, allowing the Department and Salary columns to take their default values.

EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst

Note: The Department and Salary columns will use their default values. 
```
For example:

Test	Result
SELECT EmployeeID, Name, Position 
FROM Employee;
EmployeeID  Name         Position
----------  -----------  ----------
4           Emily White  Analyst
```
```sql
insert into Employee(EmployeeID,Name,Position) values(4,'Emily White','Analyst');
```
**Output:**
<img width="1136" height="440" alt="image" src="https://github.com/user-attachments/assets/869250d6-1cb9-4a00-b410-11361aeee1a5" />

**Question 7**
Create a table named Attendance with the following constraints:
AttendanceID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
AttendanceDate as DATE.
Status as TEXT should be one of 'Present', 'Absent', 'Leave'.
```
For example:

Test	Result
INSERT INTO Attendance (AttendanceID, EmployeeID, AttendanceDate, Status) VALUES (1, 1, '2024-08-01', 'Present');
SELECT * FROM Attendance;
AttendanceID  EmployeeID  AttendanceDate  Status
------------  ----------  --------------  ----------
1             1           2024-08-01      Present
```
```sql
create table Attendance (
    AttendanceID Integer Primary key,
    EmployeeID Integer,
    AttendanceDate Date,
    Status TEXT CHECK(Status IN('Present','Absent','Leave')),
    Foreign key(EmployeeID) references Employees(EmployeeID)
);
```
**Output:**
<img width="1141" height="408" alt="image" src="https://github.com/user-attachments/assets/fc8e7d5b-f7f6-4a8e-8cdb-9f62fd0bf510" />

**Question 8**
Create a table named Employees with the following constraints:

EmployeeID should be the primary key.
FirstName and LastName should be NOT NULL.
Email should be unique.
Salary should be greater than 0.
DepartmentID should be a foreign key referencing the Departments table.
```
For example:

Test	Result
-- Attempt to insert a record with NULL FirstName
INSERT INTO Employees (EmployeeID, FirstName, LastName, Email, Salary, DepartmentID)
VALUES (1, NULL, 'Doe', 'john.doe@example.com', 50000, 1);
Error: NOT NULL constraint failed: Employees.FirstName
```
```sql
create table Employees (
    EmployeeID integer primary key,
    FirstName text not null,
    LastName text not null,
    Email text unique,
    Salary real check(Salary > 0),
    DepartmentID integer,
    foreign key (departmentid) references departments(departmentID)
);
```
**Output:**
<img width="1140" height="602" alt="image" src="https://github.com/user-attachments/assets/34c08dd5-a838-4bed-8c5d-567f057d2321" />

**Question 9**
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0
```
For example:

Test	Result
INSERT INTO products (product_id, product_name, list_price) VALUES (2, 'Product B', 50.00);
SELECT * FROM products;
product_id  product_name  list_price  discount
----------  ------------  ----------  ----------
2           Product B     50          0
```
```sql
create table products (
    product_id integer primary key,
    product_name text not null,
    list_price decimal(10,2) not null,
    discount decimal(10,2) not null default 0,
    check (list_price >= discount and discount >= 0 and list_price >=0)
);
```
**Output:**
<img width="1181" height="423" alt="image" src="https://github.com/user-attachments/assets/dfe58d89-c10c-4b6b-b160-439df9eae37f" />

**Question 10**
Write a SQL Query to add an attribute designation in the employee table with the data type VARCHAR(50).
```
For example:

Test	Result
pragma table_info('employee');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          integer     0                       0
1           salary      number      0                       0
2           designatio  varchar(50  0                       0
```
```sql
Alter table employee
add designation varchar(50)
```
**Output:**
<img width="1157" height="446" alt="image" src="https://github.com/user-attachments/assets/62e6a768-c740-497d-bdc3-7a8846466188" />

## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
