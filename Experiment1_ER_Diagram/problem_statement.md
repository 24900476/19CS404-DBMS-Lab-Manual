# ER Diagram Workshop – Submission Template
### NAME : KABIRA A
### REG NO : 212224040146
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

<img width="1177" height="638" alt="member er diagram" src="https://github.com/user-attachments/assets/f530aa51-afd5-4d79-919e-fc5d5c28fd16" />



### Entities and Attributes

| Entity          | Attributes (PK, FK)                                   | Notes                                |
|----------------|--------------------------------------------------------|--------------------------------------|
| Member         | MemberID (PK), Name, MembershipType, StartDate         | Registers for membership             |
|                |                                                        |                                      |
|                |                                                        |                                      |
| Program        | ProgramID (PK), ProgramName, Description               | Fitness programs                     |
|                |                                                        |                                      |
|                |                                                        |                                      |
| Trainer        | TrainerID (PK), TrainerName, Specialization            | Conducts sessions & programs         |
|                |                                                        |                                      |
|                |                                                        |                                      |
| ProgramTrainer | ProgramID (FK), TrainerID (FK)                         | M:N Program–Trainer mapping          |
|                |                                                        |                                      |
|                |                                                        |                                      |
| MemberProgram  | MemberID (FK), ProgramID (FK), JoinDate                | M:N Member–Program mapping           |
|                |                                                        |                                      |
|                |                                                        |                                      |
| Session        | SessionID (PK), TrainerID (FK), MemberID (FK),         | Personal training session            |
|                | SessionDate, SessionType                               |                                      |
|                |                                                        |                                      |
| Attendance     | AttendanceID (PK), SessionID (FK), MemberID (FK),      | Attendance for each session          |
|                | Status                                                 |                                      |
|                |                                                        |                                      |
| Payment        | PaymentID (PK), MemberID (FK), Amount, PaymentDate,    | Membership/session payments          |
|                | PaymentType                                            |                                      |
|                |                                                        |                                      |


### Relationships and Constraint

| Relationship                     | Cardinality     | Participation | Notes                                   |
|----------------------------------|------------------|---------------|-----------------------------------------|
| Member — joins — Program         | M : N            | Partial       | Via MemberProgram                       |
|                                  |                  |               |                                         |
|                                  |                  |               |                                         |
| Program — assigned to — Trainer  | M : N            | Partial       | Via ProgramTrainer                      |
|                                  |                  |               |                                         |
|                                  |                  |               |                                         |
| Member — books — Session         | 1 : M            | Partial       | One member may book many sessions       |
|                                  |                  |               |                                         |
|                                  |                  |               |                                         |
| Trainer — conducts — Session     | 1 : M            | Total         | Each session must have one trainer      |
|                                  |                  |               |                                         |
|                                  |                  |               |                                         |
| Session — has — Attendance       | 1 : 1 / 1 : M    | Total         | Each session has an attendance record   |
|                                  |                  |               |                                         |
|                                  |                  |               |                                         |
| Member — makes — Payment         | 1 : M            | Partial       | Multiple payments over time             |
|                                  |                  |               |                                         |
|                                  |                  |               |                                         |


### Assumptions
- Every personal training session is conducted between exactly one trainer and one membe
- Membership types available at the gym are Monthly, Quarterly, and Yearly.
- Attendance is recorded only for personal training sessions and not for general fitness programs.
- Payments recorded in the system include membership fees and fees for personal training sessions.
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

<img width="1133" height="693" alt="image" src="https://github.com/user-attachments/assets/e52be073-a9b1-492b-a854-a0ed8e2464b9" />



### Entities and Attributes

| Entity              | Attributes (PK, FK)                                             | Notes                                  |
|---------------------|------------------------------------------------------------------|----------------------------------------|
| Member              | MemberID (PK), Name, Address, Phone                             | Library users                          |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| Book                | BookID (PK), Title, Author, Category                             | Library books                          |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| Loan                | LoanID (PK), BookID (FK), MemberID (FK), LoanDate, DueDate,      | Tracks borrowing                       |
|                     | ReturnDate                                                       |                                        |
|                     |                                                                  |                                        |
| Fine                | FineID (PK), LoanID (FK), Amount, PaidStatus                     | Overdue fines                          |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| Event               | EventID (PK), EventName, EventDate, EventType                    | Library events                         |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| Speaker             | SpeakerID (PK), SpeakerName, Expertise                           | Guest speakers                         |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| EventSpeaker        | EventID (FK), SpeakerID (FK)                                     | M:N Event–Speaker mapping              |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| Room                | RoomID (PK), RoomName, Capacity                                  | Rooms for events & study               |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| EventRoomBooking    | BookingID (PK), EventID (FK), RoomID (FK), BookedTime            | Event room scheduling                  |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |
| EventRegistration   | EventID (FK), MemberID (FK)                                      | Members registering for events         |
|                     |                                                                  |                                        |
|                     |                                                                  |                                        |


### Relationships and Constraints

| Relationship                       | Cardinality     | Participation | Notes                                         |
|------------------------------------|------------------|---------------|-----------------------------------------------|
| Member — borrows — Book (Loan)     | 1 : M            | Partial       | One member can borrow many books              |
|                                    |                  |               |                                               |
|                                    |                  |               |                                               |
| Book — appears in — Loan           | 1 : M            | Partial       | Same book can be loaned many times            |
|                                    |                  |               |                                               |
|                                    |                  |               |                                               |
| Loan — generates — Fine            | 1 : 1 / 1 : M    | Partial       | Only overdue loans result in fines            |
|                                    |                  |               |                                               |
|                                    |                  |               |                                               |
| Event — has — Speaker              | M : N            | Partial       | Via EventSpeaker                              |
|                                    |                  |               |                                               |
|                                    |                  |               |                                               |
| Member — registers for — Event     | M : N            | Partial       | Via EventRegistration                         |
|                                    |                  |               |                                               |
|                                    |                  |               |                                               |
| Event — booked in — Room           | 1 : M            | Total         | Via EventRoomBooking                          |
|                                    |                  |               |                                               |
|                                    |                  |               |                                               |

### Assumptions
- A book can only be borrowed again after the previous borrower has returned it.
- Fines are charged only when books are returned after the due date
- Library rooms can be booked for only one event during a given time slot.
- Events may include multiple speakers, and members can freely register for any event.
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

<img width="940" height="493" alt="image" src="https://github.com/user-attachments/assets/f9386328-ea24-4208-9861-8d00613ae357" />


### Entities and Attributes

| Entity              | Attributes (PK, FK)                                             | Notes                                        |
|---------------------|------------------------------------------------------------------|----------------------------------------------|
| Customer            | CustomerID (PK), Name, Phone                                     | Reservation or walk-in customers             |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |
| Table               | TableID (PK), Capacity                                           | Restaurant tables                            |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |
| Reservation         | ReservationID (PK), CustomerID (FK), TableID (FK), Date, Time,   | Table booking details                         |
|                     | NumberOfGuests                                                   |                                              |
|                     |                                                                  |                                              |
| Order               | OrderID (PK), ReservationID (FK), OrderTime                      | Order placed per reservation                  |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |
| Dish                | DishID (PK), DishName, Price, Category                           | Menu items                                    |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |
| OrderItem           | OrderID (FK), DishID (FK), Quantity                              | M:N between Order and Dish                    |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |
| Bill                | BillID (PK), ReservationID (FK), TotalAmount, ServiceCharge      | Billing for each reservation                  |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |
| Waiter              | WaiterID (PK), WaiterName                                        | Assigned to reservations                      |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |
| WaiterAssignment    | WaiterID (FK), ReservationID (FK)                                | M:N Waiter–Reservation mapping                |
|                     |                                                                  |                                              |
|                     |                                                                  |                                              |

### Relationships and Constraints
| Relationship                            | Cardinality     | Participation | Notes                                               |
|-----------------------------------------|------------------|---------------|-----------------------------------------------------|
| Customer — makes — Reservation           | 1 : M            | Partial       | A customer may make many reservations               |
|                                         |                  |               |                                                     |
|                                         |                  |               |                                                     |
| Table — allocated for — Reservation      | 1 : M            | Total         | Each reservation must have one assigned table       |
|                                         |                  |               |                                                     |
|                                         |                  |               |                                                     |
| Reservation — generates — Order          | 1 : M            | Partial       | A reservation may result in multiple orders         |
|                                         |                  |               |                                                     |
|                                         |                  |               |                                                     |
| Order — contains — Dish (OrderItem)      | M : N            | Partial       | Via OrderItem associative entity                    |
|                                         |                  |               |                                                     |
|                                         |                  |               |                                                     |
| Reservation — produces — Bill            | 1 : 1            | Total         | One bill per reservation                            |
|                                         |                  |               |                                                     |
|                                         |                  |               |                                                     |
| Waiter — assigned to — Reservation       | M : N            | Partial       | Via WaiterAssignment                                |
|                                         |                  |               |                                                     |
|                                         |                  |               |                                                     |


### Assumptions

- Walk-in customers are recorded as customers with a temporary profile.
- A reservation may or may not lead to an order (e.g., cancellation).
- Service charge is applied per bill at a fixed percentage.
-  Each reservation normally has one assigned waiter, but the system supports multiple waiters if needed.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
