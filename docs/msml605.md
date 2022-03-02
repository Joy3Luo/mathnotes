Computing Systems for Machine Learning

Chapter 1 Introduction


### Chapter 2 Python Fundamentals


#### Syntax

##### hello. py

Python does not have a main method like Java
-The program's main code is just written directly in the file
Python statements do not end with semicolons

```py
print("Hello, world!")
```

##### Multi-Line Statements

Statements in Python typically end with a new line. Python does, however, allow the use of the line continuation character (\\) to denote that the line should continue. For example:

```py
total = item_one + \
        item_two + \
        item_three
```
Statements contained within the [], {}, or () brackets do not need to use the line continuation character. For example:

```py
days = ['Monday', 'Tuesday', 'Wednesday',
                'Thursday', 'Friday']
```

##### Quotation in Python

Python accepts single ('), double (") and triple (''' or """) quotes to denote string literals, as long as the same type of quote starts and ends the string

The triple quotes can be used to span the string across multiple lines. For example, all the following are legal:

```py
word = 'word'
sentence = "This is a sentence."
paragraph = """This is a paragraph. It is made up
  of multiple lines and sentences."""
```

##### Comments

As programs get bigger and more complicated, they become more difficult to read
It is a good idea to add notes to your programs
A # symbol that is not inside a string starts a comment
All characters after the # and up to the physical line end are part of the comment
Python interpreter ignores them


##### Using Blank Lines

A line containing only whitespace, possibly with a comment, is known as a blank line, and is ignored by the Python interpreter

In an interactive interpreter session, you must enter an empty physical line to terminate a multiline statement


##### Multiple Statements on a Single Line

The semicolon ( ; ) allows multiple statements on the single line given that neither statement starts a new code block. Here is a sample snip using the semicolon:

```py
import sys; x = 'foo'
```

##### Multiple Statement Groups as Suites

Groups of individual statements making up a single code block are called suites in Python
Compound or complex statements, such as if, while, def, and class, are those which require a header line and a suite
Header lines begin the statement (with the keyword) and terminate with a colon ( : ) and are followed by one or more lines which make up the suite

```py
if expression1 :
suite1
elif expression2 :
  suite2
else :
  suite3
```

##### Suites and Indentation

One of the first caveats programmers encounter when learning Python is that there are no braces to indicate blocks of code for class and function definitions or flow control. Blocks of code are denoted by line indentation, which is rigidly enforced

The number of spaces in the indentation is variable, but all statements within the block must be indented the same amount

```
if x == True:
  print ("Answer”)
  print ("True”)
else:
  print ("Answer”)
  print ("False”)
```

##### Reserved Words

Keywords contain lowercase letters only
```
and exec not
assert finally or
break for pass
class from print
continue global raise
def if return
del import try
elif in while
else is with
except lambda yield
```

#### Variables and Expressions

##### Variable Name

Variable names can be both letters and numbers
They have to begin with a letter though
Uppercase letters are allowed, generally we use lowercase
Underscore character (_) can also appear in a name
Variable name cannot be a keyword
An illegal name results in a syntax error


##### Assigning Values to Variables

Python variables do not have to be explicitly declared to reserve memory space
The declaration happens automatically when you assign a value to a variable. The equal sign (=) is used to assign values to variables

```py
counter = 100  # An int assignment
miles = 1000.0 # A float
name = "John"  # A str
print (counter)
print (miles)
print (name)
```

##### Constants

Python doesn't really have constants
Instead, declare a "global" variable at the top of your code
All methods will be able to use this value

```py
MAX_VALUE = 3
```

##### Multiple Assignments

You can also assign a single value to several variables
simultaneously

```py
a = b = c = 1
a, b, c = 1, 2, "john"
```

##### Data Types

Number types
 int
 float
 complex

Sequence type
 str (immutable)
 list
 tuple (immutable)
 range
 zip (sequence of tuples)

Boolean type
 bool

Set type
 set
 frozenset

Mapping type
 dict

Binary type
 bytes
 bytearray
 memoryview

##### Data Types: Java vs Python

Python is looser about types than Java
Variables' types do not need to be declared
Variable can change type as a program is running
If the variable value is set to a value of a different type

```py
a = 1       # integer type
a = "john"  # string type
```

##### Expressions and Statements

An expression is a combination of values, variables, and operators
A value or variable all by itself is also an expression
```py
Examples
21
x
x+21
```

A statement is a unit of code that a Python interpreter can
execute, for example,
 print
 assignment

##### Operators and Operands

Operators represent computations like addition, multiplication, division, etc.
\+  -  *  /  %  **

The values the operator is applied to are called operands

```py
>>> 1 + 1
2
>>> 1 + 3 * 4 - 2
11
>>> 7 / 2
3
>>> 7.0 / 2
3.5
>>> 10 ** 6
1000000
```

##### Modulus Operator

Works on integers
Yields the remainder of the first operand divided by the second
Indicated by %
 Quotient = 7 // 3
 Remainder = 7 % 3

Utility: find the last digits of a number
```py
>>> 97856 % 100
56
```

##### Order of Operations

When multiple operators appear in an expression, the order of evaluation depends on the rules of precedence
Multiplication and division have the same precedence; addition and subtraction have the same precedence
Operators with the same precedence are evaluated from left to right (except exponentiation which has right-to-left precedence)

##### Operators: Java vs Python

No ++ or -- operators (must manually adjust by 1)

Java
```Java
nt x = 2;
x++;
System.out.println(x);
x = x * 8;
System.out.println(x);
double d = 3.2;
d = d / 2;
System.out.println(d);
```

Python
```py
x = 2
x = x + 1
print(x)
x = x * 8
print(x)
d = 3.2
d = d / 2
print(d)
```

##### str Data Type

Strings in Python are identified as a contiguous set of characters in between quotation marks
Python allows for either pairs of single or double quotes. Subsets of strings can be taken using the slice operator ( [ ] and [ : ] ) with indexes starting at 0 in the beginning of the string and working their way from -1 at the end
The plus ( + ) sign is the string concatenation operator, and the asterisk (*) is the repetition operator

```py
str1 = 'Hello World!'
print str1 # Prints complete string
print str1[0] # Prints first character of the string
print str1[2:5] # Prints characters starting from 3rd to 6th
print str1[2:] # Prints string starting from 3rd character
print str1 * 2 # Prints string two times
print str1 + "TEST" # Prints concatenated string

Output:
Hello World!
H
llo
llo World!
Hello World!Hello World!
Hello World!TEST
```

##### String Operations

You can’t perform mathematical operations on strings

Examples
 ‘2’ - ’1’
 ‘eggs’ / ‘dozens’

The + operator works with strings and performs
concatenations

```py
first = 'hello'
second = 'class'
print(first + second)

Output:
helloclass
```

##### String Multiplication

The * operator works with strings and performs repetition
Examples
 ‘Spam’*3 is ‘SpamSpamSpam’
If one of the operands is a string, the other has to be an integer
```py
>>> "hello" * 3
"hellohellohello"
>>> print(10 * "yo ")
yo yo yo yo yo yo yo yo yo yo
>>> print(2 * 3 * "4")
444444
```

##### String Concatenation

Integers and strings cannot be concatenated in Python
str(value) - converts a value into a string
print(expr, expr)  - prints two items on the same line

```py
>>> x = 4
>>> print("Thou shalt not count to " + x + ".")
TypeError: cannot concatenate 'str' and 'int' objects
>>> print("Thou shalt not count to " + str(x) + ".")
Thou shalt not count to 4.
>>> print(x + 1, "is out of the question.")
5 is out of the question.
```

##### list Data Type

Lists are the most versatile of Python's compound data types. A list contains items separated by commas and enclosed within square brackets ([])
To some extent, lists are similar to arrays in C. One difference between them is that all the items belonging to a list can be of different data type


```py

```

#####



```py

```

#####



```py

```

#####



```py

```

#####



```py

```

#####



```py

```

#####



```py

```

#####



```py

```

#####



```py

```

#####



```py

```
