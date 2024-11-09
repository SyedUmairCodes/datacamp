# Introduction to SQL

## Tables and Relations

A relational database solution like SQL has many advantages to it like it can hold more data than a spreadsheet and multiple users can access the data and you can even encrypt sensitive information that’s stored in a database.

In relational databases, data is organized in tables that are like spreadsheets but much more powerful. A table can be connected to another table through relations in which the data is shared among the tables.

```mermaid
flowchart LR
A(Employee) --> B(Deparment) 
A --> C(Job levels)
```

> [!NOTE]
>
> An employee table can store all the information about the employee and be connected to the department table to find which department each employee works in and also the job level table to see which employee is at which position in each department.

The data stored about each employee can be accessed using their employee id which is a unique identifier and is different for all employees.

### Naming best practices

Naming things is one of  the hardest things in programming, a good rule of thumb is to make the column names singular.  Each row only stores information about a single employee, columns like `zip-codes` should be named `zip-code` since each employee only has one address.

For storing values that have multiple options like a student being enrolled in multiple courses you can name the column as a plural such as `enrolled-courses`.

## Creating Tables

You can create your own databases and tables using the `CREATE` command in SQL, then you can use the database and add tables and records in it. 

> [!IMPORTANT]
>
> When creating tables, giving the correct data type to each column is very important as you want the data to be stored in the correct format.

Numerical operations can only happen on `Integer` and other numeric data types and not on other data types, selecting the right data type based on the data that’s going to be stored in the column is very important.

```sql
CREATE DATABASE Book_store
USE Book_store
CREATE Table Books (
 id int(16) PRIMARY KEY;
 name varchar (25);
 author varchar(25);
 year_published DATE;
 genre varchar(25);
)
```

If you’re hired at a company where they already have a huge SQL database with dozens of tables and thousands of rows of data it can be hard to fully understand the relationships and datatypes of each table, this is where a database schema comes into play. A schema is a high level overview of all of the tables, their columns, and their relationships in a database so that you can quickly get up to speed with the database.

```mermaid
erDiagram
    BOOKS {
        INT book_id PK
        VARCHAR title
        INT author_id FK
        DECIMAL price
        DATE publish_date
        INT stock_quantity
    }
    
    AUTHORS {
        INT author_id PK
        VARCHAR first_name
        VARCHAR last_name
        DATE birth_date
    }
    
    CUSTOMERS {
        INT customer_id PK
        VARCHAR first_name
        VARCHAR last_name
        VARCHAR email
        VARCHAR phone_number
    }
    
    AUTHORS ||--o{ BOOKS : "writes"
```

