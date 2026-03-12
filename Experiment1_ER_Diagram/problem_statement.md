# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="1366" height="902" alt="image" src="https://github.com/user-attachments/assets/80648257-7bcc-4be4-954a-22c894a13099" />


### Entities and Attributes
<img width="1142" height="356" alt="image" src="https://github.com/user-attachments/assets/46904974-618c-4eb7-aa84-bc6f2bcfbcfc" />



### Relationships and Constraints
<img width="1077" height="305" alt="image" src="https://github.com/user-attachments/assets/e6d3d943-43db-456b-8ec3-5d576f44a422" />

### Assumptions
One membership type per member.

A program must have at least one trainer.

Personal training is optional and billed separately.

Attendance is recorded only when members participate.



# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:


<img width="1247" height="891" alt="Screenshot 2026-03-10 133915" src="https://github.com/user-attachments/assets/d5dba62c-c15d-4e30-b923-4218b9b55b1a" />


### Entities and Attributes

<img width="956" height="325" alt="image" src="https://github.com/user-attachments/assets/47bc5116-1b22-47a5-98ff-84cd4abd4e96" />


### Relationships and Constraints

<img width="759" height="278" alt="image" src="https://github.com/user-attachments/assets/2b624661-d1b7-4e70-a646-3b83c8bc845f" />


### Assumptions
Each book has only one copy in the database (copies could be modeled separately if needed).

Fines are tracked as part of loan record.

Members may or may not attend events.

Each event takes place in exactly one room.


# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:

<img width="1201" height="708" alt="image" src="https://github.com/user-attachments/assets/daf246a3-b52a-4490-91cf-d2b2b2621d7b" />


### Entities and Attributes

<img width="1089" height="405" alt="image" src="https://github.com/user-attachments/assets/42353587-06e0-472d-bdc4-044c7cf9df6c" />

### Relationships and Constraints

<img width="870" height="315" alt="image" src="https://github.com/user-attachments/assets/4a0029a3-4e12-42af-adbe-6445ce690213" />


### Assumptions
Walk-in customers treated as reservations without advance booking.

One waiter handles a reservation at a time.

Service charge fixed per bill.

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
