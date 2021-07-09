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

### HelloWorld
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

### Variables and expressions

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


### Functions

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

### Conditional statements

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

### Loops

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

if __name__ == "__main__":
  main()
```  
> 5 <br />
  6 <br />
  7 <br />
  8 <br />
  9 <br />

```python
  # use a for loop over a collection
  days = ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"]
  for d in days:
    print (d)

if __name__ == "__main__":
  main()
```
> Mon <br />
  Tue <br />
  Wed <br />
  Thu <br />
  Fri <br />
  Sat <br />
  Sun <br />

```python
  # use the break and continue statements
  for x in range(5,10):
    if (x == 7): break
    print (x)

if __name__ == "__main__":
  main()
```
> 5 <br />
  6

```python
  # use the break and continue statements
  for x in range(5,10):
    if (x % 2 == 0): continue
    print (x)

if __name__ == "__main__":
  main()
```
> 5 <br />
  7 <br />
  9 <br />

```python
  #using the enumerate() function to get index
  days = ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"]
  for i, d in enumerate(days):
    print (i, d)

if __name__ == "__main__":
  main()
```
> 0 Mon <br />
  1 Tue <br />
  2 Wed <br />
  3 Thu <br />
  4 Fri <br />
  5 Sat <br />
  6 Sun <br />

Q: Return the sum of the first item in the data list and every tenth item after?

A:
```python
def Sum10th(data):
  sum=0
  for i,d in enumerate(data):
    if (i % 10 == 0): sum=sum+d
  return sum
```

Q: Print the number of digits in the number variable? You can assume this number is always positive and always less than 10,000.

A:
```python
if (number>=1000):
  print(4)
elif (number>=100):
  print(3)
elif (number>=10):
  print(2)
else:
  print(1)
```
### Classes

```python
class myClass():
    def method1(self):
        print("myClass method1")

    def method2(self, someString):
        print("myClass method2: " + someString)

def main():
    c = myClass()
    c.method1()
    c.method2("This is a string")

if __name__ == "__main__":
    main()
```
> myClass method1 <br />
  myClass method2: This is a string


```python
class myClass():
    def method1(self):
        print("myClass method1")

    def method2(self, someString):
        print("myClass method2: " + someString)


class anotherClass(myClass):
   def method1(self):
        myClass.method1(self)
        print("myClass method1")

    def method2(self, someString):
        print("myClass method2 ")


def main():
    c = myClass()
    c.method1()
    c.method2("This is a string")

    c2 = anotherClass()
    c2.method1()
    c2.method2("This is a string")


if __name__ == "__main__":
    main()
```
> myClass method1 <br />
  myClass method2: This is a string <br />
  myClass method1 <br />
  anotherClass method1 <br />
  anotherClass method2

```python
class Advanced(Simple):
  def Inverse(self,x,y):
    return (1/Simple.Add(self,x,y))
```

Q: You have an existing class Simple() that returns the sum of two numbers using its Add(x,y) method. How can you leverage it to build another class that calculates the inverse of the sum of two numbers?

A:
```python
class Simple():
  def Add(self,x,y):
      return (x + y)

class Advanced(Simple):
  def Inverse(self,x,y):
      Simple.Add(self,x,y)
      print (1/Simple.Add(self,x,y))

def main():
    c = Advanced()
    c.Inverse(1,2)

if __name__ == "__main__":
    main()
```
> 0.3333333333333333

Q: In Python, what is the correct way to develop a class called Person that has parameters in the initialize function called name, age, and sex?

A:
```python
class Person:
  def __initialize__(self, name, age, sex):
    self.name = name
    self.age = age
    self.sex = sex   
```

Q: You need to set the annual payment in one function and print the respective monthly payment in a separate function. How would you fix the suggested code to work properly?

A:
```python
def SetAnnual():
  global annual
  annual=10000
def PrintMonthly():
  print("Your monthly payment is "+str(annual/12)+" USD.")
SetAnnual()
PrintMonthly()
```

### Modules
```python
# import the math module, which contains features for working with mathematics
import math

# the math module contains lots of pre-built functions
print("The square root of 16 is", math.sqrt(16))

# in addition to functions, some modules contain useful constants
print("Pi is:", math.pi)

# try some of the math functions for yourself here:
```
> The square root of 16 is 4.0 <br />
  Pi is: 3.141592653589793

### Date information

```python
from datetime import date
from datetime import time
from datetime import datetime

def main():
  ## DATE OBJECTS
  # Get today's date from the simple today() method from the date class
  today = date.today()
  print ("Today's date is ", today)

  # print out the date's individual components
  print ("Date Components: ", today.day, today.month, today.year)

  # retrieve today's weekday (0=Monday, 6=Sunday)
  print ("Today's Weekday #: ", today.weekday())
  days = ["monday","tuesday","wednesday","thursday","friday","saturday","sunday"]
  print ("Which is a " + days[today.weekday()])

  ## DATETIME OBJECTS
  # Get today's date from the datetime class
  today = datetime.now()
  print  ("The current date and time is ", today)

  # Get the current time
  t = datetime.time(datetime.now())
  print ("The current time is ", t)


if __name__ == "__main__":
  main();
```
> Today's date is  2021-07-09 <br />
  Date Components:  9 7 2021 <br />
  Today's Weekday #:  4 <br />
  Which is a friday <br />
  The current date and time is  2021-07-09 14:15:32.017705 <br />
  The current time is  14:15:32.017705 <br />

### Date output

```python
from datetime import datetime

def main():
  # Times and dates can be formatted using a set of predefined string
  # control codes
  now = datetime.now() # get the current date and time

  #### Date Formatting ####

  # %y/%Y - Year, %a/%A - weekday, %b/%B - month, %d - day of month
  print (now.strftime("The current year is: %Y")) # full year with century
  print (now.strftime("%a, %d %B, %y")) # abbreviated day, num, full month, abbreviated year

  # %c - locale's date and time, %x - locale's date, %X - locale's time
  print (now.strftime("Locale date and time: %c"))
  print (now.strftime("Locale date: %x"))
  print (now.strftime("Locale time: %X"))

  #### Time Formatting ####

  # %I/%H - 12/24 Hour, %M - minute, %S - second, %p - locale's AM/PM
  print (now.strftime("Current time: %I:%M:%S %p")) # 12-Hour:Minute:Second:AM
  print (now.strftime("24-hour time: %H:%M")) # 24-Hour:Minute


if __name__ == "__main__":
  main();
```
> The current year is: 2021 <br />
  Fri, 09 July, 21 <br />
  Locale date and time: Fri Jul  9 14:20:47 2021 <br />
  Locale date: 07/09/21 <br />
  Locale time: 14:20:47 <br />
  Current time: 02:20:47 PM <br />
  24-hour time: 14:20 <br />

### Timedelta objects
```python
from datetime import date
from datetime import time
from datetime import datetime
from datetime import timedelta

# construct a basic timedelta and print it
print (timedelta(days=365, hours=5, minutes=1))

# print today's date
now = datetime.now()
print ("today is: " + str(now))

# print today's date one year from now
print ("one year from now it will be: " + str(now + timedelta(days=365)))

# create a timedelta that uses more than one argument
print ("in two weeks and 3 days it will be: " + str(now + timedelta(weeks=2, days=3)))

# calculate the date 1 week ago, formatted as a string
t = datetime.now() - timedelta(weeks=1)
s = t.strftime("%A %B %d, %Y")
print ("one week ago it was " + s)

### How many days until April Fools' Day?

today = date.today()  # get today's date
afd = date(today.year, 4, 1)  # get April Fool's for the same year
# use date comparison to see if April Fool's has already gone for this year
# if it has, use the replace() function to get the date for next year
if afd < today:
  print ("April Fool's day already went by %d days ago" % ((today-afd).days))
  afd = afd.replace(year=today.year + 1)  # if so, get the date for next year

# Now calculate the amount of time until April Fool's Day  
time_to_afd = afd - today
print ("It's just", time_to_afd.days, "days until next April Fools' Day!")
```
> 365 days, 5:01:00 <br />
  today is: 2021-07-09 14:48:10.070308 <br />
  one year from now it will be: 2022-07-09 14:48:10.070308 <br />
  in two weeks and 3 days it will be: 2021-07-26 14:48:10.070308 <br />
  one week ago it was Friday July 02, 2021 <br />
  April Fool's day already went by 99 days ago <br />
  It's just 266 days until next April Fools' Day! <br />

```python


```


```python


```



```python


```
