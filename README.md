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
  ```
  SELECT title, genre FROM Books;
  ```
- Show the details of books published after the year 2000.
  ```
  SELECT * FROM Books WHERE published_year > 2000;
  ```
  
2. Advanced Filtering:

- Find all books in the Science Fiction genre that are currently available.
  ```
  SELECT * FROM Books WHERE genre = 'Science Fiction' AND available = TRUE;
  ```
- List books published between 2010 and 2020.
  ```
  SELECT * FROM Books WHERE published_year BETWEEN 2010 AND 2020;
  ```
- Which authors were born before 1900?
  ```
  SELECT * FROM Authors WHERE birth_year < 1900;
  ```
  
3. Joins and Relationships:

- Show the titles of all books along with their respective authors' names.
  ```
  SELECT b.title, a.name AS author_name
  FROM Books b
  INNER JOIN Authors a ON b.author_id = a.author_id;
  ```
- Display the borrower names and return dates for all books that have been loaned out.
  ```
  SELECT borrower_name, return_date FROM Loans;
  ```
  
4. Aggregation and Sorting:

- Count the number of books published each year.
  ```
  SELECT published_year, COUNT(*) AS num_books
  FROM Books
  GROUP BY published_year;
  ```
- List authors sorted by their birth year in descending order.
  ```
  SELECT * FROM Authors ORDER BY birth_year DESC;
  ```
- Show the most borrowed book title and the number of times it has been borrowed.
  ```
  SELECT b.title AS most_borrowed_book, COUNT(*) AS num_loans
  FROM Books b
  INNER JOIN Loans l ON b.book_id = l.book_id
  GROUP BY b.title
  ORDER BY num_loans DESC
  LIMIT 1;
  ```
  
5. Advanced Queries:

- Find books authored by J.K. Rowling.
  ```
  SELECT * FROM Books b
  INNER JOIN Authors a ON b.author_id = a.author_id
  WHERE a.name = 'J.K. Rowling';
  ```
- Retrieve books loaned out but not yet returned.
  ```
  SELECT * FROM Loans WHERE return_date IS NULL;
  ```
- List books with titles starting with 'The'.
  ```
  SELECT * FROM Books WHERE title LIKE 'The%';
  ```
  
6. Updates and Inserts:

- Mark a specific book as unavailable.
  ```
  UPDATE Books SET available = FALSE WHERE book_id = 1;
  ```
- Add a new book to the database with its respective author and genre.
  ```
  INSERT INTO Books (book_id, title, author_id, published_year, genre, available)
  VALUES (4, 'New Book', 2, 2022, 'Mystery', TRUE);
  ```
- Record a new loan for a book with borrower details and loan date.
  ```
  INSERT INTO Loans (loan_id, book_id, borrower_name, loan_date, return_date)
  VALUES (3, 2, 'Emily Johnson', '2023-03-01', NULL);
  ```
  
7. Constraints and Null Handling:

- List books with missing publication years.
  ```
  SELECT * FROM Books WHERE published_year IS NULL;
  ```
- Identify loans that do not have a return date recorded.
  ```
  SELECT * FROM Loans WHERE return_date IS NULL;
  ```
- Delete a book record and its associated loans from the database.
  ```
  DELETE FROM Books WHERE book_id = 3;
  DELETE FROM Loans WHERE book_id = 3;
  ```
8. Complex Queries:

- Show the names of borrowers who have borrowed books published before 1950.
  ```
  SELECT l.borrower_name
  FROM Loans l
  INNER JOIN Books b ON l.book_id = b.book_id
  WHERE b.published_year < 1950;
  ```
- Find books in the Fantasy genre authored by J.R.R. Tolkien.
  ```
  SELECT b.title
  FROM Books b
  INNER JOIN Authors a ON b.author_id = a.author_id
  WHERE b.genre = 'Fantasy' AND a.name = 'J.R.R. Tolkien';
  ```
- Calculate the average number of days books are borrowed before being returned.
  ```
  SELECT AVG(DATEDIFF(return_date, loan_date)) AS avg_days_borrowed
  FROM Loans
  WHERE return_date IS NOT NULL;
  ```
