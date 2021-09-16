---
layout: post
title: Data- Database
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

What is an entity?
An object about which data is captured in a database, such as "student"
All of the information about a category, such as student information, is an entity
A row of information, such as that about Abril Davis, is an instance of an entity
