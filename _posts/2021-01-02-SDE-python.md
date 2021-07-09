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


Run a file

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

Example file for HelloWorld
```python
def main():
    print("hello world!")
    name = input("What is your name? ")
    print("Nice to meet you,", name)

if __name__ == "__main__":
    main()
```
> hello world!
> What is your name? ***joe***
  Nice to meet you, joe

variables and expressions

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
> def
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
> def
  def

```python
del f
print (f)
```
> NameError: name 'f' is not defined


Example file for working with functions

```python
# define a basic function
def func1():
    print("I am a function")

func1()
print(func1())
print(func1)
```
> I am a function
  I am a function
  None

```python
# function that takes arguments
def func2(arg1, arg2):
    print(arg1, " ", arg2)
```

```python
# function that returns a value
def cube(x):
    return x*x*x
```

```python
# function with default value for an argument
def power(num, x=1):
    result = 1
    for i in range(x):
        result = result * num
    return result
```

```python
# function with variable number of arguments
def multi_add(*args):
    result = 0
    for x in args:
        result = result + x
    return result
```


func2(10, 20)
print(func2(10, 20))
print(cube(3))
print(power(2))
print(power(2, 3))
print(power(x=3, num=2))
print(multi_add(4, 5, 10, 4))


```python

```

```python

```

```python

```

```python

```

```python

```
