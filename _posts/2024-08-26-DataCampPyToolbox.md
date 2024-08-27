---
layout: post
title: DataCamp Data Python Toolbox
date: 2024-08-26 11:18 +0800
tags: [python]
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

**Course Description**

In this Python Toolbox course, you'll continue to build more advanced Python skills. First, you'll learn about iterators, objects you have already encountered in the context of for loops. You'll then learn about list comprehensions, which are extremely handy tools for all data professionals and developers working in Python. You'll end the course by working through a case study in which you'll apply all the techniques you learned in both parts of this course.

## Using iterators in PythonLand
---
### Introduction to iterators

```py
employees = ['Nick', 'Lore', 'Hugo']
for employee in employees:
  print(employee)
```
```
Nick
Lore
Hugo
```
---
```py
for letter in 'DataCamp':
  print(letter)
```
```
D
a
t
a
C
a
m
p
```
---
```py
for i in range(4):
  print(i)
```
```
0
1
2
3
```
---
```py
word = 'Da'
it = iter(word)
next(it)
```
```
'D'
```

```py
next(it)
```
```
'a'
```
---
```py
word = 'Data'
it = iter(word)
print(*it)
```
```
D a t a
```
---
```py
pythonistas = {'hugo': 'bowne-anderson', 'francis': 'castro'}
for key,value in pythonistas.items():
  print(key, value)
```
```
hugo bowne-anderson
francis castro
```
---
```py
file = open('file.txt')
it = iter(file)
print(next(it))
```
```
This is the first line.
```
```py
print(next(it))
```
```
This is the second line.
```
---
### Iterating over iterables (1)

Great, you're familiar with what iterables and iterators are! In this exercise, you will reinforce your knowledge about these by iterating over and printing from iterables and iterators.

**_Instructions:_**
* Create a for loop to loop over flash and print the values in the list. Use person as the loop variable.
* Create an iterator for the list flash and assign the result to superhero.
* Print each of the items from superhero using next() 4 times.

```py
# Create a list of strings: flash
flash = ['jay garrick', 'barry allen', 'wally west', 'bart allen']

# Print each list item in flash using a for loop
for i in flash:
    print(i)

# Create an iterator for flash: superhero
superhero = iter(flash)

# Print each item from the iterator
print(next(superhero))
print(next(superhero))
print(next(superhero))
print(next(superhero))
```
```
jay garrick
barry allen
wally west
bart allen
jay garrick
barry allen
wally west
bart allen
```
---
### Iterating over iterables (2)

One of the things you learned about in this chapter is that not all iterables are actual lists. A couple of examples that we looked at are strings and the use of the range() function. In this exercise, we will focus on the range() function.

You can use range() in a for loop as if it's a list to be iterated over:

```
for i in range(5):
    print(i)
```

Recall that range() doesn't actually create the list; instead, it creates a range object with an iterator that produces the values until it reaches the limit (in the example, until the value 4). If range() created the actual list, calling it with a value of 10^100 may not work, especially since a number as big as that may go over a regular computer's memory. The value 10^100 is actually what's called a Googol which is a 1 followed by a hundred 0s. That's a huge number!

Your task for this exercise is to show that calling range() with 10^100 won't actually pre-create the list.

**_Instructions:_**
* Create an iterator object small_value over range(3) using the function iter().
* Using a for loop, iterate over range(3), printing the value for every iteration. Use num as the loop variable.
* Create an iterator object googol over range(10 ** 100).

```py
# Create an iterator for range(3): small_value
small_value = iter(range(3))

# Print the values in small_value
print(next(small_value))
print(next(small_value))
print(next(small_value))

# Loop over range(3) and print the values
for i in range(3):
    print(i)

# Create an iterator for range(10 ** 100): googol
googol = iter(range(10 ** 100))

# Print the first 5 values from googol
print(next(googol))
print(next(googol))
print(next(googol))
print(next(googol))
print(next(googol))
```
```
0
1
2
0
1
2
0
1
2
3
4
```
---
### Iterators as function arguments

You've been using the iter() function to get an iterator object, as well as the next() function to retrieve the values one by one from the iterator object.

There are also functions that take iterators and iterables as arguments. For example, the list() and sum() functions return a list and the sum of elements, respectively.

In this exercise, you will use these functions by passing an iterable from range() and then printing the results of the function calls.

**_Instructions:_**
* Create a range object that would produce the values from 10 to 20 using range(). Assign the result to values.
* Use the list() function to create a list of values from the range object values. Assign the result to values_list.
* Use the sum() function to get the sum of the values from 10 to 20 from the range object values. Assign the result to values_sum.

```py
# Create a range object: values
values = range(10,21)

# Print the range object
print(values)

# Create a list of integers: values_list
values_list = list(iter(values))

# Print values_list
print(values_list)

# Get the sum of values: values_sum
values_sum = sum(values)

# Print values_sum
print(values_sum)

```
```
range(10, 21)
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
165
```
---
### Playing with iterators

```py
avengers = ['hawkeye', 'iron man', 'thor', 'quicksilver']
e = enumerate(avengers)
e_list = list(e)
print(e_list)
```
```
[(0, 'hawkeye'),(1,'iron man'), (2,'thor'), (3, 'quicksilver')]
```
```py
for index, calue in enumerate(avengers):
  print(index, value)
```
```
0 hawkeye
1 iron man
2 thor
3 quicksilver
```
```py
for index, calue in enumerate(avengers, start=10):
  print(index, value)
```
```
10 hawkeye
11 iron man
12 thor
13 quicksilver
```
---
```py
avengers = ['hawkeye', 'iron man', 'thor', 'quicksilver']
names = ['barton','stark','odinson','maximoff']
z = zip(avengers, names)
z_list = list(z)
print(z_list)
```
```
[('hawkeye', 'barton'),('iron man', 'stark'), ('thor', 'odinson'), ('quicksilver', 'maximoff')]
```
```py
for z1, z2 in zip(avengers, names):
  print(z1,z2)
```
```
hawkeye barton
iron man stark
thor odinson
quicksilver maximoff
```
```py
z = zip(avengers, names)
print(*z)
```
```
('hawkeye', 'barton') ('iron man', 'stark')  ('thor', 'odinson') ('quicksilver', 'maximoff')
```
---
### Using enumerate

You're really getting the hang of using iterators, great job!

You've just gained several new ideas on iterators from the last video and one of them is the enumerate() function. Recall that enumerate() returns an enumerate object that produces a sequence of tuples, and each of the tuples is an index-value pair.

In this exercise, you are given a list of strings mutants and you will practice using enumerate() on it by printing out a list of tuples and unpacking the tuples using a for loop.

**_Instructions:_**
* Create a list of tuples from mutants and assign the result to mutant_list. Make sure you generate the tuples using enumerate() and turn the result from it into a list using list().
* Complete the first for loop by unpacking the tuples generated by calling enumerate() on mutants. Use index1 for the index and value1 for the value when unpacking the tuple.
* Complete the second for loop similarly as with the first, but this time change the starting index to start from 1 by passing it in as an argument to the start parameter of enumerate(). Use index2 for the index and value2 for the value when unpacking the tuple.

```py
# Create a list of strings: mutants
mutants = ['charles xavier',
            'bobby drake',
            'kurt wagner',
            'max eisenhardt',
            'kitty pryde']

# Create a list of tuples: mutant_list
mutant_list = list(enumerate(mutants))

# Print the list of tuples
print(mutant_list)

# Unpack and print the tuple pairs
for index1, value1 in enumerate(mutants):
    print(index1, value1)

# Change the start index
for index2, value2 in enumerate(mutants, start = 1):
    print(index2, value2)

```
```
[(0, 'charles xavier'), (1, 'bobby drake'), (2, 'kurt wagner'), (3, 'max eisenhardt'), (4, 'kitty pryde')]
0 charles xavier
1 bobby drake
2 kurt wagner
3 max eisenhardt
4 kitty pryde
1 charles xavier
2 bobby drake
3 kurt wagner
4 max eisenhardt
5 kitty pryde
```
---
### Using zip

Another interesting function that you've learned is zip(), which takes any number of iterables and returns a zip object that is an iterator of tuples. If you wanted to print the values of a zip object, you can convert it into a list and then print it. Printing just a zip object will not return the values unless you unpack it first. In this exercise, you will explore this for yourself.

Three lists of strings are pre-loaded: mutants, aliases, and powers. First, you will use list() and zip() on these lists to generate a list of tuples. Then, you will create a zip object using zip(). Finally, you will unpack this zip object in a for loop to print the values in each tuple. Observe the different output generated by printing the list of tuples, then the zip object, and finally, the tuple values in the for loop.

**_Instructions:_**
* Using zip() with list(), create a list of tuples from the three lists mutants, aliases, and powers (in that order) and assign the result to mutant_data.
* Using zip(), create a zip object called mutant_zip from the three lists mutants, aliases, and powers.
* Complete the for loop by unpacking the zip object you created and printing the tuple values. Use value1, value2, value3 for the values from each of mutants, aliases, and powers, in that order.

```py

```
```

```
---
