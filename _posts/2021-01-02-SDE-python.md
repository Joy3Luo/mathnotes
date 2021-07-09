---
layout: post
title: Programming - python
date: 2021-01-02 12:18 +0800
tags: [Programming]
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


#### Run a file

```pyhon
C:\Users\joy3l>cd"C:\Users\joy3l\Desktop\Exercise Files\Chap01"
The filename, directory name, or volume label syntax is incorrect.

C:\Users\joy3l>cd "C:\Users\joy3l\Desktop\Exercise Files\Chap01"

C:\Users\joy3l\Desktop\Exercise Files\Chap01>dir
 Volume in drive C is OS
 Volume Serial Number is 2C95-528B

 Directory of C:\Users\joy3l\Desktop\Exercise Files\Chap01

2021/07/07  15:42    <DIR>          .
2021/07/07  15:42    <DIR>          ..
2021/07/07  15:42                21 01_03.py
               1 File(s)             21 bytes
               2 Dir(s)  856,122,343,424 bytes free

C:\Users\joy3l\Desktop\Exercise Files\Chap01>python 01_03.py
Hello world!
```

#### Example file for HelloWorld
```python
def main():
    print("hello world!")
    name = input("What is your name? ")
    print("Nice to meet you,", name)

if __name__ == "__main__":
    main()
```
> hello world! <br />
  What is your name? ***joe*** <br />
  Nice to meet you, joe

#### variables and expressions

```python
# Declare a variable and initialize it
f = 0
print (f)
```
> 0

```python
# re-declaring the variable works
f = "abc"
print (f)
```
> abc

```python
# ERROR: variables of different types cannot be combined
#print ("string type " + 123)
print ("string type " + str(123))
```
> string type 123

```python
# Global vs. local variables in functions
def someFunction():
  #global f
  f = "def"
  print (f)

someFunction()
print (f)
```
> def <br />
  abc

```python
# Global vs. local variables in functions
def someFunction():
  global f
  f = "def"
  print (f)

someFunction()
print (f)
```
> def <br />
  def

```python
del f
print (f)
```
> NameError: name 'f' is not defined


#### Example file for working with functions

```python
# define a basic function
def func1():
    print("I am a function")

func1()
print(func1())
print(func1)
```
> I am a function <br />
  I am a function <br />
  None

```python
# function that takes arguments
def func2(arg1, arg2):
    print(arg1, " ", arg2)

func2(10, 20)
print(func2(10, 20))
```
> 10   20 <br />
  10   20

```python
# function that returns a value
def cube(x):
    return x*x*x

print(cube(3))
```
> 27

```python
# function with default value for an argument
def power(num, x=1):
    result = 1
    for i in range(x):
        result = result * num
    return result

print(power(2))
print(power(2, 3))
print(power(x=3, num=2))
```
> 2 <br />
  8 <br />
  8 <br />

```python
# function with variable number of arguments
def multi_add(*args):
    result = 0
    for x in args:
        result = result + x
    return result

print(multi_add(4, 5, 10, 4))
```
> 23

#### Example file for working with conditional statements

```python
def main():
    x, y = 10, 100

    # conditional flow uses if, elif, else
    if(x < y):
        st = "x is less than y"
    elif (x == y):
        st = "x is same as y"
    else:
        st = "x is greater than y"
    print(st)

    # conditional statements let you use "a if C else b"
    st = "x is less than y" if (x < y) else "x is greater than or equal to y"
    print(st)

    # Python does not have support for higher-order conditionals
    # like "switch-case" in other languages


if __name__ == "__main__":
    main()
```
> x is less than y <br />
  x is less than y

#### Example file for working with loops

```python
def main():
  x = 0

  # define a while loop
  while (x < 5):
     print (x)
     x = x + 1

if __name__ == "__main__":
  main()
```
> 0 <br />
  1 <br />
  2 <br />
  3 <br />
  4 <br />

```python
  # define a for loop
  for x in range(5,10):
    print (x)

  # use a for loop over a collection
  days = ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"]
  for d in days:
    print (d)

  # use the break and continue statements
  for x in range(5,10):
    #if (x == 7): break
    #if (x % 2 == 0): continue
    print (x)

  #using the enumerate() function to get index
  days = ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"]
  for i, d in enumerate(days):
    print (i, d)

if __name__ == "__main__":
  main()
```

```python

```

```python

```

```python

```
