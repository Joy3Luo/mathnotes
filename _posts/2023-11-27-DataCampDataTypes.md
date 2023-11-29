---
layout: post
title: DataCamp Data Types for Data Science in Python
date: 2023-11-27 11:18 +0800
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

  <style TYPE="text/css">code.has-jax {font: inherit; font-size: 100%; background: inherit; border: inherit;}</style><script type="text/x-mathjax-config">
  MathJax.Hub.Config({
      tex2jax: {
          inlineMath: [['$','$'], ['\\(','\\)']],
          displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
          skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'] // removed 'code' entry
      }});
  MathJax.Hub.Queue(function() {
      var all = MathJax.Hub.getAllJax(), i;
      for(i = 0; i < all.length; i += 1) {
          all[i].SourceElement().parentNode.className += ' has-jax';
      }});
  </script><script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-AMS_HTML-full"></script>  

**Course Description**

Have you got your basic Python programming chops down for Data Science but are  yearning for more? Then this is the course for you. Herein, you'll consolidate and practice your knowledge of lists, dictionaries, tuples, sets, and date times. You'll see their relevance in working with lots of real data and how to leverage several of them in concert to solve multistep problems, including an extended case  study using Chicago metropolitan area transit data. You'll also learn how to use many of the objects in the Python Collections module, which will allow you to store and manipulate your data for a variety of Data Scientific purposes. After taking this course, you'll be ready to tackle many Data Science challenges Pythonically.

## Fundamental Sequence Data Types
---
### Manipulating lists for fun and profit

You may be familiar with adding individual data elements to a list by using the .append() method. However, if you want to combine a list with another array type (list, set, tuple), you can use the .extend() method on the list.

You can also use the .index() method to find the position of an item in a list. You can then use that position to remove the item with the .pop() method.

In this exercise, you'll practice using all these methods!

**_Instructions:_**
* Create a list called baby_names with the names 'Ximena', 'Aliza', 'Ayden', and 'Calvin'.
* Use the .extend() method on baby_names to add 'Rowen' and 'Sandeep' and print the list.
* Use the .index() method to find the position of 'Rowen' in the list. Save the result as position.
* Use the .pop() method with position to remove 'Rowen' from the list.

```py
# Create a list containing the names: baby_names
baby_names = ['Ximena', 'Aliza', 'Ayden', 'Calvin']

# Extend baby_names with 'Rowen' and 'Sandeep'
baby_names.extend(['Rowen', 'Sandeep'])

# Find the position of 'Rowen': position
position = baby_names.index('Rowen')

# Remove 'Rowen' from baby_names
baby_names.pop(position)

# Print baby_names
print(baby_names)
```
```
['Ximena', 'Aliza', 'Ayden', 'Calvin', 'Sandeep']
```
---
### Looping over lists

Previously, you've used a for loop to iterate over a list, but you can also use a list comprehension. List comprehensions take the form of [action for item in list] and return a new list.

We can use the sorted() function to sort the data in a list from lowest to highest in the case of numbers and alphabetical order if the list contains strings. The sorted() function returns a new list and does not affect the list you passed into the function. You can learn more about sorted() in the Python documentation.

A list of lists, records has been pre-loaded, and each entry is a list of this form:

`['2014','F','20799','Emma']`

**_Instructions:_**
* contains the name, found in the fourth element of row.
* Print baby_names in alphabetical order using the sorted() function.

```py
# Create the list comprehension: baby_names
baby_names = [row[3] for row in records]

# Print the sorted baby names in ascending alphabetical order
print(sorted(baby_names))
```
```
['Abigail', 'Addison', 'Amelia', 'Aubrey', 'Ava', 'Avery', 'Brooklyn', 'Charlotte', 'Chloe', 'Elizabeth', 'Ella', 'Emily', 'Emma', 'Evelyn', 'Grace', 'Harper', 'Isabella', 'Lillian', 'Madison', 'Mia', 'Natalie', 'Olivia', 'Sofia', 'Sophia', 'Victoria', 'Zoey']
```
---
### Using and unpacking tuples

If you have a tuple like ('chocolate chip cookies', 15) and you want to access each part of the data, you can use an index just like a list. However, you can also "unpack" the tuple into multiple variables such as type, count = ('chocolate chip cookies', 15) that will set type to 'chocolate chip cookies' and count to 15.

Often you'll want to pair up multiple array data types. The zip() function does just that. It will return a list of tuples containing one element from each list passed into zip().

When looping over a list, you can also track your position in the list by using the enumerate() function. The function returns the index of the list item you are currently on in the list and the list item itself. (We'll talk more about the last line of code in our next lesson)

**_Instructions:_**
* Use the zip() function to pair up girl_names and boy_names into a variable called pairs.
* Use a for loop to loop through pairs, using enumerate() to keep track of your position. Unpack pairs into the variables rank and pair.
* Unpack pair into the variables girl_name and boy_name.
* Print the rank, girl name, and boy name, in that order. The rank is contained in rank.

```py
# Pair up the girl and boy names: pairs
pairs = zip(girl_names,boy_names)

# Iterate over pairs
for rank, pair in enumerate(pairs):
    # Unpack pair: girl_name, boy_name
    girl_name, boy_name = pair
    # Print the rank and names associated with each rank
    print(f'Rank {rank+1}: {girl_name} and {boy_name}')
```
```
Rank 1: Jada and Josiah
Rank 2: Emily and Ethan
Rank 3: Ava and David
Rank 4: Serenity and Jayden
Rank 5: Claire and Mason
Rank 6: Sophia and Ryan
Rank 7: Sarah and Christian
Rank 8: Ashley and Isaiah
Rank 9: Chaya and Jayden
Rank 10: Abigail and Michael
Rank 11: Zoe and Noah
Rank 12: Leah and Samuel
Rank 13: Hailey and Sebastian
Rank 14: Ava and Noah
Rank 15: Olivia and Dylan
Rank 16: Emma and Lucas
Rank 17: Chloe and Joshua
Rank 18: Sophia and Angel
Rank 19: Aaliyah and Jacob
Rank 20: Angela and Matthew
Rank 21: Camila and Josiah
Rank 22: Savannah and Jacob
Rank 23: Serenity and Muhammad
Rank 24: Chloe and Alexander
Rank 25: Fatoumata and Jason
```
---
### Making tuples by accident

Tuples are very powerful and useful, and it's super easy to make one by accident. All you have to do is create a variable and follow the assignment with a comma. This becomes an error when you try to use the variable later expecting it to be a string or a number.

You can verify the data type of a variable with the type() function. In this exercise, you'll see for yourself how easy it is to make a tuple by accident.

**_Instructions:_**
* Create a variable named normal and set it equal to 'simple'.
* Create a variable named error and set it equal to 'trailing comma',.
* Print the type of the normal and error variables.

```py
# Create the normal variable: normal
normal = 'simple'

# Create the mistaken variable: error
error = 'trailing comma',

# Print the types of the variables
print(type(normal))
print(type(error))
```
```
<class 'str'>
<class 'tuple'>
```
---
### Formatted String Literals ("f" strings)

We've been using plain strings with "" or '' in this class so far, but there are several types of strings and blend variables with them. the most recent addition of a string type to Python is the "f-strings", which is short for formatted string literals. "F-strings" make it easy to mix strings with variables and formatting to help get exactly the output you want and you make them by prefacing the quotes with the letter f like f"". If you want to include a variable within a string you can use the {} around the variable in an f-string to insert the variable's value into the string itself. For example if we had a variable count with the number 12 stored it in, we could make an f-string like f"{count} cookies", which would output the string "12 cookies" when printed. The list top_ten_girl_names contains tuples that correspond to the top_ten_rank and name for each position.

**_Instructions:_**
* Loop over the top_ten_girl_names list and use tuple unpacking to get the top_ten_rank and name.
* Print out each rank and name like this Rank #: 1 - Jada where the number 1 is the rank and Jada is the name.

```py
# Loop over top_ten_girl_names and unpack each tuple into top_ten_rank and name
for top_ten_rank, name in top_ten_girl_names:
  	# Print each name in the proper format
    print(f"Rank #: { top_ten_rank } - { name }")
```
```
Rank #: 1 - Jada
Rank #: 2 - Emily
Rank #: 3 - Ava
Rank #: 4 - Serenity
Rank #: 5 - Claire
Rank #: 6 - Sophia
Rank #: 7 - Sarah
Rank #: 8 - Ashley
Rank #: 9 - Chaya
Rank #: 10 - Abigail
```
---
### Combining multiple strings

F strings work great for a few variables, but what if you want to combine a whole list of variables into a string. You can use the "".join() method for just that. You put what you want to join the list items with inside the "" and then pass the list into the join() method. For example, if you want to join all the items in a list named cookies with a comma and space it would look like ", ".join(cookies).

In this exercise, you'll use these skills to convert a list of the top ten boy names into a sentence stored in a string.

**_Instructions:_**
* Make a string that contains: The top ten boy names are: and store it as preamble.
* Make a string that contains: , and and store it as conjunction.
* Make a string that combines the first 9 names in boy_names list with a comma and store it as first_nine_names.
* Make an f-string that contains preamble, first_nine_names, conjunction, the final item in boy_names and a period.

```py
# The top ten boy names are:  as preamble
preamble = "The top ten boy names are: "

# , and as conjunction
conjunction = ', and'

# Combines the first 9 names in boy_names with a comma and space as first_nine_names
first_nine_names = ', '.join(boy_names[:9])

# Print f-string preamble, first_nine_names, conjunction, the final item in boy_names and a period
print(f"{preamble}{first_nine_names}{conjunction} {boy_names[-1]}.")
```
```
The top ten boy names are: Josiah, Ethan, David, Jayden, Mason, Ryan, Christian, Isaiah, Jayden, and Michael.
```
---
### Finding strings in other strings

Many times when we are working with strings, we care about which characters are in the string. For example, we may want to know how many cookies in a list of cookies have the word Chocolate in them, or how many start with the letter C. We can perform these checks by using the in keyword and the .startswith() method on a string. We can also use conditionals on a list comprehension in the form of `[action for item in list if something is true]`. Using our cookies examples, it would be something like `[cookie_name for cookie_name in cookies if 'chocolate' in cookie_name.lower()]`. Note these checks are case sensitive so we're using the .lower() method on the string. We can also "chain" methods together by calling them one after the other.

**_Instructions:_**
* Store and print a list of girl_names that start with s.
* Store and print a list of girl_names with angel in them.

```py
# Store a list of girl_names that start with s: names_with_s
names_with_s = [name for name in girl_names if name.lower().startswith('s')]

print(names_with_s)

# Store a list of girl_names that contain angel: names_with_angel
names_with_angel = [name for name in girl_names if 'angel' in name.lower()]

print(names_with_angel)
```
```
['Serenity', 'Sophia', 'Sarah', 'Sophia', 'Savannah', 'Serenity']
['Angela']
```
---
## Dictionaries - The Root of Python
---
### Creating and looping through dictionaries

You'll often encounter the need to loop over some array type data, like in Chapter 1, and provide it some structure so you can find the data you desire quickly.

You start that by creating an empty dictionary and assigning part of your array data as the key and the rest as the value.

Previously, you used sorted() to organize your data in a list. Dictionaries can also be sorted. By default, using sorted() on a dictionary will sort by the keys of the dictionary.

The goal of this exercise is to get familiar with building dictionaries via looping over some data source, and then looping over the dictionary to use that data.

**_Instructions:_**
* Create an empty dictionary called squirrels_by_park.
* Loop over squirrels, unpacking it into the variables park and squirrel_details.
* Inside the loop, add each squirrel_details to the squirrels_by_park dictionary using the park as the key.
* Sort the squirrel_details dictionary keys in ascending order, print each park and its value using an F string..

```py
# Create an empty dictionary: squirrels_by_park
squirrels_by_park = {}

# Loop over the squirrels list and unpack each tuple
for park, squirrel_details in squirrels:
    # Add each squirrel_details to the squirrels_by_park dictionary
    squirrels_by_park[park] = squirrel_details

# Sort the squirrels_by_park dict alphabetically by park
for park in sorted(squirrels_by_park):
    # Print each park and its value in squirrels_by_park
    print(f'{park}: {squirrels_by_park[park]}')
```
```
City Hall Park: ('Gray', 'Cinnamon', 'Eating', 'Approaches')
Highbridge Park: ('Gray', 'Cinnamon', 'Running, Eating', 'Runs From, watches us in short tree')
J. Hood Wright Park: ('Gray', 'White', 'Running', 'Indifferent')
Madison Square Park: ('Gray', None, 'Foraging', 'Indifferent')
Marcus Garvey Park: ('Black', 'Cinnamon', 'Cleaning', None)
Seward Park: ('Gray', 'Cinnamon', 'Eating', 'Indifferent')
Tompkins Square Park: ('Gray', 'Gray', 'Lounging', 'Approaches')
Union Square Park: ('Gray', 'Black', 'Climbing', None)
```
---
### Safely finding by key

As demonstrated in the video, if you attempt to access a key that isn't present in a dictionary, you'll get a KeyError. One option to handle this type of error is to use a try: except: block. You can learn more about error handling in Python Data Science Toolbox (Part 1).

Python provides a faster, more versatile tool to help with this problem in the form of the .get() method. The .get() method allows you to supply the name of a key, and optionally, what you'd like to have returned if the key is not found.

You'll be using same squirrels_by_park dictionary, which is keyed by the park name and the value is a tuple with the main color, highlights, action, and reaction to humans, and will gain practice using the .get() method.

**_Instructions:_**
* Safely print 'Union Square Park' from the squirrels_by_park dictionary .
* Safely print the type of 'Fort Tryon Park' from the squirrels_by_park dictionary.
* Safely print 'Central Park' from the squirrels_by_park dictionary or 'Not Found'.

```py
# Safely print 'Union Square Park' from the squirrels_by_park dictionary
print(squirrels_by_park.get('Union Square Park'))

# Safely print the type of 'Fort Tryon Park' from the squirrels_by_park dictionary
print(type(squirrels_by_park.get('Fort Tryon Park')))

# Safely print 'Central Park' from the squirrels_by_park dictionary or 'Not Found'
print(squirrels_by_park.get('Central Park', 'Not Found'))
```
```
('Gray', 'Black', 'Climbing', None)
<class 'NoneType'>
Not Found
```
---
### Adding and extending dictionaries

If you have a dictionary and you want to add data to it, you can simply create a new key and assign the data you desire to it. It's important to remember that if it's a nested dictionary, then all the keys in the data path must exist, and each key in the path must be assigned individually.

You can also use the .update() method to update a dictionary with a list of keys and values from another dictionary, tuples or keyword arguments.

The squirrels_by_park dictionary is already loaded for you, which is keyed by the park name and the value is a tuple with the main color, highlights, action, and reaction to humans.

**_Instructions:_**
* Assign the squirrels_madison list as the value to the 'Madison Square Park' key of the squirrels_by_park dictionary.
* Update the 'Union Square Park' key in the squirrels_by_park dictionary with the data in the squirrels_union tuple.
* Loop over the squirrels_by_park dictionary. Print the park_name and a list of all primary_fur_colors for squirrels safely in that park using a list comprehension; return 'N/A' if the key isn't found.

```py
# Assign squirrels_madison as the value to the 'Madison Square Park' key
squirrels_by_park['Madison Square Park'] = squirrels_madison

# Update squirrels_by_park with the squirrels_union tuple
squirrels_by_park.update([squirrels_union])

# Loop over the park_name in the squirrels_by_park dictionary
for park_name in squirrels_by_park:
    # Safely print a list of the primary_fur_color for each squirrel in park_name
    print(park_name, [squirrel.get('primary_fur_color', 'N/A') for squirrel in squirrels_by_park[park_name]])  
```
```
Union Square Park ['Gray', 'Gray', 'Cinnamon', 'Gray', 'Gray', 'Gray', 'Gray']
Madison Square Park ['Gray', 'Gray', 'Gray']
```
---
### Popping and deleting from dictionaries

Often, you will want to remove keys and value from a dictionary. You can do so using the del Python instruction. It's important to remember that del will throw a KeyError if the key you are trying to delete does not exist. You can not use it with the .get() method to safely delete items; however, it can be used with try: catch:.

If you want to save that deleted data into another variable for further processing, the .pop() dictionary method will do just that. You can supply a default value for .pop() much like you did for .get() to safely deal with missing keys. It's also typical to use .pop() instead of del since it is a safe method.

**_Instructions:_**
* Remove "Madison Square Park" from squirrels_by_park and store it as squirrels_madison.
* Safely remove "City Hall Park" from squirrels_by_park with a empty dictionary as the default and store it as squirrels_city_hall. To do this, pass in an empty dictionary {} as a second argument to .pop().
* Delete "Union Square Park" from squirrels_by_park.

```py
# Remove "Madison Square Park" from squirrels_by_park
squirrels_madison = squirrels_by_park.pop('Madison Square Park')

# Safely remove "City Hall Park" from squirrels_by_park with an empty dictionary as the default
squirrels_city_hall = squirrels_by_park.pop('City Hall Park', {})

# Delete "Union Square Park" from squirrels_by_park
del squirrels_by_park['Union Square Park']

# Print squirrels_by_park
print(squirrels_by_park)
```
```
{'Tompkins Square Park': [{'primary_fur_color': 'Gray', 'highlights_in_fur_color': 'Gray', 'activities': 'Foraging', 'interactions_with_humans': 'Approaches'}, {'primary_fur_color': 'Gray', 'highlights_in_fur_color': 'Gray', 'activities': 'Climbing (down tree)', 'interactions_with_humans': 'Indifferent'}, {'primary_fur_color': 'Gray', 'highlights_in_fur_color': 'Gray', 'activities': 'Foraging', 'interactions_with_humans': 'Indifferent'}, {'primary_fur_color': 'Gray', 'highlights_in_fur_color': 'Gray', 'activities': 'Foraging', 'interactions_with_humans': 'Indifferent'}]}
```
---
### Working with dictionaries more pythonically

So far, you've worked a lot with the keys of a dictionary to access data, but in Python, the preferred manner for iterating over items in a dictionary is with the .items() method.

This returns each key and value from the dictionary as a tuple, which you can unpack in a for loop. You'll now get practice doing this.

We've loaded a squirrels_by_park dictionary, and the Madison Square Park key contains a list of dictionaries.

**_Instructions:_**
* Iterate over the first record in squirrels_by_park["Madison Square Park"], unpacking its items into field and value.
* Repeat the process for the second record in `squirrels_by_park["Union Square Park"]`.

```py
# Iterate over the first squirrel entry in the Madison Square Park list
for field, value in squirrels_by_park["Madison Square Park"][0].items():
    # Print field and value
    print(field, value)

print('-' * 13)

# Iterate over the second squirrel entry in the Union Square Park list
for field, value in squirrels_by_park["Union Square Park"][1].items():
    # Print field and value
    print(field, value)
```
```
primary_fur_color Gray
highlights_in_fur_color None
activities Foraging
interactions_with_humans Indifferent
-------------
primary_fur_color Cinnamon
highlights_in_fur_color None
activities Foraging
interactions_with_humans None
```
---
### Checking dictionaries for data

You can check to see if a key exists in a dictionary by using the in expression.

For example, you can check to see if 'cookies' is a key in the recipes dictionary by using if 'cookies' in recipes: this allows you to safely react to data being present in the dictionary.

We've loaded a squirrels_by_park dictionary with park names for the keys and a list of dictionaries of the squirrels.

**_Instructions:_**
* Check to see if Tompkins Square Park is in the squirrels_by_park dictionary, and print 'Found Tompkins Square Park' if it is present.
* Check to see if Central Park is in squirrels_by_park. Then, print 'Found Central Park' if found and 'Central Park missing' if not found.

```py
# Check to see if Tompkins Square Park is in squirrels_by_park
if "Tompkins Square Park" in squirrels_by_park:
    # Print 'Found Tompkins Square Park'
    print('Found Tompkins Square Park')

# Check to see if Central Park is in squirrels_by_park
if "Central Park" in squirrels_by_park:
    # Print 'Found Central Park' if found
    print('Found Central Park')
else:
    # Print 'Central Park missing' if not found
    print('Central Park missing')
```
```
Found Tompkins Square Park
Central Park missing
```
---
### Dealing with nested dictionaries

A dictionary can contain another dictionary as the value of a key, and this is a very common way to deal with repeating data structures such as yearly, monthly or weekly data. All the same rules apply when creating or accessing the dictionary.

For example, if you had a dictionary that had a ranking of my cookie consumption by year and type of cookie. It might look like `cookies = {'2017': {'chocolate chip': 483, 'peanut butter': 115}, '2016': {'chocolate chip': 9513, 'peanut butter': 6792}}`. I could access how many chocolate chip cookies I ate in 2016 using `cookies['2016']['chocolate chip']`.

When exploring a new dictionary, it can be helpful to use the .keys() method to get an idea of what data might be available within the dictionary. You can also iterate over a dictionary and it will return each key in the dictionary for you to use inside the loop.

We've loaded a squirrels_by_park dictionary with park names for the keys and a nested dictionary of one squirrels data.

**_Instructions:_**
* Print the keys of the squirrels_by_park dictionary, NOTE: They are park_names.
* Print the keys of the squirrels_by_park dictionary for the park_name Union Square Park.
* Loop over the squirrels_by_park dictionary. Inside the loop, safely print the park_name and the highlights_in_fur_color. Print 'N/A' if the highlightsinfur_color is not found or None.

```py
# Print a list of keys from the squirrels_by_park dictionary
print(squirrels_by_park.keys())

# Print the keys from the squirrels_by_park dictionary for 'Union Square Park'
print(squirrels_by_park['Union Square Park'].keys())

# Loop over the dictionary
for park_name in squirrels_by_park:
    # Safely print the park_name and the highlights_in_fur_color or 'N/A'
    print(park_name, squirrels_by_park[park_name].get('highlights_in_fur_color', 'N/A'))
```
```
dict_keys(['J. Hood Wright Park', 'Stuyvesant Square Park', 'Highbridge Park', 'Tompkins Square Park', 'Union Square Park', 'City Hall Park', 'Msgr. McGolrick Park', 'John V. Lindsay East River Park'])
dict_keys(['primary_fur_color', 'activities', 'interactions_with_humans'])
J. Hood Wright Park Cinnamon
Stuyvesant Square Park Cinnamon
Highbridge Park White
Tompkins Square Park Gray
Union Square Park N/A
City Hall Park White
Msgr. McGolrick Park Cinnamon
John V. Lindsay East River Park Gray
```
---
### Dealing with nested mixed types

Previously, we used the in expression so see if data is in a dictionary such as if 'cookies' in recipes_dict. However, what if we want to find data in a dictionary key that is a list of dictionaries? In that scenario, we can use a for loop to loop over the items in the nested list and operate on them. Additionally, we can leverage list comprehensions to effectively filter nested lists of dictionaries. For example: `[cookie for cookie in recipes["cookies"] if "chocolate chip" in cookie["name"]]` would return a list of cookies in recipes list that have chocolate chip in the name key of the cookie.

We've loaded a squirrels_by_park dictionary with park names for the keys and a list of dictionaries of the squirrels.

**_Instructions:_**
* Use a for loop to iterate over the squirrels found in the Tompkins Square Park key of squirrels_by_park: Safely print each activities of each squirrel.
* Print the list of 'Cinnamon' primary_fur_color squirrels found in Union Square Park using a list comprehension.

```py
# Use a for loop to iterate over the squirrels in Tompkins Square Park:
for squirrel in squirrels_by_park["Tompkins Square Park"]:
	# Safely print the activities of each squirrel or None
    print(squirrel.get('activities'))

# Print the list of 'Cinnamon' primary_fur_color squirrels in Union Square Park
print([squirrel for squirrel in squirrels_by_park["Union Square Park"] if 'Cinnamon' in squirrel["primary_fur_color"]])
```
```
Foraging
Climbing (down tree)
None
Foraging
[{'primary_fur_color': 'Cinnamon', 'highlights_in_fur_color': None, 'activities': 'Foraging', 'interactions_with_humans': None}]
```
---
## Numeric Data Types, Booleans, and Sets
---
### Printing floats

Scientific notation is a powerful tool for representing numbers, but it can be confusing to handle when trying to print float values. However, we can use the f strings we learned about previously to make sure we get them printed properly every time by using a format specifier. For example, if we wanted to format a variable in an f string as a float, we can use the f format specifier, such as: print(f"{some_variable:f}"). It also takes an operation precision on the float format specifier, for example, print(f"{some_variable:.4f}") would print four decimal places of precision.

**_Instructions:_**
* Print float1, float2, and float3 notice where the jump to scientific notation occurs.
* Print float2 and float3 using the default float format specifier, and notice what happened to float3.
* Print float3 with the float format specifier and a precision of 7.

```py
# Print floats 1, 2, and 3
print(float1)
print(float2)
print(float3)

# Print floats 2 and 3 using the f string formatter
print(f"{float2:f}")
print(f"{float3:f}")

# Print float 3 with a 7 f string precision
print(f"{float3:0.7f}")
```
```
0.0001
1e-05
1e-07
0.000010
0.000000
0.0000001
```
---
### Division with integers and floats

Python supports two different division operators: / and //. In Python 3, / will consistently return a float result, and // is floor division and will consistently return an integer result. Floor division is the same as doing math.floor(numerator/divisor), which returns the highest integer less than or equal to the result of the division operation. You can learn more about math.floor in the Python Docs.

**_Instructions:_**
* Print the result of 2/1 and 1/2.
* Print the floored division result of 2//1 and 1//2.
* Print the type of 2/1 and 2//1.

```py
# Print the result of 2/1 and 1/2
print(2/1)
print(1/2)

# Print the floored division result of 2//1 and 1//2
print(2//1)
print(1//2)

# Print the type of 2/1 and 2//1
print(type(2/1))
print(type(2//1))
```
```
2.0
0.5
2
0
<class 'float'>
<class 'int'>
```
---
### More than just true and false

Python has two boolean values available for you to use: True and False. Most commonly these boolean values are used to indicate that something is on or off, yes or no, or similar states. Additionally, many python types return "truthy" or "falsey" values depending on their condition when evaluated using the bool() function.

**_Instructions:_**
* Create an empty list called my_list
* Print the truthiness of my_list.
* Append the string 'cookies' to my_list
* Print the truthiness of my_list.

```py
# Create an empty list
my_list = []

# Check the truthiness of my_list
print(bool(my_list))

# Append the string 'cookies' to my_list
my_list.append('cookies')

# Check the truthiness of my_list
print(bool(my_list))
```
```
False
True
```
---
### Comparisons

Booleans and their truthiness are most often used in comparisions, and we use comparisions without even thinking about their underlying data type. To perform a comparision, we can use a comparision operator. Python supports the following comparision operators:

```
== equal to
!= not equal to
> greater than
< less than
>= greater than or equal to
<= less than or equal to
```

For this exercise, we'll be using a subset of the Palmer Archipelago (Antarctica) penguin data set, named penguins, as a list of dictionaries with the keys of species, flipper_length, body_mass and sex.

**_Instructions:_**
* Use a for loop to iterate over the penguins list.
* Check the penguin entry for a body_mass of more than 3300 grams.
* Print the species and sex of the penguin if true.

```py
# Use a for loop to iterate over the penguins list
for penguin in penguins:
  # Check the penguin entry for a body mass of more than 3300 grams
  if penguin["body_mass"] > 3300 :
  	# Print the species and sex of the penguin if true
    print(f"{penguin['species']} - {penguin['sex']}")
```
```
Adlie - FEMALE
Gentoo - FEMALE
Adlie - MALE
Gentoo - FEMALE
Gentoo - FEMALE
Chinstrap - FEMALE
Adlie - MALE
Chinstrap - FEMALE
Chinstrap - FEMALE
Adlie - FEMALE
Gentoo - FEMALE
Adlie - MALE
Adlie - FEMALE
Adlie - FEMALE
Gentoo - .
Gentoo - FEMALE
Adlie - MALE
Gentoo - MALE
```
---
### Truthy, True, Falsey, and False

While comparisons check for truthiness, something being truthy is not the same as it being True. The inverse of that statement is also true about falsey values and them not being False. So we need to be vigilent when we are checking is something is True or False vs truthy or falsey. In Python, we have the is operator to check if two things are identical. This time we'll be using a penguin details record dictionary which has the same keys as the prior exercise (species, flipper_length, body_mass, sex) with the tracked key that has a boolean value.

We loaded a dictionary, penguin_305_details, with all the details of a singular penguin's data.

**_Instructions:_**
* Check the truthiness of penguin_305_details sex key. If true, check if sex is True and store it as sex_is_true. Print the sex key and sex_is_true.
* Check the truthiness of penguin_305_details tracked key. If true, check if tracked is True and store it as tracked_is_true. Print the tracked key and tracked_is_true.

```py
# Check the truthiness of penguin_305_details sex key
if penguin_305_details["sex"]:
	# If true, check if sex is True and store it as sex_is_true
    sex_is_true = penguin_305_details["sex"] is True
    # Print the sex key's value and sex_is_true
    print(f"{penguin_305_details['sex']}: {sex_is_true}")

# Check the truthiness of penguin_305_details tracked key
if penguin_305_details["tracked"]:
	# If true, check if tracked is True and store it as tracked_is_true
    tracked_is_true = penguin_305_details["tracked"] is True
    # Print the tracked key and tracked_is_true
    print(f"{penguin_305_details['tracked']}: {tracked_is_true}")
```
```
FEMALE: False
True: True
```
