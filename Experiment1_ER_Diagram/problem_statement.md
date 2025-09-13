# ER Diagram Workshop

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
*Paste or attach your diagram here*  
<img width="768" height="144" alt="fitness_er" src="https://github.com/user-attachments/assets/adef5847-be41-4ef6-adc5-ab73abc86f9e" />


### Entities and Attributes

| Entity                      | Attributes (PK, FK)                                             | Notes                             |
| --------------------------- | --------------------------------------------------------------- | --------------------------------- |
| **Member**                  | MemberID (PK), Name, MembershipType, StartDate                  | Each member unique                |
| **Program**                 | ProgramID (PK), ProgramName                                     | Yoga, Zumba, Weight Training      |
| **Trainer**                 | TrainerID (PK), Name, Specialty                                 | Multiple trainers per program     |
| **Enrollment**              | MemberID (FK), ProgramID (FK), EnrollDate                       | Resolves M\:N Member↔Program      |
| **PersonalTrainingSession** | SessionID (PK), MemberID (FK), TrainerID (FK), Date, Time       | Private booking                   |
| **Attendance**              | SessionID (FK), MemberID (FK), Status (Present/Absent)          | Tracks attendance                 |
| **Payment**                 | PaymentID (PK), MemberID (FK), Amount, PaymentDate, PaymentType | Covers both membership & sessions |


### Relationships and Constraints

| Relationship                      | Cardinality | Participation                     | Notes                                 |
| --------------------------------- | ----------- | --------------------------------- | ------------------------------------- |
| Member ↔ Program (via Enrollment) | M\:N        | Total (Member), Partial (Program) | A member must enroll in ≥1 program    |
| Program ↔ Trainer                 | M\:N        | Partial both                      | Trainers can handle multiple programs |
| Member ↔ Trainer (via Session)    | M\:N        | Partial both                      | Personal sessions                     |
| Member ↔ Attendance ↔ Session     | M\:N        | Total (Session), Partial (Member) | Tracks who attended                   |
| Member ↔ Payment                  | 1\:M        | Total (Payment)                   | Each payment belongs to a member      |


### Assumptions
- Membership types: Monthly, Quarterly, Yearly.

- Programs predefined (Yoga, Zumba, etc.).

- A session can have only one trainer and one member.

- Payments may include membership fees and personal training fees separately.

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
<img width="768" height="160" alt="library_er" src="https://github.com/user-attachments/assets/5f2367b0-acf3-4064-a6c3-d086a12a272c" />


### Entities and Attributes

| Entity           | Attributes (PK, FK)                                           | Notes              |
| ---------------- | ------------------------------------------------------------- | ------------------ |
| **Member**       | MemberID (PK), Name, Contact                                  | Library members    |
| **Book**         | BookID (PK), Title, Author, Category                          | Base entity        |
| **BookCopy**     | CopyID (PK), BookID (FK), Availability                        | Physical copy      |
| **Loan**         | LoanID (PK), CopyID (FK), MemberID (FK), LoanDate, ReturnDate | Resolves borrowing |
| **Fine**         | FineID (PK), LoanID (FK), Amount, PaidStatus                  | Linked to overdue  |
| **Event**        | EventID (PK), Name, Date, Topic                               | Cultural programs  |
| **Registration** | EventID (FK), MemberID (FK)                                   | Resolves M\:N      |
| **Speaker**      | SpeakerID (PK), Name, Expertise                               | Author or guest    |
| **EventSpeaker** | EventID (FK), SpeakerID (FK)                                  | Resolves M\:N      |
| **Room**         | RoomID (PK), Capacity                                         | Rooms used         |
| **EventRoom**    | EventID (FK), RoomID (FK)                                     | 1:1 mapping        |


### Relationships and Constraints

| Relationship             | Cardinality | Participation | Notes                        |
| ------------------------ | ----------- | ------------- | ---------------------------- |
| Member ↔ BookCopy (Loan) | M\:N        | Total (Loan)  | Tracks borrowing             |
| Loan ↔ Fine              | 1:1         | Partial       | Only overdue loans get fines |
| Event ↔ Member (Reg)     | M\:N        | Partial       | Members can register         |
| Event ↔ Speaker          | M\:N        | Partial       | Each event has ≥1 speaker    |
| Event ↔ Room             | 1:1         | Total         | Every event assigned a room  |


### Assumptions
- Each book may have multiple copies.

- Fine applies only if ReturnDate > DueDate.

- Each event is scheduled in exactly one room.

- A member can register for multiple events.
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
<img width="768" height="146" alt="restaurant_er" src="https://github.com/user-attachments/assets/a0de15ec-e56e-4f14-b013-4408866469ca" />



### Entities and Attributes

| Entity                | Attributes (PK, FK)                                                 | Notes                    |
| --------------------- | ------------------------------------------------------------------- | ------------------------ |
| **Customer**          | CustomerID (PK), Name, Phone                                        |                          |
| **Reservation**       | ReservationID (PK), CustomerID (FK), Date, Time, NumGuests          |                          |
| **Table**             | TableID (PK), Capacity                                              | Reserved tables          |
| **ReservationTable**  | ReservationID (FK), TableID (FK)                                    | Resolves assignment      |
| **Order**             | OrderID (PK), ReservationID (FK), OrderTime                         |                          |
| **Dish**              | DishID (PK), DishName, Price, CategoryID (FK)                       |                          |
| **Category**          | CategoryID (PK), CategoryName                                       | Starter/Main/Dessert     |
| **OrderDetails**      | OrderID (FK), DishID (FK), Quantity                                 | Resolves M\:N            |
| **Bill**              | BillID (PK), ReservationID (FK), FoodCharges, ServiceCharges, Total | One bill per reservation |
| **Waiter**            | WaiterID (PK), Name, Shift                                          |                          |
| **WaiterReservation** | WaiterID (FK), ReservationID (FK)                                   | Waiter assignment        |


### Relationships and Constraints

| Relationship                | Cardinality | Participation       | Notes                                    |
| --------------------------- | ----------- | ------------------- | ---------------------------------------- |
| Customer ↔ Reservation      | 1\:M        | Total (Reservation) | One customer can have many reservations  |
| Reservation ↔ Table         | M\:N        | Partial             | A reservation may use multiple tables    |
| Reservation ↔ Order         | 1\:M        | Partial             | One reservation can have many orders     |
| Order ↔ Dish (OrderDetails) | M\:N        | Total (Order)       | Tracks multiple dishes per order         |
| Dish ↔ Category             | M:1         | Total (Dish)        | Each dish belongs to a category          |
| Reservation ↔ Bill          | 1:1         | Total               | Each reservation generates one bill      |
| Waiter ↔ Reservation        | M\:N        | Partial             | A waiter can serve multiple reservations |


### Assumptions
- One bill per reservation (not per order).

- Walk-in customers also create a reservation entry.

- Each reservation may span multiple tables if needed.

- Service charges are fixed % of food total.

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
