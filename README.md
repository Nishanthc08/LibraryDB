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

### Queries
1. Basic Retrieval and Filtering:

- Retrieve all information about books.
  ```
  SELECT * FROM Books;
  ```
- List the titles and genres of all books in the database.
- Show the details of books published after the year 2000.

2. Advanced Filtering:

- Find all books in the Science Fiction genre that are currently available.
- List books published between 2010 and 2020.
- Which authors were born before 1900?

3. Joins and Relationships:

- Show the titles of all books along with their respective authors' names.
- Display the borrower names and return dates for all books that have been loaned out.

4. Aggregation and Sorting:

- Count the number of books published each year.
- List authors sorted by their birth year in descending order.
- Show the most borrowed book title and the number of times it has been borrowed.

5. Advanced Queries:

- Find books authored by J.K. Rowling.
- Retrieve books loaned out but not yet returned.
- List books with titles starting with 'The'.

6. Updates and Inserts:

- Mark a specific book as unavailable.
- Add a new book to the database with its respective author and genre.
- Record a new loan for a book with borrower details and loan date.

7. Constraints and Null Handling:

- List books with missing publication years.
- Identify loans that do not have a return date recorded.
- Delete a book record and its associated loans from the database.

8. Complex Queries:

- Show the names of borrowers who have borrowed books published before 1950.
- Find books in the Fantasy genre authored by J.R.R. Tolkien.
- Calculate the average number of days books are borrowed before being returned.
