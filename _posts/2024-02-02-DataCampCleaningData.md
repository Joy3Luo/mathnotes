---
layout: post
title: Cleaning Data in Python
date: 2024-02-02 11:18 +0800
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

It's commonly said that data scientists spend 80% of their time cleaning and manipulating data and only 20% of their time analyzing it. The time spent cleaning is vital since analyzing dirty data can lead you to draw inaccurate conclusions.


Data cleaning is an essential task in data science. Without properly cleaned data, the results of any data analysis or machine learning model could be inaccurate. In this course, you will learn how to identify, diagnose, and treat a variety of data cleaning problems in Python, ranging from simple to advanced. You will deal with improper data types, check that your data is in the correct range, handle missing data, perform record linkage, and more!

---
## Common data problems
---
### Numeric data or ... ?
In this exercise, and throughout this chapter, you'll be working with bicycle ride sharing data in San Francisco called ride_sharing. It contains information on the start and end stations, the trip duration, and some user information for a bike sharing service.

The user_type column contains information on whether a user is taking a free ride and takes on the following values:

1 for free riders.
2 for pay per ride.
3 for monthly subscribers.
In this instance, you will print the information of ride_sharing using .info() and see a firsthand example of how an incorrect data type can flaw your analysis of the dataset. The pandas package is imported as pd.

**_Instructions:_**
* Print the information of ride_sharing.
* Use .describe() to print the summary statistics of the user_type column from ride_sharing.
*

```py
# Print the information of ride_sharing
print(ride_sharing.info())

# Print summary statistics of user_type column
print(ride_sharing['user_type'].describe())
```

**_Instructions:_**
* Convert user_type into categorical by assigning it the 'category' data type and store it in the user_type_cat column.
* Make sure you converted user_type_cat correctly by using an assert statement.

```py
# Print the information of ride_sharing
print(ride_sharing.info())

# Print summary statistics of user_type column
print(ride_sharing['user_type'].describe())

# Convert user_type from integer to category
ride_sharing['user_type_cat'] = ride_sharing['user_type'].astype('category')

# Write an assert statement confirming the change
assert ride_sharing['user_type_cat'].dtype == 'category'

# Print new summary statistics
print(ride_sharing['user_type_cat'].describe())
```
---
### Summing strings and concatenating numbers

In the previous exercise, you were able to identify that category is the correct data type for user_type and convert it in order to extract relevant statistical summaries that shed light on the distribution of user_type.

Another common data type problem is importing what should be numerical values as strings, as mathematical operations such as summing and multiplication lead to string concatenation, not numerical outputs.

In this exercise, you'll be converting the string column duration to the type int. Before that however, you will need to make sure to strip "minutes" from the column in order to make sure pandas reads it as numerical. The pandas package has been imported as pd.

**_Instructions:_**
* Use the .strip() method to strip duration of "minutes" and store it in the duration_trim column.
* Convert duration_trim to int and store it in the duration_time column.
* Write an assert statement that checks if duration_time's data type is now an int.
* Print the average ride duration.

```py
# Strip duration of minutes
ride_sharing['duration_trim'] = ride_sharing['duration'].str.strip('minutes')

# Convert duration to integer
ride_sharing['duration_time'] = ride_sharing['duration_trim'].astype('int')

# Write an assert statement making sure of conversion
assert ride_sharing['duration_time'].dtype == 'int'

# Print formed columns and calculate average ride duration 
print(ride_sharing[['duration','duration_trim','duration_time']])
print(ride_sharing['duration_time'].mean())
```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
###



**_Instructions:_**
*
*
*

```py

```
```

```
---
