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
![WhatsApp Image 2025-08-28 at 21 41 52_0d3b2057](https://github.com/user-attachments/assets/067a8872-0a16-4d0f-80c3-cde5fbe2cb97)

### Entities and Attributes

| Entity | Attributes (PK, FK)                | Notes   |
|--------|--------------------                |----------|
| User   |user_id (PK), name,mobile_no, address |Identifies the user.|  
| Permission| per_id (PK), per_module, per_name|Defines permissions granted to the user.|       
|Trainer| trainer_id (PK), name, mobile, email|Represents trainers managing the members.|      
| Member|mem_id (PK), mem_type, mem_name, mem_mobile, mem_email| Represents gym members.|       
| Fitness|fit_id (PK), fit_type, fit_desc|Defines the fitness programs.| 

### Relationships and Constraints
| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|User - Permission|1:N|Mandatory (A user must have at least one permission) | A user can have multiple permissions.|     
| User - Trainer| N:M|Optional (User may or may not be a trainer)| A user can manage many trainers and vice versa.|
| Trainer - Fitness|1:N|Mandatory (A trainer must be associated with at least one fitness type)|Trainers manage fitness types.|
|Member - Fitness|N:M|Optional (Members may or may not be associated with a fitness type)|A member can be associated with multiple fitness types.|

### Assumptions
- Role-Based Access: Users have different roles (e.g., admin, trainer, member), with permissions assigned based on their role.
- Trainer-Managed Programs: Trainers manage fitness programs, and members can join multiple fitness types, each guided by a trainer.
- Flexible Member Participation: Members can participate in multiple fitness programs, with flexibility in the types and number of programs they join.

---

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
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

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
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
