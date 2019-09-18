# README file for SQL commands

## What is SQL?

Structured Query Language (SQL) is the database language used to perform certain operations on existing databases. This language can be used to create a database. SQL uses certain commands like Create, Drop, Insert etc. to carry out the required tasks.

## Types of commands

These commands are categorized into these categories:

DDL – Data Definition Language
DQl – Data Query Language
DML – Data Manipulation Language
DCL – Data Control Language
TCL - Transaction Control Language

Only DDL, DQL and DML types are described in this file.

## List of commands

### Create a Database

CREATE DATABASE <DB_name>;

### Use Database

USE <DB_name>;

### Create Table

CREATE TABLE <table_name> (
  <column_name> <type of data in column>,;
  )

e.g.
USE my_db;
CREATE table film_table
(
film_name VARCHAR(64) ,
film_type VARCHAR(24),
date_of_release DATE,
Director VARCHAR(32),
Writer VARCHAR(32),
Rating DECIMAL(3,2),
Language VARCHAR(24),
Official_Website VARCHAR(64),
Plot_Summary VARCHAR(MAX);
)


### Delete Table

DROP TABLE <table_name>

### Adding a column

Alter table <table_name> Add <column_name> <type of data used in column>

e.g.

USE my_db;
ALTER table film_table ADD Trailer_link VARCHAR(64);

### Modifying an existing column

Alter table <table_name> Add  column <column_name> <type of data used in column>

USE my_db;
ALTER TABLE film_table
ALTER COLUMN Trailer_link VARCHAR(64);

### Replacing data in the table

UPDATE <table_name>
SET <column_name_for_change>= <NEW DATA INPUT>
WHERE <column_name_condition> = <condition>

### Delete all data in a table

DELETE FROM <table_name>

### Delete data from a row

DELETE FROM <table_name>
WHERE <column_name_condition> = <condition>

### Making sure data isn't left blank using NOT NULL

Create table <table_name>
(
(column_name_1) (data_type) NOT NULL,
(column_name_2) (data_type) NOT NULL
)

### Making a Primary Key when making the table

Create table <table_name>
(
(column_name_1) (data_type) NOT NULL identity primary Key,
(column_name_2) (data_type) NOT NULL
)

### Wildcards

% - substitute for zero or more characters

_ - substitute for a single character

[character_list] – brings back anything starting with those letters

[^character_list] – brings back anything that does not start with those letters

### String functions

SUBSTRING(expression, start, length) – makes a substring of an existing string

CHARINDEX(‘a’,’text’) – “find ‘a’ in column called ‘text’”

LEFT(name, 5) - for the first or last 5 characters take the left most part of a string

LTRIM or RTRIM - used to remove spaces at the beginning or end of a string

LEN(name) - the length of the string

Replace - Replace things. e.g. Replace(name, ‘  ‘, ‘____’) to replace spaces with underscore in the column

UPPER(name) to convert to all upper (or lower) case

### Dates

SELECT GETDATE() – returns current date & time

SELECT SYSDATETIME() – returns the date and time of the computer being used

DATEADD(d/m/Y,5,OrderDate) AS “Due Date” to add 5 days/months/Years

DATEDIFF(d, OrderDate, ShippedDate) to calculate the difference between two dates

SELECT YEAR(OrderDate) AS “Order Year” gets year from a date

SELECT MONTH(OrderDate) AS “Order Month” gets month from a date

SELECT DAY(OrderDate) AS “Order Day” gets day from a date

### Conditional cases

SELECT <column_name> CASE
WHEN DATEDIFF(d, OrderDate, ShippedDate) < 10 THEN ‘On Time’
ELSE ‘Overdue’
END AS ‘Status’
FROM Orders

### Grouping functions

SUM(<column_name>) – grand total of a column for all rows selected

AVG(<column_name>) – average of the column for all rows selected

MIN(<column_name>) – finds the smallest value in a column for all rows

MAX(<column_name>) - finds the largest value in a column for all rows

COUNT(<column_name>) – counts the number of rows in column. If * is used then all rows are counted.

These must be used in conjunction with a GROUP BY clause.

HAVING is essentially a WHERE condition used only for when a GROUP BY clause is in effect. It limits the data in the query based on a given condition.

### Find All Columns and Rows in a Table

SELECT * FROM <table name>;

### Retrieving Specific Columns of Information

SELECT <column_name> FROM <table name>;

### Aliasing Column Names

SELECT <column name> AS <alias> FROM <table name>

### Finding the Data You Want

SELECT <columns> FROM <table> WHERE <condition>;

### Equality Operator

Find all rows that a given value matches a column's value.

SELECT <columns> FROM <table> WHERE <column name> = <value>;

### Inequality Operator

The not equal to or inequality operator can be written in two ways != and <>. The latter is less common.

SELECT <columns> FROM <table> WHERE <column name> != <value>;
SELECT <columns> FROM <table> WHERE <column name> <> <value>;

### Relational Operators

There are several relational operators you can use:

•	< less than
•	<= less than or equal to
•	> greater than
•	>= greater than or equal to

These are primarily used to compare numeric and date/time types.

SELECT <columns> FROM <table> WHERE <column name> < <value>;

SELECT <columns> FROM <table> WHERE <column name> <= <value>;

SELECT <columns> FROM <table> WHERE <column name> > <value>;

SELECT <columns> FROM <table> WHERE <column name> >= <value>;

### More Than One Condition

You can compare multiple values in a WHERE condition. If you want to test that both conditions are true use the AND keyword, or either conditions are true use the OR keyword.

SELECT <columns> FROM <table> WHERE <condition 1> AND <condition 2> ...;

SELECT <columns> FROM <table> WHERE <condition 1> OR <condition 2> ...;

### Searching in a Set of Values

SELECT <columns> FROM <table> WHERE <column> IN (<value 1>, <value 2>, ...);

To find all rows that are not in the set of values you can use NOT IN.

SELECT <columns> FROM <table> WHERE <column>  NOT IN (<value 1>, <value 2>, ...);

### Searching within a Range of Values

SELECT <columns> FROM <table> WHERE <column> BETWEEN <lesser value> AND <greater value>;

### Missing Values

SELECT * FROM <table> WHERE <column> IS NULL;

### Ordering Columns

Ordering by a single column criteria:
SELECT * FROM <table name> ORDER BY <column> [ASC|DESC];

### Limiting Results

SELECT TOP <# of rows> <columns> FROM <table>;

### Concatenating Strings

SELECT <value or column> + <value or column> + <value or column>  FROM <table>;  
