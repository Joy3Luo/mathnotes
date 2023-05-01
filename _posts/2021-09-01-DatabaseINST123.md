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



#### Exercises

from hackerrank.com

**CITY**

Field|Type
:--|:--
ID|NUMBER
NAME|VARCHAR2(17)
COUNTRYCODE|VARCHAR2(3)
DISTRICT|VARCHAR2(20)
POPULATION|NUMBER



1 Revising the Select Query I

Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.

```SQL
SELECT *
FROM CITY
WHERE CountryCode ='USA'
AND Population>100000;
```
```HTML
3878 Scottsdale USA Arizona 202705
3965 Corona USA California 124966
3973 Concord USA California 121780
3977 Cedar Rapids USA Iowa 120758
3982 Coral Springs USA Florida 117549
```

2 Revising the Select Query II

Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

```SQL
SELECT NAME
FROM CITY
WHERE CountryCode ='USA'
AND Population>120000;
```
```HTML
Scottsdale
Corona
Concord
Cedar Rapids
```

3 Select All

Query all columns (attributes) for every row in the CITY table.

```SQL
SELECT *
FROM city;
```
```HTML
6 Rotterdam NLD Zuid-Holland 593321
3878 Scottsdale USA Arizona 202705
3965 Corona USA California 124966
3973 Concord USA California 121780
3977 Cedar Rapids USA Iowa 120758
```

4 Select By ID

Query all columns for a city in CITY with the ID 1661.


```SQL
SELECT *
FROM city
WHERE id=1661;
```
```HTML
1661 Sayama JPN Saitama 162472
```

5 Japanese Cities' Names

Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.

```SQL
SELECT NAME
FROM CITY
WHERE CountryCode ='JPN';
```
```HTML
Neyagawa
Ageo
Sayama
Omuta
Tokuyama
```

------------------------------------------

**STATION**

Field|Type
---|---
ID|NUMBER
CITY|VARCHAR2(21)
STATE|VARCHAR2(2)
LAT_N|NUMBER
LONG_W|NUMBER

where LAT_N is the northern latitude and LONG_W is the western longitude.


6 Weather Observation Station 1

Query a list of CITY and STATE from the STATION table.

```SQL
SELECT city, state
FROM station;
```
```HTML
Acme LA
Addison MI
Agency MO
Aguanga CA
Alanson MI{-truncated-}
```

7 Weather Observation Station 3

Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.

```SQL
SELECT DISTINCT(city)
FROM station
WHERE MOD(id,2)=0;
```
```HTML
Aguanga
Alba
Albany
Amo
Andersonville {-truncated-}
```

8 Weather Observation Station 4

Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.

```SQL
SELECT COUNT(city)-COUNT(DISTINCT(city))
FROM station;
```
```HTML
13
```

9 Weather Observation Station 5

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

```SQL
WITH Longest AS (SELECT CITY, LENGTH(CITY) AS Lengths FROM STATION
                ORDER BY Lengths desc, City LIMIT 1),
     Shortest AS (SELECT CITY, LENGTH(CITY) AS Lengths FROM STATION
                ORDER BY Lengths, City LIMIT 1)
SELECT CITY, Lengths FROM Shortest
UNION
SELECT CITY, Lengths FROM Longest;
```
```HTML
Amo 3
Marine On Saint Croix 21
```

10 Weather Observation Station 6

Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

**SUBSTR: Extract a substring from a string (start at position 5, extract 3 characters)

```SQL
SELECT DISTINCT city
FROM station
WHERE SUBSTR(city, 1, 1) IN ('A', 'E' , 'I', 'O', 'U');
```

```HTML
Acme
Addison
Agency{-truncated-}
```

11 Weather Observation Station 7

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

```SQL
SELECT DISTINCT city
FROM station
WHERE SUBSTR(city, -1) IN ('A', 'E' , 'I', 'O', 'U');
```
```HTML
Acme
Aguanga
Alba
Aliso Viejo
Alpine
Amazonia{-truncated-}
```

12 Weather Observation Station 8

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

```SQL
SELECT DISTINCT city
FROM station
WHERE SUBSTR(city, 1, 1) IN ('A', 'E' , 'I', 'O', 'U')
AND SUBSTR(city, -1) IN ('A', 'E' , 'I', 'O', 'U');
```
```HTML
Acme
Aguanga
Alba
Aliso Viejo
Alpine{-truncated-}
```

13 Weather Observation Station 9

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

```SQL
SELECT DISTINCT city
FROM station
WHERE SUBSTR(city, 1, 1) NOT IN ('A', 'E' , 'I', 'O', 'U');
```
```HTML
Baileyville
Bainbridge
Baker
Baldwin{-truncated-}
```

14 Weather Observation Station 10

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

```SQL
SELECT DISTINCT city
FROM station
WHERE SUBSTR(city, -1) NOT IN ('A', 'E' , 'I', 'O', 'U');
```
```HTML
Addison
Agency
Alanson
Albany{-truncated-}
```

15 Weather Observation Station 11

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

```SQL
SELECT DISTINCT city
FROM station
WHERE SUBSTR(city, 1, 1) NOT IN ('A', 'E' , 'I', 'O', 'U')
OR SUBSTR(city, -1) NOT IN ('A', 'E' , 'I', 'O', 'U');
```
```HTML
Addison
Agency
Alanson
Albany{-truncated-}
```

16 Weather Observation Station 12

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

```SQL
SELECT DISTINCT city
FROM station
WHERE SUBSTR(city, 1, 1) NOT IN ('A', 'E' , 'I', 'O', 'U')
AND SUBSTR(city, -1) NOT IN ('A', 'E' , 'I', 'O', 'U');
```
```HTML
Baker
Baldwin
Bass Harbor
Beaufort{-truncated-}
```

------------------------------------------

**Employee**

Column|Type
---|---
EMPLOYEE_ID|INTEGER
NAME|STRING
MONTHS|INTEGER
SALARY|INTEGER


where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is their monthly salary.

17 Employee Names

Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

```SQL
SELECT NAME
FROM Employee
ORDER BY NAME ASC;
```
```HTML
Alan
Amy
Andrew
Andrew
Angela{-truncated-}
```

18 Employee Salaries

Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than 2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.

```SQL
SELECT NAME
FROM Employee
WHERE SALARY > 2000 AND MONTHS < 10
ORDER BY EMPLOYEE_ID ASC;
```
```HTML
Rose
Patrick
Lisa
Amy
Pamela{-truncated-}
```

------------------------------------------

**TRIANGLES**

Column|Type
---|---
A|INTEGER
B|INTEGER
C|INTEGER

19 Type of Triangle

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with 3 sides of equal length.

Isosceles: It's a triangle with 2 sides of equal length.

Scalene: It's a triangle with 3 sides of differing lengths.

Not A Triangle: The given values of A, B, and C don't form a triangle.

```SQL
SELECT
    CASE
        WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
        WHEN A = B AND B = C THEN 'Equilateral'
        WHEN A = B OR A = C OR B = C THEN 'Isosceles'
        ELSE 'Scalene'
    END as TriangleType
FROM TRIANGLES;
```
```HTML
Equilateral
Equilateral
Isosceles
Equilateral
Isosceles
Equilateral
Scalene
Not A Triangle
Scalene
Scalene
Scalene
Not A Triangle
Not A Triangle
Scalene
Equilateral
```

------------------------------------------

**OCCUPATIONS**

Column|Type
---|---
NAME|STRING
OCCUPATION|STRING

Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.

20 The PADS

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).

And

Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

```HTML
There are a total of [occupation_count] [occupation]s.
```

where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

** concat: Add two strings together

```SQL
select concat(name,'(', upper(substr(occupation,1,1)),')') as name
from OCCUPATIONS
union select concat('There are a total of',' ',count(*),' ',lower(occupation),'s.') as name
from OCCUPATIONS
group by occupation
order by name
```
```HTML
Aamina(D)
Ashley(P)
Belvet(P)
Britney(P)
Christeen(S)
Eve(A)
Jane(S)
Jennifer(A)
Jenny(S)
Julia(D)
Ketty(A)
Kristeen(S)
Maria(P)
Meera(P)
Naomi(P)
Priya(D)
Priyanka(P)
Samantha(A)
There are a total of 3 doctors.
There are a total of 4 actors. {-truncated-}
```

21 Occupations

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

Note: Print NULL when there are no more names corresponding to an occupation.


```SQL
select
    min(if(occupation = 'Doctor',name,null)) as Doctor,
    min(if(occupation = 'Professor',name,null)) as Professor,
    min(if(occupation = 'Singer',name,null)) as Singer,
    min(if(occupation = 'Actor',name,null)) as Actor
from
(select name,occupation,Row_number() Over (partition by occupation order by name) as row_num from occupations) as ord group by row_num;
```
```HTML
Aamina Ashley Christeen Eve
Julia Belvet Jane Jennifer
Priya Britney Jenny Ketty
NULL Maria Kristeen Samantha
NULL Meera NULL NULL
NULL Naomi NULL NULL
NULL Priyanka NULL NULL
```

------------------------------------------

**BST**

Column|Type
---|---
N|INTEGER
P|INTEGER

You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

22 Binary Tree Nodes

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

Root: If node is root node.

Leaf: If node is leaf node.

Inner: If node is neither root nor leaf node.


```SQL
select N,
    case
        when P is null then 'Root'
        when N in (select distinct P from BST) then 'Inner'
        else 'Leaf'
    end
from BST
order by 1
```
```HTML
1 Leaf
2 Inner
3 Leaf
4 Inner
5 Leaf
```

Example:

```SQL
SELECT Customers.customer_id, Customers.first_name, Orders.amount
FROM Customers
LEFT JOIN Orders
ON Customers.customer_id = Orders.customer
WHERE Orders.amount >= 500;
```




23 New Companies

Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.


```SQL
select
    e.company_code,
    max(founder),
    count(distinct lead_manager_code),
    count(distinct senior_manager_code),
    count(distinct manager_code),
    count(distinct employee_code)
from employee e
left join company c
on e.company_code = c.company_code
group by e.company_code
order by e.company_code
```
```HTML
C1 Angela 1 2 5 13
C10 Earl 1 1 2 3
C100 Aaron 1 2 4 10
C11 Robert 1 1 1 1
C12 Amy 1 2 6 14
```

24 Weather Observation Station 19

Consider P1(a,c) and P2(b,d) to be two points on a 2D plane where (a,b) are the respective minimum and maximum values of Northern Latitude (LAT_N) and (c,d) are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION.

Query the Euclidean Distance between points p1 and p2 and format your answer to display 4 decimal digits.

```SQL
SELECT ROUND(SQRT(POWER((MAX(Lat_N) - MIN(Lat_N)), 2) +POWER((MAX(Long_W) - MIN(Long_W)), 2)), 4)
FROM Station;
```
```HTML
184.1616
```
