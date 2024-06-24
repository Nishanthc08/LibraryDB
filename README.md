# Library Database

This project contains the SQL scripts to create and populate a library database.

## Database Schema

### Authors
- `author_id` (INT, Primary Key)
- `name` (VARCHAR)
- `birth_year` (INT)

### Books
- `book_id` (INT, Primary Key)
- `title` (VARCHAR)
- `author_id` (INT, Foreign Key)
- `published_year` (INT)
- `genre` (VARCHAR)
- `available` (BOOLEAN)

### Loans 
- `loan_id` (INT, Primary Key)
- `book_id` (INT, Foreign Key)
- `borrower_name` (VARCHAR)
- `loan_date` (DATE)
- `return_date` (DATE)

