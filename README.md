# Library Management System

A fully normalised relational database (1NF through BCNF) built in MySQL, connected to a Java CLI application via JDBC. Demonstrates core DBMS concepts including normalisation, weak entities, ISA hierarchies, participation constraints, transactions, and query optimisation.

## Tech Stack
Java, JDBC, MySQL

## Project Structure
```
library-management-system/
├── db/
│   ├── schema/
│   │   ├── 01_create_tables.sql       # DDL for all 10 tables
│   │   └── 02_insert_sample_data.sql  # Sample seed data
│   ├── queries/
│   │   ├── member_queries.sql         # Member lookup and loan history
│   │   ├── book_queries.sql           # Book search and availability
│   │   └── report_queries.sql         # Overdue books, fine reports
│   ├── indexes/
│   │   └── create_indexes.sql         # Indexes on email, isbn, loan_date
│   └── triggers/
│       └── fine_trigger.sql           # Auto-compute fine on overdue return
├── src/
│   ├── dao/
│   │   ├── MemberDAO.java
│   │   ├── BookDAO.java
│   │   ├── CopyDAO.java
│   │   ├── LoanDAO.java
│   │   └── FineDAO.java
│   ├── model/
│   │   ├── Member.java
│   │   ├── Book.java
│   │   ├── Copy.java
│   │   ├── Loan.java
│   │   └── Fine.java
│   ├── service/
│   │   ├── LoanService.java           # Business logic: issue, return, fine calc
│   │   ├── MemberService.java
│   │   └── BookService.java
│   ├── util/
│   │   ├── DBConnection.java          # Singleton JDBC connection
│   │   └── InputValidator.java
│   └── cli/
│       ├── Main.java                  # Entry point
│       └── MenuController.java        # Interactive CLI menu loop
├── docs/
│   ├── er_diagram.png                 # ER diagram
│   ├── normalisation_notes.md         # FDs and normal form proofs
│   └── schema_description.md
├── db.properties                      # DB credentials (gitignored)
├── .gitignore
└── README.md
```

## DBMS Concepts Demonstrated
- **1NF**: Eliminated repeating groups (authors stored in separate table)
- **2NF**: Removed partial dependencies (author nationality separated from book-author table)
- **3NF**: Eliminated transitive dependencies (publisher details extracted)
- **BCNF**: Documented determinants for all tables
- **Weak Entity**: Copy depends on Book for existence
- **ISA Hierarchy**: StudentMember and FacultyMember as subtypes of Member
- **Participation Constraints**: Every Fine must reference a Loan (total participation)
- **Transactions**: Loan issuance atomically updates Copy availability

## Setup
```bash
# 1. Create database
mysql -u root -p < db/schema/01_create_tables.sql
mysql -u root -p < db/schema/02_insert_sample_data.sql

# 2. Configure credentials
cp db.properties.example db.properties
# Edit db.properties with your MySQL credentials

# 3. Compile and run
javac -cp .:lib/mysql-connector.jar src/**/*.java
java -cp .:lib/mysql-connector.jar cli.Main
```

## CLI Menu
```
========= Library Management System =========
1. Add new member
2. Search books
3. Issue book
4. Return book
5. View member loan history
6. View overdue books
7. Pay fine
8. Exit
```
