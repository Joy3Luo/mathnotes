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

```py
if x == True:
  print ("Answer")
  print ("True")
else:
  print ("Answer")
  print ("False")
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
The values stored in a list can be accessed using the slice operator ( [ ] and [ : ] ) with indexes starting at 0 in the beginning of the list and working their way to end-1
The plus ( + ) sign is the list concatenation operator, and the asterisk
( * ) is the repetition operator

```py
list = [ 'abcd', 786 , 2.23, 'john', 70.2 ]
tinylist = [123, 'john']

print list          # Prints complete list
print list[0]       # Prints first element of the list
print list[1:3]     # Prints elements starting from 2nd till 3rd
print list[2:]      # Prints elements starting from 3rd element
print tinylist * 2  # Prints list two times
print list + tinylist # Prints concatenated lists
Output:
['abcd', 786, 2.23, 'john', 70.2]
abcd
[786, 2.23]
[2.23, 'john', 70.2]
[123, 'john', 123, 'john']
['abcd', 786, 2.23, 'john', 70.2, 123, 'john']
```

##### tuple Data Type

A tuple is another sequence data type that is similar to the list. A tuple consists of a number of values separated by commas. Unlike lists, however, tuples are enclosed within parentheses

The main differences between lists and tuples are: Lists are enclosed in brackets ( [ ] ), and their elements and size can be changed, while tuples are enclosed in parentheses ( ( ) ) and cannot be updated. Tuples can be thought of as read-only lists

```py
tuple = ( 'abcd', 786 , 2.23, 'john', 70.2  )
tinytuple = (123, 'john')

print(tuple)        # Prints complete list
print(tuple[0])        # Prints first element of the list
print(tuple[1:3])     # Prints elements starting from 2nd till 3rd
print tuple[2:]       # Prints elements starting from 3rd element
print tinytuple * 2   # Prints list two times
print tuple + tinytuple # Prints concatenated lists


OUTPUT:
('abcd', 786, 2.23, 'john', 70.2)
abcd
(786, 2.23)
(2.23, 'john', 70.2)
(123, 'john', 123, 'john')
('abcd', 786, 2.23, 'john', 70.2, 123, 'john')
```

##### dict Data Type

Python 's dictionaries are hash table type. They work like associative arrays or hashes found in Perl and consist of key-value pairs
Keys can be almost any Python type, but are usually numbers or strings. Values, on the other hand, can be any arbitrary Python object
Dictionaries are enclosed by curly braces ( { } ) and values can be assigned and accessed using square braces ( [] )

```py
dict = {}
dict['one'] = "This is one"
dict[2]     = "This is two“
tinydict = {'name': 'john','code':6734, 'dept': 'sales'}
print(dict['one'])      # Prints value for 'one' key
print (dict[2])          # Prints value for 2 key
print (tinydict)         # Prints complete dictionary
print (tinydict.keys())  # Prints all the keys
print (tinydict.values()) # Prints all the values

OUTPUT:
This is one
This is two
{'dept': 'sales', 'code': 6734, 'name': 'john'}
['dept', 'code', 'name']
['sales', 6734, 'john']
```

##### Data Type Conversion

```py
Function Description
int(x [,base]) Converts x to an integer. base specifies the base if x is a string
long(x [,base] ) Converts x to a long integer. base specifies the base if x is a string
float(x) Converts x to a floating-point number
complex(real [,imag]) Creates a complex number
str(x) Converts object x to a string representation
repr(x) Converts object x to an expression string
eval(str) Evaluates a string and returns an object
tuple(s) Converts s to a tuple
list(s) Converts s to a list
set(s) Converts s to a set
dict(d) Creates a dictionary. d must be a sequence of (key,value) tuples
frozenset(s) Converts s to a frozen set
chr(x) Converts an integer to a character
unichr(x) Converts an integer to a Unicode character
ord(x) Converts a single character to its integer value
hex(x) Converts an integer to a hexadecimal string
oct(x) Converts an integer to an octal string
```

#### Conditionals

##### Boolean Expressions

A boolean expression is an expression that is either true or false
It uses the operator '=\=', which compares the operands to the left and the right of this operator
It produces either True or False
 for example, 5=\=5 will return True
 and 5==6 will return False

True and False are of type bool

 x != y # x is not equal to y
 x > y # x is greater than y
 x < y # x is less than y
 x >= y # x is greater than or equal to y
 X <= y # x is less than or equal to y

##### Logical Operators

Three logical operators: and, or, and not. For example:
 x > 0 and x < 10
 This is true only if x is greater than 0 and less than 10
 n%2 == 0 or  n%3 == 0 is true if either of the conditions is
true, that is, if the number is divisible by 2 or 3
 The not operator negates a boolean expression, so not(x > y)
is true if x > y is false, that is, if x is less than or equal to y

##### Conditional Execution

We need to check conditions and change the behavior of the program
The simplest conditional statement is if, for example:

The Boolean expression after ‘if’ is called the condition
```py
if x>0:
  print('x is positive')

OUTPUT:
x is positive
```

##### if Statement

if statements have a header followed by an indented body
Statements like these are called compound statements
There is no limit on the number of statements that can appear in the body, but there must be at least one
Sometimes it is useful to have a body with no statements, usually as a place holder
In that case use the pass statement, which does nothing

```py
if x < 0: pass  # need to handle negative values
```

##### Alternative Execution

When there are two possibilities and the condition determines which one gets executed
The alternatives are called branches, because they are branches in the flow of execution

```py
if x%2 == 0:
  print('x is even')
else:
  print('x is odd')
```

##### Chained Conditionals

Sometimes there are more than two possibilities and we need more than two branches

One way to express a computation like that is a chained conditional:
elif is an abbreviation of “else if”

```py
if(x <y):
  print('x is less than y')
elif(x>y):
  print('x is greater than y')
else:
  print('x and y are equal')
```

There is no limit to the number of elif statements
If there is an else clause, it must be at the end
Each condition is checked in order. If the first one is false, the next is checked, and so on

We don’t need an else statement:

```py
if choice == 'a':
  draw_a()
elif choice == 'b':
  draw_b()
elif choice == 'c':
  draw_c()
```

#### Functions

##### Function

A function is some reusable code that
• takes arguments(s) as input
• does some computation and
• returns a result or results

There are two kinds of functions in Python
• Built-in functions that are provided as part of Python - raw_input(), type(), float(), int() ...
• Functions that we define ourselves and then use

We treat the built-in function names as "new" reserved words (i.e., we avoid them as variable names)

##### A Built-in Function: max()

A built-in function is some stored code that we use. It takes some input and produces an output.

```py
>>> big = max('Hello world')
>>> print big
'w'
```

##### Type Conversion Functions

There are built-in functions in Python that convert from one data type to another

 The int() function takes any value and converts it into an integer, if it can
 int() can convert floating-point values to integers, but it doesn’t round off, and instead chops off the fraction part
 float() converts integers and strings to floating-point numbers
 str() converts its arguments to string

##### Math Functions

Python has a math module that provides mathematical functions
Before using the module, it needs to be imported `import math`
This module contains the functions and variables defined in the module
To access one of the functions, you have to specify the name of the module and the name of the function

##### Import
Python provides 2 ways to import modules
 We have already seen  import math
 import statement imports all the functions from a module into the code

We can also import functions using  from
 Imports only the specified function
 Syntax
  from [module] import [function or value]
  from random import choice

##### Counting and Iterating Functions


len: returns the number of items of an enumerable object
```py
>>> len( [‘c’, ‘m’, ‘s’, ‘c’, 3, 2, 0] )
7
```
range: returns an iterable object
```py
>>> list( range(10) )
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
enumerate: returns iterable tuple (index, element) of a list
```py
>>> enumerate( [“311”, “320”, “330”] )
[(0, “311”), (1, “320”), (2, “330”)]
```
map: apply a function to a sequence or iterable
```py
>>>arr = [1, 2, 3, 4, 5]
>>>map(lambda x: x**2, arr)
[1, 4, 9, 16, 25]
```

```py
>>> map(lambda x, y: x + y, [1, 3, 5, 7, 9], [2, 4, 6, 8, 10])
[3, 7, 11, 15, 19]
```
filter: returns a list of elements for which a predicate is true
```py
>>>arr = [1, 2, 3, 4, 5, 6, 7]
>>> filter(lambda x: x % 2 == 0, arr)
[2, 4, 6]
```

##### User-Defined Functions

A named sequence of statements that perform a certain computation
After defining a function, you can call it by name
 Example: type(34)

Why Define & Use Functions?
 A group of statements gets a name
 Modular code
 Easier debugging
 Code reuse

```py
# Prints a helpful message.
def hello():
  print("Hello, world!")
# main (calls hello twice)

hello()
hello()
```
Must be declared above the 'main' code
Statements inside the function must be indented

##### Whitespace Significance

Python uses indentation to indicate blocks, instead of {}
 Makes the code simpler and more readable
 In Java, indenting is optional.  In Python, you must indent

```py
# Prints a helpful message.
def hello():
  print("Hello, world!")
# main (calls hello twice)

hello()
hello()
```

##### Arguments, Parameters, Variables

Most functions require arguments
 E.g.: math functions

An expression can also be used as an argument

Inside the function, arguments are assigned to variables called parameters
 Parameters are local to the function
Some functions return a value and others return nothing (void)
A variable created inside a function is local

```py
def summation(x,y):
  z = x + y
  return(z)

print(summation(2,4))

m = summation(2,4)
print(m)
```

```py
def decide(x,y):
  if x=='green’ and y=='Red’:  
    print("You can go!")

y = 'Red'
y = 'green'
y = 'green'
z = 'Red'

decide(z,y)
```

#### Iterations

##### Iterations

Involves repetition
A statement or group of statements that need to be repeated
Help in automation of repeated tasks

##### The for Loop

Uses an iterator (name) and repeats for values 0 (inclusive) to max (exclusive)

```py
for name in range(max):
    statements
```

```py
>>> for i in range(5):
...     print(i)
0
1
2
3
4
```

##### for Loop Variations

Can specify a min other than 0, and a step other than 1

```py
for name in range(min, max):
    statements

for name in range(min, max, step):
    statements
```

```py
>>> for i in range(2, 6):
...     print(i)
2
3
4
5
>>> for i in range(15, 0, -5):
...     print(i)
15
10
5
```

##### Nested Loops

Nested loops are often replaced by string * and +

```py
for line in range(1, 6):
  print((5 - line) * "." + str(line))

output:
....1
...2
..3
.4
5
```

```py
def bar():
  print "#" + 16 * "=" + "#"
def top():
  for line in range(1, 5):        # split a long line by ending it with \     
    print("|" + (-2 * line + 8) * " " + \             
         "<>" + (4 * line - 4) * "." + "<>" + \              
         (-2 * line + 8) * " " + "|")
def bottom():    
  for line in range(4, 0, -1):        
    print("|" + (-2 * line + 8) * " " + \              
         "<>" + (4 * line - 4) * "." + "<>" + \              
         (-2 * line + 8) * " " + "|")

# main
bar()
top()
bottom()
bar()

```
```
output:
#================#
|      <><>      |
|    <>....<>    |
|  <>........<>  |
|<>............<>|
|<>............<>|
|  <>........<>  |
|    <>....<>    |
|      <><>      |
#================#
```

##### Concatenating Ranges

Ranges can be concatenated with +
 Can be used to loop over a disjoint range of numbers

```py
>>> range(1, 5) + range(10, 15)
[1, 2, 3, 4, 10, 11, 12, 13, 14]

>>> for i in range(4) + range(10, 7, -1):
...     print(i)
0
1
2
3
10
9
8
```

##### while Loop

In the definition there is no starting iterator
We need to use a condition with the while

It requires a condition, e.g.,
```py
n = 12
while(n >0):
  print(n)
  n = n - 1
```

##### Execution Flow for a while Loop

At the start of each iteration, evaluate the condition, yielding True or False
If the condition is false, exit the while statement and continue execution at the next statement
If the condition is true, execute the body and then go to the condition again
The body of the loop will change the value of one or more variables so that condition eventually becomes false and the loop terminates

##### break Statement

Sometimes we want to break out of a loop if some
condition is satisfied

```py
n = 12
while(n >0):
  print(n)
  n = n - 1
  if n == 7:
    break

output:
12
11
10
9
8
```

Chapter 3 Python Advanced

#### Strings

##### String

A sequence type
A sequence of zero or more characters
  course = “MSML 605”

A string is delimited (begins and ends) by single or double quotes
The empty string has zero characters ('' or "")

```py
poem = 'Ode to a Nightingale'
lyric = "Roll on, Columbia, roll on"
exclamation = "That makes me !#? "
```

Quote Characters in Strings

 You can include a single quote in a double quoted string or a double quote in a single quoted string
```py
will = "All the world's a stage"
ben = 'BF: "A penny saved is a penny earned"'
```

 To put a single quote in a single quoted string, precede it with the backslash ('\\') or 'escape' character.  

```py
>>> will = 'All the world\'s a stage'
>>> print(will)
All the world's a stage
```

 The same goes for double quotes
```py
>>> ben = "BF: \"A penny saved is a penny earned\""
>>> print(ben)
BF: "A penny saved is a penny earned"
```

Putting a Format Character in a String

 A format character is interpreted by the print() function to change the layout of text
 To put a format character in a string, precede it with the
backslash ('\')
 A newline is represented by '\n'  

```py
>>> juliette = 'Good night, good night\nParting is such sweet sorrow'
>>> print(juliette)
Good night, good night
Parting is such sweet sorrow
```

 A tab is represented by '\t'
```py
>>> tabs = 'col0\tcol1\tcol2'
>>> print(tabs)
col0 col1 col2
```

##### Bracket operator and Index

You can access the characters one at a time with the bracket operator
The first character has index 0
`second_character = course[1]`

```py
>>> course = "MSML 605"
>>> second_character = course[1]
>>> print(second_character)
S
```
index has to be an integer

##### Negative Indices

Using negative indices: counts backwards from the string end

```py
>>> course[-1]
5
```

##### len() Function

last index using length

```py
>>> len(course)
8
```

##### Traversal with while

Processing one character at a time

```py
course = "MSML 605"
index = 0
while index < len(course):
  letter = course[index]
  print(letter)
  index +=1

output:
M
S
M
L

6
0
5
```

##### Traversal with for

A more Pythonic way to traverse a string using for

```py
course = "MSML 605"
for c in course:
  print(c)

output:
M
S
M
L

6
0
5
```

```py
course = "MSML 605"
for c in course:
  print(c, end = ' ')

output:
M S M L   6 0 5
```

##### String Concatenation

Two strings can be concatenated using the ‘+’ operator

```py
word1 = 'abc'
word2 = 'def'
word = word1 + word2
print(word)

output:
abcdef
```

##### String Slices

A segment of a string is a slice
Selecting a slice is similar to selecting a character

The operator [n:m] returns the part of the string from the “n-eth” character to the “m-eth” character

It includes the first but excludes the last

```py
>>> greeting = 'hello, world'
>>> greeting[1:3]
'el'
>>> greeting[-3:-1]
'rl'
```

If the first index before the colon is omitted, the slice starts at the beginning of the string.
If you omit the second index, the slice goes to the end of the string

```py
>>> print(greeting[:4], greeting[7:])
hell world
```

If the first index >= second index, the result is an empty string
You can pick every kth element if you like

```py
>>> greeting[3:10:2]
'l,wr'
```

##### Strings Are Immutable

Once created, a string cannot be modified
What happens if [ ] operators are used on the left side of the assignment operator?

```py
>>> greeting = 'hello, world'
>>> greeting = 'J' + greeting[1:]
>>> greeting
'Jello, world'
```

##### String Search

find is the opposite of the [ ] operator
Instead of taking an index and extracting the corresponding character, it takes a character and finds an index

```py
def find(word,letter):
  index = 0
  while index < len(word):
    if word[index] == letter:
      return(index)
    index +=1
  return(-1)
```

##### Looping and Counting

The following program counts the number of times the letter ‘a’ appears in a string

```py
word = 'banana'
count = 0
for leter in word:
  if letter == 'a':
    count +=1
print(count)

output:
3
```

##### upper() Method

A method is a function that is bundled together with an object: it takes arguments and returns a value
A method call is called an invocation
We are invoking upper() on word
```py
word = 'banana'
word = word.upper()
word

OUTPUT
'BANANA'
```

##### find() Method

There is a string method named ‘find()’
We invoke find() on word

```py
word = 'banana'
index = word.find('a')
print (index)  # will print 1, the first instance of 'a'
```

find() can also find substrings not just characters
`word.find('na')`

It can take as a second argument the index where it
should start:
`word.find(‘na’,3)`

As a third argument the index where it should stop:

```py
name = ‘bob’
name.find(‘b’,1,2)
```

##### in Operator

The word ‘in’ is a Boolean operator that takes two strings and returns true if the first appears as a substring in the second
`‘a’ in ‘banana’`
`‘seed’ in ‘banana’`

##### String Comparison

Relational operators work on strings
Equality operator ‘==’
Other relational operations are useful for putting words in alphabetical order:

```py
if word < 'banana’:
   print('Your word, ' + word + ', comes before banana.')
elif word > 'banana’:
   print('Your word, ' + word + ', comes after banana.')
else:
   print('All right, bananas.')
```

##### String Operationss

 "hello"+"world" "helloworld"      # concatenation
 "hello"*3 "hellohellohello" # repetition
 "hello"[0] "h"      # indexing
 "hello"[-1] "o"      # (from end)
 "hello"[1:4] "ell"      # slicing
 len("hello") 5      # size
 "hello" < "jello" 1      # comparison
 "e" in "hello" 1      # search
 New line:  "escapes: \n "
 Line continuation:  triple quotes ’’’
 Quotes:  ‘single quotes’, "raw strings"

##### String Methods

 upper()
 lower()
 capitalize()
 count(s)
 find(s)
 rfind(s)
 index(s)
 strip(), lstrip(), rstrip()
 replace(a, b)
 expandtabs()
 split()
 join()
 center(), ljust(), rjust()

#### Lists

A sequence type
A sequence of values
These values can be of any type
Values in a list are called items or elements

```py

```

##### Lists are Mutable

The syntax for accessing list elements is the same as for accessing string characters
The expression inside brackets specifies the index

```py
>>> numbers = [7, 34, 56]
>>> numbers[1] = 36        # list is mutable
>>> print(numbers)
[7, 36, 56]
```

##### Mapping

You can think of a list as a mapping between indices and elements
Each index “maps to” one of the elements

`num = [2, 34, 56]`

##### Indices

List indices work the same way as string indices
 Any integer expression can be used as an index
 if you try to read or write an element that does not exist, you get an IndexError
 If an index has a negative value, it counts backward from the end
of the list

##### ‘in’ Operator

The ‘in’ operator also works on lists

```py
cheeses = [“Cheddar”, “Mozzarella”, “Blue”]
“Blue” in cheeses   # True
“Brie” in cheeses   # False
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

#####



```py

```

#####



```py

```

#####



```py

```
