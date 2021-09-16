---
layout: post
title: Data - Database
date: 2021-09-01 12:18 +0800
tags: [Data]
toc:  true
---

<!-- Global site tag (gtag.js) - Google Analytics -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-TG0XJZG53F"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    gtag('config', 'G-TG0XJZG53F');
  </script>

### Creating Your First Database
#### Database Structure

The primary object for containing and organizing data and relationships between data in a relational database is the **TABLE**.

TABLE:
- Columns – each column contains data about a particular attribute that is of a specific data type; (i.e., characters, dates, numbers).
- Rows – contains specific values for each of the columns in the table.

A single database can contain one table, dozens of tables, or in the case of the FAAs air traffic tracking system – hundreds of tables.

#### Tables
Tables can give us clues about the content and purpose of a database.

Example:

`student_enrollment` table
```
student_id	class_id	class_section   semester       
----------- 	---------	--------------	----------
CHRISPA004	COMPSCI101	3		Fall 2017
DAVISHE010	COMPSCI101 	3	        Fall 2017
ABRILDA002	ENG101		40		Fall 2017
DAVISHE010	ENG101		40      	Fall 2017
RILEYPH002	ENG101		40	        Fall 2017
```

A `students` table
```
student_id	first_name	last_name	dob       
-----------	-----------	----------	----------
ABRILDA002	Abril		Davis		1999-01-10
CHRISPA004	Chris		Park		1996-04-10
DAVISHE010	Davis		Hernandez	1987-09-14
RILEYPH002	Riley		Phelps		1996-06-15
```

`student_id` is the primary key column that identifies each row of data uniquely.

#### Databases

What is an **entity**?
- An object about which data is captured in a database, such as "student"
- All of the information about a category, such as student information, is an **entity**
- A row of information, such as that about Abril Davis, is an **instance** of an entity

What are the main entities of an enrollments database?
- Students
- Classes
- Sections
- Instructors
- Location

Conceptual	Physical   [Logical]

Entity		🡪  Table 🡪   [Relation]

Instance	🡪  Row* 	🡪   [Tuple]

Attribute	🡪  Column	🡪  [Attribute]

#### Creating a Database on the RDBMS

PostgreSQL is a database management system or DBMS.

In the case of relational databases such as PostgreSQL, MySQL, Oracle, SQL Server, they are relational database management systems or RDBMS.

An RDBMS can contain and manage many databases, each of which can contain at least 1 table and up to hundreds of tables.

The new database `analysis`
```
CREATE DATABASE analysis;
```

This command contains two keywords: `CREATE` and `DATABASE`

SQL commands end with the punctuation – the semi-colon `;`
The semi-colon ***is not*** required at the end of every command

#### Creating a Table

- A table is where all of the data in a database lives.
- Tables are also where we define the relationships between different data in the database (e.g., students to classes, instructors to classes, etc.)
- When you create a table you define and describe all of the columns (attributes or fields) in the table. Each column must have
    - A name
    - A data type (e.g., text, integer, decimal, date)

To create a `teachers` table in the `analysis` database

➊ CREATE TABLE teachers (		

    ➋ id bigserial,

    ➌ first_name varchar(25),

       last_name varchar(50),

       school varchar(50),

    ➍ hire_date date,

    ➎ salary numeric

➏ );

➊ keywords CREATE and TABLE: Comma separated list of column names and data types in parentheses.

➋ bigserial: a datatype that autoincrements when a new row is created. This is our primary key.

➌ columns for teacher name and school are  data type varchar. The number in () is the max length.

➍ & ➎ are columns with date and numeric data types.

➏ We close the command with ;

#### Populating a Table
We can add data to tables in multiple ways:
- Importing large amounts of data from a text file or other database
- Using the `INSERT INTO` command
- Using an interface application to insert new rows

#### Inserting Data into the Teachers Table

➊ INSERT INTO teachers (first_name, last_name, school, 			hire_date, salary)

➋ VALUES ('Janet', 'Smith', 'F.D. Roosevelt HS', '2011-10-30', 36200),

         ('Lee', 'Reynolds', 'F.D. Roosevelt HS', '1993-05-22', 65000),

         ('Samuel', 'Cole', 'Myers Middle School', '2005-08-01', 43500),

         ('Samantha', 'Bush', 'Myers Middle School', '2011-10-30', 36200),

         ('Betty', 'Diaz', 'Myers Middle School', '2005-08-30', 43500),

         ('Kathleen', 'Roush', 'F.D. Roosevelt HS', '2010-10-22', 38500); ➌

➊ keywords INSERT and INTO identify the table into which the data will be put

➋ keyword VALUES identifies the data to be inserted.

➌ The command is terminated with the ;

#### What happens when things go wrong?
Computers do EXACTLY what they are told to do!
- This is true whether what we told them is what we meant or not.
- Computers are literal and unforgiving of our mistakes.
- Hence, the error message.
  - Computer, language, and software developers attempt to help computers communicate what we humans have done wrong.
``` plaintext
ERROR:  syntax error at or near "("
LINE 5:     ('Samuel', 'Cole', 'Myers Middle School', '2005-08-01', 43...
            ^
********** Error **********
```
- Sometimes error messages are clear, other times not.

#### Formatting SQL for Readability
- SQL requires no special formatting to run
- SQL is not case-sensitive, (except some configurations)
  - INSERT = Insert = insert = InSeRt
- Indentation is not required
- However, there are some "good practice" principles"
  - Uppercase SQL keywords, such as SELECT
  - Uppercase data type names, such as TEXT and INTEGER (Less strict)
  - `lowercase_and_underscores` for object names, such as tables and columns
  - Indent clauses and code blocks using either spaces or tabs

### Data Exploration with SELECT

`SELECT * FROM teachers;`

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%201.png)

Querying a Subset of Columns

```
SELECT last_name, first_name, salary 	
  FROM teachers;
```

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%202.png)

Using DISTINCT to Find Unique Values

```
SELECT DISTINCT school
  FROM teachers;
```

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%203.png)

Using DISTINCT on Multiple Columns
```
SELECT DISTINCT school, salary
  FROM teachers;
```
![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%204.png)

Sorting Data with ORDER BY

```
SELECT first_name, last_name, salary
  FROM teachers
  ORDER BY salary DESC;
```

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%205.png)

ORDER BY with Multiple Columns

```
SELECT last_name, school, hire_date
  FROM teachers
  ORDER BY school ASC, hire_date DESC;
```

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%206.png)

Filtering Rows with WHERE

```
SELECT last_name, school, hire_date
  FROM teachers
  WHERE school = 'Myers Middle School';
```

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%207.png)

Comparison and Matching Operators in PostgreSQL

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%208.png)

#### More Examples with WHERE

```
SELECT first_name, last_name, school
  FROM teachers
  WHERE first_name = 'Janet';

SELECT school
  FROM teachers
  WHERE school != 'F.D. Roosevelt HS';

SELECT first_name, last_name, hire_date
  FROM teachers
  WHERE hire_date < '2000-01-01';

SELECT first_name, last_name, salary
  FROM teachers
  WHERE salary >= 43500;

SELECT first_name, last_name, school, salary
  FROM teachers
  WHERE salary BETWEEN 40000 AND 65000;
```

#### Using LIKE and ILIKE with WHERE

- Percent sign (%) A wildcard matching one or more characters

- Underscore (_) A wildcard matching just one character

LIKE patterns that will match : baker
```
LIKE 'b%'
LIKE '%ak%'
LIKE '_aker'
LIKE 'ba_er'
```

LIKE patterns that will NOT match : baker
```
LIKE 'b_'
LIKE 'ak%'
LIKE '_ker'
LIKE '%ake'
```

The ILIKE operator
```
SELECT first_name
  FROM teachers
  WHERE first_name LIKE 'sam%';

SELECT first_name
  FROM teachers
  WHERE first_name ILIKE 'sam%';
```

#### Examples with AND and OR
```
SELECT * FROM teachers
  WHERE school = 'Myers Middle School'
    AND salary < 40000;

SELECT * FROM teachers
  WHERE last_name = 'Cole'
    OR last_name = 'Bush';

SELECT * FROM teachers
  WHERE school = 'F.D. Roosevelt HS'
  AND
  (salary < 38000 OR salary > 40000);
```

#### Putting It All Together
General syntax:

SELECT column_names

  FROM table_name

  WHERE criteria

  ORDER BY column_names;


Example:
```
SELECT first_name, last_name,
        school, hire_date, salary
  FROM teachers
  WHERE school LIKE '%Roos%'
  ORDER BY hire_date DESC;
```

![](https://joy3luo.github.io/mathnotes/pics/databaseinst123/ch2%209.png)
