---
tags:
  - degree/compsys/databases
---
h![[Databases MOC 🌍]]

### What makes a good database language?

Should allow users to
- Define relations 
- Define attribute domains
- Define constraints 
- Insert, modify and delete data 
- Perform simple and complex queries.

Plus the syntax should be easy to learn and use and conform to a recognised standard.

---
### SQL 

Structured Query Language:
- Is the most common database language 
- Is an ISO/ANSI standard 
- Has a simple syntax 
- Has two components DDL and DML

Data Definition Language (DDL)
- Define the schema for each relation (attributes)
- Define the domain of each attribute 
- Specify integrity constraints (primary / foreign keys)

Data Manipulation Language (DML)
- Insert / update / delete / retrieve data 
- Query language

---
### SQL Statements 

An SQL statement consists of
- Reserved words like SELECT, WHERE, IS, NOT, NULL
- User-defined words like relation or attribute names.

```sQL
SELECT fName, lName
FROM Staff
WHERE Staff.position != 'Assistant' AND Staff.salary > 10000
```

Most of SQL is case-insensitive but relation names and string literals are.

SQL is free-format, so line breaks, white space and indentation do not matter.

Statements can be chained and terminate with a semicolon. Semicolons can sometimes be required.

For example, this is entirely valid SQL.
```sQL
SeLeCt fNaMe, LnAmE
fRoM sTaFf
WhErE sTaFf.PoSiTiOn != 'Assistant' aNd StAfF.sAlArY > 10000
```
But try using it, see what it gets you.

---
### Primary Domain Types in SQL 

- `CHAR(n)`: Character string of fixed length $n$.
- `VARCHAR(n)`: Character string of maximum length $n$.
- `BIT(n)`: bit string of fixed length $n$.
- `INTEGER`: large positive/negative integer values.
- `SMALLINT`: small positive/negative integer values (up to 32767, equivalent to a `SHORT` in cpp)
- `NUMERIC(p,d)`: A (positive/negative) decimal number with precision $p$ (total number of digits) and scale $d$ (number of decimal digits).

##### Custom Domain Types 
We can also define our own custom domain types.

```sQL
CREATE DOMAIN Postcode AS VARCHAR(8)
```

```sQL
CREATE DOMAIN GenderType AS CHAR(1)
CHECK (VALUE IN ('M', 'F', 'O'))
```

```sQL
CREATE DOMAIN StaffNumber AS VARCHAR(5)
CHECK (VALUE IN (SELECT staffNo FROM Staff))
```

---
### Data Manipulation Language (DML)

Manipulation of an existing database.

The main statements of interest in DML 
- [[#SELECT Statement|SELECT]] - To query data in the database.
- [[#INSERT Statement|INSERT]] - To insert new data into an existing table.
- [[#UPDATE Statement|UPDATE]] - To update data in an existing table.
- [[#DELETE Statement|DELETE]] - To delete data from an existing table.

---
### SELECT Statement

```sQL
SELECT [DISTINCT] {* | column1 [AS newName][, ...]}
FROM table1 [alias] [, ...]
[WHERE conditions]
[GROUP BY columnList]
[HAVING conditions]
[ORDER BY columnList [ASC | DESC]]
```

The sequence of processing:
- `FROM` - specifies the table or tables to be used.
- `WHERE` - filters the rows subject to some condition.
- `GROUP BY` - forms groups of rows with the same column value.
- `HAVING` - filters the groups subject to some condition.
- `SELECT` - specifies which columns are to appear in the output.
- `ORDER BY` - specifies the order of the output.

##### SELECT FROM
```sQL
SELECT staffNo, fName, lName, salary
FROM Staff
```

Returns a table with only the specified columns from Staff.

| `staffNo` | `fName` | `lName` | `salary` |
| ---- | ---- | ---- | ---- |
| SA9 | Mary | Howe | 9000 |
| SG14 | David | Ford | 18000 |
| SG37 | Ann | Beech | 12000 |
| SG5 | Susan | Brand | 24000 |
| SL21 | John | White | 30000 |
| SL41 | Julie | Lee | 9000 |

##### Aliases
```sQL
SELECT staffNo, fName, lName, salary/12 AS monthly
FROM Staff
```
Here `salary/12` is a derived attribute and can be referred to as `monthly`.

| `staffNo` | `fName` | `lName` | `monthly` |
| ---- | ---- | ---- | ---- |
| SA9 | Mary | Howe | 750 |
| SG14 | David | Ford | 1500 |
| SG37 | Ann | Beech | 1000 |
| SG5 | Susan | Brand | 2000 |
| SL21 | John | White | 2500 |
| SL41 | Julie | Lee | 750 |

##### SELECT WHERE
```sQL
SELECT staffNo, fName, lName, salary/12 AS monthly
FROM Staff
WHERE salary/12 < 1500
```

>[!attention] 
>You **cannot** reuse alias in `WHERE`, `GROUP BY` or `HAVING` clause.

Here we are getting a table in which the monthly salaries are less than 1500.

| `staffNo` | `fName` | `lName` | `monthly` |
| ---- | ---- | ---- | ---- |
| SA9 | Mary | Howe | 750 |
| SG37 | Ann | Beech | 1000 |
| SL41 | Julie | Lee | 750 |

##### Derived Query Hacks
```sQL
SELECT staffNo, fName, lName, salary AS yearlySalary, (SELECT yearlySalary)/12 AS monthlySalary
FROM Staff
WHERE salary/12 < 1500
```

This includes the yearly salary, and reuses the yearly salary alias.

This can be inconsistent depending on the implementation.

| `staffNo` | `fName` | `lName` | `yearlySalary` | `monthlySalary` |
| ---- | ---- | ---- | ---- | ---- |
| SA9 | Mary | Howe | 9000 | 750 |
| SG37 | Ann | Beech | 12000 | 1000 |
| SL41 | Julie | Lee | 9000 | 750 |

##### DISTINCT

A response may contain duplicate rows.
```sQL
SELECT salary
FROM Staff
```

| salary |
| ---- |
| 9000 |
| 18000 |
| 12000 |
| 24000 |
| 30000 |
| 9000 |
Use the `DISTINCT` keyword to eliminate duplicates.
```sQL
SELECT DISTINCT salary
FROM Staff
```

| salary |
| ---- |
| 9000 |
| 18000 |
| 12000 |
| 24000 |
| 30000 |

##### BETWEEN

```sQL
SELECT fName, lName, salary
FROM Staff
WHERE salary BETWEEN 12000 AND 20000
```

>[!important] 
>The between operator includes the min and max.

This is equivalent to
```sQL
SELECT fName, lName, salary
FROM Staff
WHERE salary >= 12000 AND salary <= 20000
```

##### IN

```sQL
SELECT fName, lName, salary, position
FROM Staff
WHERE position IN ('Manager', 'Supervisor')
```

This would list the details of all employees who's position is either Manager or Supervisor.

This is equivalent to
```sQL
SELECT fName, lName, salary, position
FROM Staff
WHERE position='Manager' OR position='Supervisor'
```

##### LIKE

For situations like "*Find all staff whose first name starts with J*"

SQL has two pattern-matching symbols, the `%` and `_`.
- `%` represents an arbitrary sequence of characters.
- `_` represents and arbitrary single character.

`LIKE 'H%'` means starting with 'H'.
`LIKE 'H___'` means 4 characters, starting with 'H'.
`LIKE '%e'` means any string ending with 'e'.
`NOT LIKE 'H%'` means first character is not 'H'.

```sQL
SELECT fName, lName
FROM Staff
WHERE fName LIKE 'J%'
```
Staff whose first names start with 'J'.

```sQL
SELECT fName, lName
FROM Staff
WHERE fName LIKE '____'
```
Staff whose first names are 4 characters.

##### Combining Conditions 

```sQL
SELECT fName, lName, position, salary
FROM Staff
WHERE position NOT IN ('Manager', 'Supervisor') AND
(fName LIKE 'J%' OR salary > 10000)
```

This gets all staff who are not managers or supervisors and either their name starts with J, or their salary is over 10k.

Parenthesis is used to group expressions, like BIDMAS.

##### Testing for NULL 

```sQL
SELECT *
FROM Viewing
WHERE propertyNo='PG4' AND comment IS NULL
```

We have to specifically test for `NULL` since it's not a value.

`NULL` is not the same as `''`.

##### ORDER BY clause 

The table returned by SELECT is not ordered. ORDER BY can be used to sort the rows.

```sQL
SELECT fName, lName, gender
FROM Staff 
ORDER BY gender, fName
```
It uses ascending ASC by default, or you can specify descending DESC.

```sQL
SELECT fName, lName, gender 
FROM Staff
ORDER BY gender ASC, fName DESC
```

The table is ordered by the first variable, then by the 2nd, 3rd etc.

##### Aggregate Functions 

Operates on a single column to return a single value.

```sQL
SELECT AVG(salary) FROM Staff
SELECT SUM(salary) FROM Staff 
SELECT COUNT(salary) FROM Staff 
SELECT SUM(salary)/COUNT(salary) FROM Staff
SELECT COUNT(DISTINCT salary) FROM Staff
```

You can combine these with selectors.
```sQL
SELECT AVG(salary) AS managerSalary
FROM Staff
WHERE position='Manager'
```

##### GROUP BY clause 

Used in combination with aggregate functions.
It first groups rows by attributes 
then the aggregate functions are applied to each group.

```sQL
SELECT position, AVG(salary)
FROM Staff
GROUP BY position 
ORDER BY AVG(salary) DESC
```
This request would return 

| position | AVG(salary) |
| ---- | ---- |
| Manager | 27000 |
| Supervisor | 18000 |
| Assistant | 10000 |

##### Joins 

Queries multiple tables into one result.

Usually we want some combination of 
- Combining rows 
- Filtering rows based on some criterion 
- Appending rows 

##### Inner Join

Without using `JOIN`
```sQL
SELECT *
FROM Staff, Branch
WHERE Staff.branchNo = Branch.branchNo
```
This may be inefficient as it constructs all combinations first.

Using `JOIN USING`
```sQL
SELECT *
FROM Staff JOIN Branch USING branchNo
```
This is not implemented by all [[Database Management System|DBMS]].

Using `JOIN ON`
```sQL
SELECT *
FROM Staff JOIN Branch ON Staff.branchNo = Branch.branchNo
```
This is an efficient and general solution.

As an example:
```sQL
SELECT fName, lName, street 
FROM Staff JOIN Branch ON Staff.branchNo = Branch.branchNo
WHERE fName LIKE '____'
```
This gets the names of staff with 4 letter names and the street of the branch they work in.

| fName | lName | street |
| ---- | ---- | ---- |
| Mary | Howe | 16 Argyll St |
| John | White | 22 Deer Rd |

##### Outer Join 

Outer join left includes in the result any records from the left table which did not have a join.

For example, if you had a table called `Staff` like 

| fName | lName |
| ---- | ---- |
| John | White |
| Betty | Rand |
| William | Hardy |

And you joined it with `Salaries`

| lName | salary |
| ---- | ---- |
| White | 9000 |
| Rand | 10000 |
| Gerard | 17000 |

A request like
```sQL
SELECT fName, lName, salary
FROM Staff LEFT JOIN Salaries ON Staff.lName = Salaries.lName
```
would return 

| fName | lName | salary |
| ---- | ---- | ---- |
| John | White | 9000 |
| Betty | Rand | 10000 |
| William | Hardy | NULL |

and a request like 
```sQL
SELECT fName, lName, salary
FROM Staff RIGHT JOIN Salaries ON Staff.lName = Salaries.lName
```
would return 

| fName | lName | salary |
| ---- | ---- | ---- |
| John | White | 9000 |
| Betty | Rand | 10000 |
| NULL | Gerard | 17000 |

##### Subqueries 

```sQL
SELECT staffNo, fName, lName, position 
FROM Staff 
WHERE branchNo = (
	SELECT branchNo
	FROM Branch 
	WHERE street = '163 Main St'
)	
```
This request gets all staff who work at the branch at 163 Main St.

Say the branch number of the 163 Main St branch was `'B003'`, this would be equivalent to

```sQL
SELECT staffNo, fName, lName, position 
FROM Staff 
WHERE branchNo = 'B003'
```

##### SOME or ANY Operator 

The `SOME` and `ANY` operators are aliases.

```sQL
SELECT staffNo, fName, lName, position, salary 
FROM Staff 
WHERE salary > SOME (
	SELECT salary 
	FROM Staff 
	WHERE branchNo = 'B003'
)
```

This would fetch all staff members who have a salary greater than at least one staff member at the B003 branch.

This could also be achieved by
```sQL
SELECT staffNo, fName, lName, position, salary 
FROM Staff 
WHERE salary > (
	SELECT MIN(salary)
	FROM Staff 
	WHERE branchNo = 'B003'
)
```
Which checks of the salary is greater than the smallest salary at branch B003.

##### ALL Operator

```sQL
SELECT staffNo, fName, lName, position, salary 
FROM Staff 
WHERE salary > ALL (
	SELECT salary 
	FROM Staff 
	WHERE branchNo = 'B003'
)
```

This would fetch all staff members who have a salary greater than all the staff member at branch B003.

This could also be achieved by
```sQL
SELECT staffNo, fName, lName, position, salary 
FROM Staff 
WHERE salary > (
	SELECT MAX(salary)
	FROM Staff 
	WHERE branchNo = 'B003'
)
```
Which checks of the salary is greater than the largest salary at branch B003.

---
### INSERT Statement

Standard format is 
```sQL
INSERT INTO TableName [(columnList)]
VALUES (valueList)
```

The *columnList* is optional, but if not specified the values are enumerated in the order the table was created.

If specified, the omitted values are set to NULL, unless a DEFAULT operation was used at table creation.

If specified, the *valueList* must match one-to-one with the *columnList*.

```sQL
INSERT INTO Staff 
VALUES ('SG16', 'Alan', 'Brown', 'Assistant', 10000, 'B003')
```

```sQL
INSERT INTO Staff(staffNo, fName, lName, salary)
VALUES ('SG16', 'Alan', 'Brown', NULL, 10000, NULL)
```

---
### UPDATE Statement 

Standard format is
```sQL
UPDATE TableName
SET columnName = dataValue [, ...]
[WHERE condition]
```

The `WHERE` is optional, but only rows matching the condition are updated. Else, all rows are updated.

The `dataValue`s must be within the domain of the columns.

```sQL
UPDATE Staff 
SET salary = salary * 1.000001
```

```sQL
UPDATE Staff 
SET salary = salary * 1.05
WHERE position = 'Manager'
```

---
### DELETE Statement

Standard format is
```sQL
DELETE FROM TableName
[WHERE condition]
```

The `WHERE` is optional, but only rows matching the condition are deleted. Else, all rows are deleted.

```sQL
DELETE FROM Staff 
WHERE branchNo = 'B003'
```

```sQL
DELETE FROM Staff
```

---
### Data Definition Language (DDL)

Defining data in the database.

The main statements of interest in DDL 
- [[#CREATE Statement|CREATE]] - Create a new table and define its schema.
- [[#DROP Statement|DROP]] - Delete table.
- [[#ALTER Statement|ALTER]] - Change the relation schema.
- [[#CREATE VIEW Statement|CREATE VIEW]] - Define a view.

---
### CREATE Statement

We can create [[#Custom Domain Types]] using the CREATE statement.

##### CREATE TABLE 

Standard format 
```sQL
CREATE TABLE TableName(
	Attribute Domain [NOT NULL | UNIQUE | ...]
	[, ...]
	[integrity & referential constraints]
)
```

When we create tables we have many operators we can use.
- `PRIMARY KEY` and `FOREIGN KEY`: Integrity and Referential constraints
- `ON UPDATE`: what to do when the corresponding primary key is updated.
- `ON DELETE`: what to do when the corresponding primary key is deleted.
- `CASCADE`: when updates happen, update the foreign key. When deletions happen, delete the record.
- `SET NULL`: when updates or deletions happen, set the foreign key to `NULL`.
- `SET DEFAULT`: when updates or deletions happen, set the foreign key to the default value.
- `NO ACTION`: when updates or deletions happen, do nothing. Very dangerous!!!


```sQL
CREATE TABLE Person(
	name VARCHAR(30) NOT NULL UNIQUE,
	passport INTEGER,
	ssn INTEGER,
	age SHORTINT,
	gender GenderType,
	married BIT(1) DEFAULT 0,
	PRIMARY KEY (ssn),
	FOREIGN KEY (passport)
		REFERENCES PassportTable(id)
		ON DELETE SET NULL 
		ON UPDATE CASCADE
)
```

Here, `GenderType` is a [[#Custom Domain Types|Custom Domain Type]].

---
### DROP Statement 

Statement format 
```sQL
DROP TABLE TableName (CASCADE | RESTRICT)
```

In `CASCADE` mode, which is the default, the drop is forced and all dependent objects are dropped recursively.

In `RESTRICT` mode, the drop is rejected if there are other objects whose existence depends on the existence of *TableName*.

---
### ALTER Statement 

Used to change schema of a relation.

We can add new attributes.
```sQL
ALTER TABLE Person ADD salary INTEGER
```

We can remove attributes.
```sQL
ALTER TABLE Person DROP married CASCADE
```

We can change attribute characteristics.
```sQL
ALTER TABLE Person ALTER gender SET DEFAULT 'F'
```

---
### CREATE VIEW Statement

![[Relational Data Model#Views]]

Say we have a relation `Employee(id, name, department, project, salary)`.

```sQL
CREATE VIEW Developers AS
SELECT name, project 
FROM Employee 
WHERE department = 'Development'
```
This creates a view of all developers but hides the salary field.

```sQL
CREATE VIEW DurhamView AS
SELECT buyer, seller, product, shop 
FROM Person, Purchase
WHERE Purchase.buyer = Person.name AND 
	Person.city = 'Durham'
```
This creates a new virtual table of the purchases of people who live in Durham, `DurhamView(buyer, seller, product, shop)`

Views can be queried like other relations.
```sQL
SELECT name, shop 
FROM DurhamView, Product 
WHERE DurhamView.product = Product.name AND 
	Product.category = 'shoes'
```

Since views are computed on demand, they are slower. The queries on views get translated into the queries on the original tables.

##### Updating Views 

Say we have the relation `Employee(id, name, department, project, salary)`

```sQL
CREATE VIEW Developers AS 
SELECT name, project 
FROM Employee 
WHERE department = 'Development'
```
If we try to make insertions into this view 
```sQL
INSERT INTO Developers 
VALUES ('John', 'Project5')
```
This will fail as it will be translated into 
```sQL
INSERT INTO Employee 
VALUES (NULL, 'John', NULL, 'Project5', NULL)
```
And we cannot have a `NULL` primary key.

Take this new view
```sQL
CREATE VIEW Paying AS 
SELECT id, name, salary 
FROM Employee 
WHERE salary > 40000
```
Using this view, we can try inserting data.

```sQL
INSERT INTO Paying 
VALUES (82463, 'John', 43000)
```
This would be translated into 
```sQL
INSERT INTO Employee 
VALUES (82463, 'John', NULL, NULL, 43000)
```
This will work as we have a valid primary key.

---
### Additional Information

- [[Comp Sys Part 3 Lecture 7 SQL.pdf]]
