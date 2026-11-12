# AMA Questions - Nov 12, 2026

### 1. What is "S" stands for in SOLID?

S – Single Responsibility Principle (SRP)

A class should have only one responsibility (one job).

Example:

Imagine a Student class:
- Store student details.
- Calculate student marks.
Sending emails should be handled by a separate class.

In simple words: One class = One job.

---
### 2. Query to insert row in a table?
```
INSERT INTO table_name (column1, column2, column3)
VALUES (value1, value2, value3);
```

---
### 3. Can a primary key column have a null value?

Primary Key = Unique + Not Null

Primary key is a column that uniquely identifies each row.

Primary keu CANNOT contain NULL values.

Because Primary Key uniquely identifies each row. so it must always have a value
---
### 4. What is self join in sql ?
Self Join means joining a table with itself.

It is used when we need to compare or connect rows within the same table.

Example:

Imagine an employees table:
emp_id	name	manager_id
1	Arun	NULL
2	Kumar	1
3	Ravi	1

```
SELECT
    e.name AS employee,
    m.name AS manager
FROM employees e
JOIN employees m
ON e.manager_id = m.emp_id;
```

Self Join allows us to use the same table twice to connect related records.

    
---
### 5. Use of foreign nkey?
Foreign Key is used to connect two tables.

It ensures that a value in one table matches an existing value in another table.

Example:

Students table
student_id (PK)	name
1	Arun
2	Kumar

Marks table
mark_id	student_id (FK)	marks
101	1	90
102	2	85

Here, student_id in the Marks table is a Foreign Key referencing the Students table.

In simple words: A Foreign Key connects two tables and maintains data consistency.

---
### 6. What is the difference between left join and right join?
LEFT JOIN: 

-   Returns all records from the left table and matching records from the right table.

-   If no match is found, the right table columns contain NULL.

RIGHT JOIN:

-   Returns all records from the right table and matching records from the left table.

-   If no match is found, the left table columns contain NULL.


Remember:
- LEFT JOIN → All rows from the left table.
- RIGHT JOIN → All rows from the right table.
---

### 7. What is the difference iterators and iterables?

#### Iterable

    An Iterable is something that you can loop through one item at a time.

    Examples: List, Tuple, String, Dictionary, Set.

#### Iterator
An Iterator is an object that gives you one item at a time when requested.


#### Difference :
- Iterable = Something you can loop over.

- Iterator = Something that provides the next item.

---
### 8. Can you give an example for interface segregation?
A class should not be forced to implement methods it doesn't need.

Example:

imagine an interface called Animal with these methods:
- eat()
- fly()
- swim()

A dog can eat and swim, but it cannot fly.

Instead of forcing the Dog class to implement all three methods create a smaller interfaces based on their responsibilities.

Don't force a class to use methods it does not need

---
### 9. List any 3 pip commands?

- pip install package_name – Installs a package.



- pip uninstall package_name – Uninstalls a package.



- pip list – Displays all installed packages.



---
### 10. What is generators?
Generators are special functions that produce values one at a time using yield keyword.

Example: Instead of storing all numbers in memory, a generator produces them one by one.

---
### 11. Types of joins in SQL?

- INNER JOIN – Returns matching records from both tables.



- LEFT JOIN – Returns all records from the left table.



- RIGHT JOIN – Returns all records from the right table.



- FULL OUTER JOIN – Returns all records from both tables.



- CROSS JOIN – Returns all possible combinations.



- SELF JOIN – Joins a table with itself.
---
### 12. What is the use of normalization?

Normalization organizes data into multiple related tables to:
- Avoid duplicate data.
- Maintain data consistency.
- Reduce data redundancy.
  
---
### 13. What will happen when we use DELETE without WHERE clause?

It deletes all rows from the table but keeps the table structure.
```
DELETE FROM students;
```

---
### 14. What is the difference between loops and Generator function?

|Loops|	Generator Functions|
|---------|----------|
|Used to repeat operations.	|Used to produce values one by one.|
|Can process existing data.	|Can generate data when needed.|
|Use for or while.	|Use yield.|

---
### 15. What is the difference between git reset and git reboot?
|git reset	|git revert|
|---------|----------|

|Moves the branch to an earlier commit.	|Creates a new commit to undo previous changes.|
|Can remove commits from branch history.	|Preserves existing commit history.|
|Mainly used for local changes.	|Safer for shared projects.|

Example:
- git reset – Removes the last commit from the current branch.
- git revert – Creates a new commit that reverses the last commit's changes.
Remember:
- Reset = Move backward in history.
- Revert = Undo changes by creating a new commit.

---
### 16. What is aggregate functions?
Aggregate functions perform calculations on multiple rows and return a single result.

Examples:
- COUNT() – Counts rows.
- SUM() – Calculates total.
- AVG() – Calculates average.
- MAX() – Finds maximum value.
- MIN() – Finds minimum value.

---
### 17. What is the use of git init?
git init creates a new Git repository in a folder.

In simple words: It enables Git version control for your project.

---
