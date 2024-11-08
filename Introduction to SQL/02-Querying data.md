# Querying Data

Any command run in SQL is called a query, queries can be as complex as you want them or just be a simple query that fetches a single record. SQL does not force a style of writing queries but it is often a best practice to write the keywords of the language such as `SELECT` or `CREATE` in uppercase letters for better readability. 

> [!TIP]
>
> Comments can be added using double dashes to inform about what the query does when it's run.

```sql
-- Return all titles from the books table
SELECT title
FROM books;

-- Select title and author from the books table
SELECT title, author
FROM books;

-- Select all fields from the books table
SELECT * FROM books;
```

You can also use keywords like `DISTINCT` to show the records that are unique in the database. In the books table an author can write multiple books.

J.K. Rowling wrote all seven Harry Potter books, so if our library has all Harry Potter books, seven books will be written by J.K Rowling.

```sql
-- Select unique authors from the books table
SELECT DISTINCT author 
FROM books;

-- Select unique authors and genre combinations from the books table
SELECT  DISTINCT author, genre
FROM books;
```

> [!TIP]
>
> Aliases can be given to the resulting columns that are returned from running queries to give them more meaning and to clarify their intent.

## Setting limits

A table can have thousands of records, if you only need the first few records then you can set a limit on the amount of results a query returns using the `LIMIT` or `TOP` keywords based on the distribution of SQL you’re using.

```sql
-- Select the first 10 genres from books using PostgreSQL
SELECT genre 
FROM books LIMIT 10;

-- Select the first 10 genres from books using SQL Server
SELECT TOP(10) genre 
FROM books;
```

A view in SQL, allows you to see the results of a query that you have run before whenever you want without running the query again. They are like virtual tables in which the query result is stored instead of the data.

```sql
-- Save the results of this query as a view called library_authors
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;

-- Your code to create the view:
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;

-- Select all columns from library_authors
SELECT * FROM library_authors 
```

