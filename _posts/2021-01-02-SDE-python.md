



run file

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
  #global f
  f = "def"
  print (f)

someFunction()
print (f)
```

```python
del f
print (f)
```

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

```python

```
