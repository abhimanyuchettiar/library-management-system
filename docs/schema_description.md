# Schema Description

## Tables
- **Member** — library members (students and faculty)
- **Book** — book metadata, linked to Publisher
- **Author** — author details
- **BookAuthor** — many-to-many junction: Book <-> Author
- **Publisher** — publisher details (extracted for 3NF)
- **Copy** — physical copies of a book (weak entity)
- **Loan** — borrowing record linking Member and Copy
- **Fine** — overdue fine linked to a Loan
- **Reservation** — book reservation by a Member
- **Staff** — library staff

## Key Relationships
TODO: Describe cardinality and participation for each relationship
