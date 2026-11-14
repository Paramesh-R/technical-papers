## 1. What is SQL?

SQL (Structured Query Language): A language used to store, retrieve, manipulate, and manage data in relational databases.


RDBMS: A database that stores data in related tables (rows and columns), similar to Excel.



Term	Meaning
Table	Collection of related data
Row	A single record
Column	An attribute/property
Schema	Structure/design of a database


Popular SQL Databases
- MySQL
- PostgreSQL
- SQLite
- Oracle
- Microsoft SQL Server
Note: All support SQL, but some syntax and features differ.




Why do we use SQL?
- Retrieve data.
- Insert new records.
- Update existing records.
- Delete records.
- Manage database structures.


Remember
 SQL is used to communicate with relational databases.


 ---

## 2. SQL SELECT Queries

**SELECT**: Used to retrieve data from a database table.

1. Select specific columns

    ```SQL
    SELECT column1, column2
    FROM table_name;
    ```

    Retrieves only the specified columns.


1. Select all columns
    ```SQL
    SELECT *
    FROM table_name;
    ```

Retrieves all columns and rows from the table.

Key points: 

- **SELECT** → Specifies what data to retrieve.
- **FROM** → Specifies which table to retrieve data from.
- **\*** → Represents all columns.
- Query result → Rows and columns.



Remember: SELECT only retrieves data; it does not modify the original table.

---

## 3. SQL – WHERE (Text Constraints)

Used to filter rows based on text conditions.


Operators
|Operator|	Meaning|
|---|---|
|=	|Exact match (case-sensitive)|
|!= or <>	|Not equal|
|LIKE	|Pattern matching (case-insensitive in SQLBolt)|
|NOT LIKE	|Does not match pattern|
|%	|Matches zero or more characters|
|_	|Matches exactly one character|
|IN()	|Matches any value in a given list|
|NOT IN()	|Excludes values in a given list|


```SQL
-- Exact match
WHERE name = 'John'

-- Contains "at"
WHERE name LIKE '%at%'

-- Starts with "A"
WHERE name LIKE 'A%'

-- Ends with "n"
WHERE name LIKE '%n'

-- Exactly 3 characters, starts with "A"
WHERE name LIKE 'A__'

-- Match multiple values
WHERE city IN ('Chennai', 'Bangalore')

```


Important points
- Text values must be inside quotes.
- % → Any number of characters.
- _ → Exactly one character.
- LIKE → Used for pattern matching.
Remember: WHERE filters rows; LIKE searches text patterns.



---
 
##  4: Filtering and Sorting Results
1. **DISTINCT** : Removes duplicate rows from the query result.


    ```SQL
    SELECT DISTINCT column_name
    FROM table_name;
    ```
2. **ORDER BY** : Sorts query results.
    
    ```SQL
    SELECT *
    FROM table_name
    ORDER BY column_name ASC;
    ```

   - ASC → Ascending (default).
   - DESC → Descending.
  
3. **LIMIT** : Restricts the number of rows returned.
    
    ```SQL
    SELECT *
    FROM table_name
    LIMIT 5;
    ```

    Returns only 5 rows.


4. **OFFSET** : Skips a specified number of rows before returning results.
    
    ```SQL
    SELECT *
    FROM table_name
    LIMIT 5 OFFSET 10;
    ```

    Skips 10 rows and returns the next 5.


#### Quick Revision
|Keyword	|Purpose|
|----|----|
|DISTINCT | Removes duplicates|
|ORDER BY | Sorts results|
|ASC	  | Ascending order|
|DESC	  | Descending order|
|LIMIT	  | Restricts rows|
|OFFSET	  | Skips rows|

Remember: **ORDER BY** sorts, **LIMIT** restricts, and **OFFSET** skips.

---

### SELECT SYNTAX
``` SQL
SELECT column1, column2
FROM table_name
WHERE condition
ORDER BY column_name ASC/DESC
LIMIT number
OFFSET number;
```

---




## SQL Lesson 6: Multi-table Queries with JOINs

**Database Normalization**: Organizing data into separate related tables to reduce duplicate data.

Benefit: Less duplicate data and easier maintenance.

1. Primary Key - A column that uniquely identifies each row in a table.
2. JOIN - Combines data from multiple tables using a related column.
3. INNER JOIN - Returns only matching rows from both tables.

Syntax:
```SQL
SELECT *
FROM table1
INNER JOIN table2
ON table1.id = table2.id;
```

Example:
- Table 1: Employees (employee_id, name)
- Table 2: Salaries (employee_id, salary)
INNER JOIN combines employee details with salaries where employee_id matches.

|Important| Keywords|
|----|----|
|Keyword|	Purpose|
|JOIN|	Combines tables|
|INNER| JOIN	Returns matching rows only|
|ON|	Specifies the matching condition|
|PRIMARY KEY| Uniquely identifies a row|

Remember: JOIN and INNER JOIN are equivalent.

Key concept: INNER JOIN = Only matching records from both tables.


---


## SQL Lesson 7: OUTER JOINs

Used when we want to retrieve matching and non-matching records from tables.

Types of OUTER JOINs

|JOIN	|What it returns|
|----|----|
|LEFT JOIN|	All rows from left table + matching rows from right|
|RIGHT JOIN|	All rows from right table + matching rows from left|
|FULL JOIN|	All rows from both tables|

Syntax

```SQL
SELECT *
FROM table1
LEFT JOIN table2
ON table1.id = table2.id;
```

Quick Example

Table A – Employees
|ID	|Name|
|----|----|
|1	|John|
|2	|David|

Table B – Salaries

|ID	|Salary|
|----|----|
|1	|30000|
|3	|40000|

|JOIN|	Result IDs|
|----|----|
|INNER JOIN|	1|
|LEFT JOIN	|1, 2|
|RIGHT JOIN|	1, 3|
|FULL JOIN	|1, 2, 3|

Important Points
- Unmatched columns return NULL.
- LEFT OUTER JOIN = LEFT JOIN.
- RIGHT OUTER JOIN = RIGHT JOIN.
- FULL OUTER JOIN = FULL JOIN.
  
Remember:
- LEFT → Keep everything from left.
- RIGHT → Keep everything from right.
- FULL → Keep everything from both.


---

## SQL Lesson 8: NULL Values

**NULL** means a value is missing, unknown, or unavailable.

Important: NULL is not the same as 0 or an empty string.


NULL Operators

|Operator	|Purpose|
|--|--|
|IS NULL	|Checks for missing values|
|IS NOT NULL|	Checks for available values|

Examples

```SQL
-- Find missing values
SELECT *
FROM employees
WHERE salary IS NULL;
```
```SQL
-- Find available values
SELECT *
FROM employees
WHERE salary IS NOT NULL;
```

Important Points
- NULL represents missing or unknown data.
- Use IS NULL, not = NULL.
- Use IS NOT NULL to exclude missing values.
- Default values like 0 or '' can be used when appropriate.

Remember: Never use = NULL or != NULL. Use IS NULL or IS NOT NULL.

---

## SQL Lesson 9: Queries with Expressions

1. **Expressions** perform calculations or transformations on column values directly inside a SQL query.

    Example:
    ``` SQL
    SELECT salary * 2
    FROM employees;
    ```

    Multiplies each employee's salary by 2.


2. **AS (Alias)**
    
    Gives a temporary, meaningful name to a column or table in query results.

    ```SQL
    SELECT salary * 2 AS double_salary
    FROM employees;
    ```

    Result column name: double_salary

3. **Table Alias**
    ```SQL
    SELECT *
    FROM employees AS e;
    ```

Uses e as a shorter name for employees.


Important Points
- **Expressions** → Perform calculations or transformations.
- **AS** → Assigns an alias.
- **Aliases** make queries easier to read.
- **Aliases** do not rename the original database columns or tables.
  
Remember: Expression = Calculation; Alias = Temporary name.

---

## SQL Lesson 10: Aggregate Functions

**Aggregate Functions**
    
Functions used to calculate and summarize data from multiple rows.

**Common Aggregate Functions**
|Function|	Purpose|
|--|--|
|COUNT()|	Counts rows|
|MIN()	|Finds smallest value|
|MAX()	|Finds largest value|
|AVG()	|Calculates average|
|SUM()	|Calculates total|

**Examples**
```SQL
-- Count employees
SELECT COUNT(*) FROM employees;

-- Find highest salary
SELECT MAX(salary) FROM employees;

-- Calculate average salary
SELECT AVG(salary) FROM employees;

-- Calculate total salary
SELECT SUM(salary) FROM employees;
```

***GROUP BY***

Groups rows having the same value and applies aggregate functions to each group.

```SQL
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

Returns the employee count for each department.

Important Points
- **COUNT(*)** → Counts all rows.
- **COUNT(column)** → Counts only non-NULL values.
- **GROUP BY** → Creates groups based on column values.
- Without GROUP BY, aggregate functions work on the entire result.

Remember: Aggregate functions summarize data; GROUP BY summarizes data separately for each group.

---

## SQL Lesson 11: HAVING Clause



**HAVING** filters grouped results, usually after applying aggregate functions.

Syntax
```SQL
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias, …
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;
```
Example
```SQL
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

Returns only departments having more than 5 employees.


WHERE vs HAVING

|WHERE	|HAVING|
|---|---|
|Filters individual rows|	Filters |grouped results
|Applied before GROUP BY|	Applied |after GROUP BY
|Generally used with columns|	Commonly |used with aggregate functions



Remember
- WHERE → Filters rows.
- GROUP BY → Groups rows.
- HAVING → Filters groups.
Easy way to remember: WHERE filters before grouping; HAVING filters after grouping.

---
## SQL Lesson 12: Order of Query Execution
SQL clauses are written in one order but executed in a different order.

Execution Order
1. FROM / JOIN

2. WHERE

3. GROUP BY

4. HAVING

5. SELECT

6. DISTINCT

7. ORDER BY

8. LIMIT / OFFSET


Purpose of Each Step

|Clause	|Purpose|
|---|---|
|FROM / JOIN	|Identify and combine |tables
|WHERE	|Filter individual rows|
|GROUP BY|	Group similar rows|
|HAVING	|Filter groups|
|SELECT	|Select columns and calculate |expressions
|DISTINCT|	Remove duplicates|
|ORDER BY|	Sort results|
|LIMIT / OFFSET|	Restrict and skip rows|

Important Points
- SQL execution order differs from writing order.
- WHERE executes before GROUP BY.
- HAVING executes after GROUP BY.
- SELECT aliases are generally unavailable in WHERE and HAVING.
- ORDER BY can use SELECT aliases.

Remember this execution order:

FROM → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY → LIMIT

---

## SQL Lesson 13: Inserting Rows

1. What is Schema?

    Schema defines the structure of a database table, including column names and data types.

    Example:
    - Year → INTEGER
    - Title → TEXT
2. INSERT INTO

    Used to insert new records (rows) into a table.

    Insert all columns:
    ```SQL
    INSERT INTO employees
    VALUES (1, 'John', 30000);
    ```

    Insert specific columns:
    ```SQL
    INSERT INTO employees (id, name)
    VALUES (2, 'David');
    ```

3. Insert Multiple Rows

    ```SQL
    INSERT INTO employees (id, name)
    VALUES
    (3, 'Sam'),
    (4, 'Peter');
    ```

Important Points
- Number of values must match the specified columns.
- Text values must be quoted.
- Unspecified columns use their default values (or NULL, if allowed).
- Specifying column names makes INSERT statements more flexible.
Remember: INSERT INTO adds new rows; it does not modify existing rows.

---

## SQL Lesson 14: Updating Rows
**UPDATE**

Used to modify existing records in a table.
Syntax
```
UPDATE table_name
SET column1 = value1,
    column2 = value2
WHERE condition;
```

Example
```
UPDATE employees
SET salary = 40000
WHERE id = 1;

```
Updates the salary of employee with ID 1.

Important Points
- UPDATE → Modifies existing rows.
- SET → Specifies new values.
- WHERE → Identifies which rows to update.
- Without WHERE → Updates ALL rows.

Warning
 Always check your WHERE condition using a SELECT query before executing an UPDATE.

Remember: UPDATE without WHERE can modify the entire table.

---

## SQL Lesson 15: Deleting Rows
**DELETE**

Used to remove existing rows from a table.

Syntax
```SQL
DELETE FROM table_name
WHERE condition;

```
Example
```SQL
DELETE FROM employees
WHERE id = 1;
```

Deletes the employee whose ID is 1.
Important Points
- DELETE → Removes rows.
- WHERE → Specifies which rows to delete.
- Without WHERE → Deletes ALL rows.
- Table structure remains unchanged.

Warning:

 Always test the WHERE condition using SELECT before executing DELETE.

Remember:
- INSERT → Add rows.
- UPDATE → Modify rows.
- DELETE → Remove rows.
---

## SQL Lesson 16: Creating Tables
***CREATE TABLE***

Used to create a new table with a defined structure (schema).

Syntax
    
    ```SQL
    CREATE TABLE IF NOT EXISTS table_name (
        column1 datatype constraint DEFAULT value,
        column2 datatype constraint DEFAULT value
    );
    ```

- IF NOT EXISTS → Creates the table only if it doesn't already exist.
- DEFAULT → Assigns a default value.


1. Common Data Types

    |Data Type|	Purpose|
    |-------|--------|
    |INTEGER|	Whole numbers|
    |FLOAT, DOUBLE, REAL|	Decimal numbers|
    |CHAR, VARCHAR, TEXT|	Text|
    |BOOLEAN|	True/False|
    |DATE, DATETIME	|Date and time|
    |BLOB	|Binary data|

1. Table Constraints
   
    |Constraint	|Purpose|
    |-------|--------|
    PRIMARY KEY|	Uniquely identifies each row
    AUTOINCREMENT|	Automatically generates incremental IDs
    UNIQUE	|Prevents duplicate values
    NOT NULL|	Prevents NULL values
    CHECK	|Validates values against a condition
    FOREIGN KEY	|Links to another table's key

1. Example
    ```SQL
    CREATE TABLE employees (
        id INTEGER PRIMARY KEY,
        name TEXT NOT NULL,
        age INTEGER,
        salary FLOAT
    );
    ```

Remember
- CREATE TABLE → Creates a table.
- Data type → Defines what data a column can store.
- Constraint → Defines rules for column values.
- Default → Provides a value when none is supplied.
Key concept: Schema defines the table structure; constraints enforce data rules.

----

## SQL Lesson 17: Altering Tables
ALTER TABLE
    
    Used to modify an existing table's structure.
Add a Column
    
```SQL
ALTER TABLE employees
ADD email VARCHAR(100);
```

Adds a new column.

Drop a Column
```SQL
ALTER TABLE employees
DROP COLUMN email;
```

Removes a column and its data.

4. Rename a Table
```SQL
ALTER TABLE employees
RENAME TO staff;
```

Changes the table name.


Quick Revision

|Command|	Purpose|
|----|----|
|ALTER TABLE|	Modify table structure|
|ADD	|Add a column|
|DROP COLUMN|	Remove a column|
|RENAME TO	|Rename a table|

Remember: ALTER TABLE changes the structure, not just the data.

Note: Supported ALTER operations vary across database systems.

----
## SQL Lesson 18: Dropping Tables
1. DROP TABLE
Completely removes a table, including its data and structure (schema).

Syntax
```SQL
DROP TABLE IF EXISTS employees;

```
- DROP TABLE → Removes the entire table.
- IF EXISTS → Prevents an error if the table doesn't exist.
- 
DELETE vs DROP vs TRUNCATE

|Command	|Purpose|
|---|---|
|DELETE	|Removes rows; keeps table |structure
|TRUNCATE|	Removes all rows; keeps |table structure
|DROP	|Removes the entire table|

Important Point

A table referenced by another table through a foreign key may not be dropped until its dependencies are handled.

Remember:
- DELETE → Remove rows.
- TRUNCATE → Empty the table.
- DROP → Remove the table itself.
---