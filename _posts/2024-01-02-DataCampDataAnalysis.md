---
layout: post
title: DataCamp Exploratory Data Analysis in Python
date: 2024-01-02 11:18 +0800
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

So you’ve got some interesting data - where do you begin your analysis? This course will cover the process of exploring and analyzing data, from understanding what’s included in a dataset to incorporating exploration findings into a data science workflow.


Using data on unemployment figures and plane ticket prices, you’ll leverage Python to summarize and validate data, calculate, identify and replace missing values, and clean both numerical and categorical values. Throughout the course, you’ll create beautiful Seaborn visualizations to understand variables and their relationships.


For example, you’ll examine how alcohol use and student performance are related. Finally, the course will show how exploratory findings feed into data science workflows by creating new features, balancing categorical features, and generating hypotheses from findings.


By the end of this course, you’ll have the confidence to perform your own exploratory data analysis (EDA) in Python.You’ll be able to explain your findings visually to others and suggest the next steps for gathering insights from your data!

## Getting to Know a Dataset
---
### Functions for initial exploration

You are researching unemployment rates worldwide and have been given a new dataset to work with. The data has been saved and loaded for you as a pandas DataFrame called unemployment. You've never seen the data before, so your first task is to use a few pandas functions to learn about this new data.

pandas has been imported for you as pd.

**_Instructions:_**
* Use a pandas function to print the first five rows of the unemployment DataFrame.

```py
# Print the first five rows of unemployment
print(unemployment.head())
```
```
  country_code          country_name      continent   2010   2011  ...   2017   2018   2019   2020   2021
0          AFG           Afghanistan           Asia  11.35  11.05  ...  11.18  11.15  11.22  11.71  13.28
1          AGO                Angola         Africa   9.43   7.36  ...   7.41   7.42   7.42   8.33   8.53
2          ALB               Albania         Europe  14.09  13.48  ...  13.62  12.30  11.47  13.33  11.82
3          ARE  United Arab Emirates           Asia   2.48   2.30  ...   2.46   2.35   2.23   3.19   3.36
4          ARG             Argentina  South America   7.71   7.18  ...   8.35   9.22   9.84  11.46  10.90

[5 rows x 15 columns]
```

**_Instructions:_**
* Use a pandas function to print a summary of column non-missing values and data types from the unemployment DataFrame.

```py
# Print a summary of non-missing values and data types in the unemployment DataFrame
print(unemployment.info())
```
```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 182 entries, 0 to 181
Data columns (total 15 columns):
 #   Column        Non-Null Count  Dtype  
---  ------        --------------  -----  
 0   country_code  182 non-null    object
 1   country_name  182 non-null    object
 2   continent     177 non-null    object
 3   2010          182 non-null    float64
 4   2011          182 non-null    float64
 5   2012          182 non-null    float64
 6   2013          182 non-null    float64
 7   2014          182 non-null    float64
 8   2015          182 non-null    float64
 9   2016          182 non-null    float64
 10  2017          182 non-null    float64
 11  2018          182 non-null    float64
 12  2019          182 non-null    float64
 13  2020          182 non-null    float64
 14  2021          182 non-null    float64
dtypes: float64(12), object(3)
memory usage: 21.5+ KB
None
```

**_Instructions:_**
* Print the summary statistics (count, mean, standard deviation, min, max, and quartile values) of each numerical column in unemployment.

```py
# Print summary statistics for numerical columns in unemployment
print(unemployment.describe())
```
```
          2010     2011     2012     2013     2014  ...     2017     2018     2019     2020     2021
count  182.000  182.000  182.000  182.000  182.000  ...  182.000  182.000  182.000  182.000  182.000
mean     8.409    8.315    8.318    8.345    8.180  ...    7.669    7.426    7.244    8.421    8.391
std      6.249    6.267    6.367    6.416    6.284  ...    5.902    5.819    5.697    6.041    6.067
min      0.450    0.320    0.480    0.250    0.200  ...    0.140    0.110    0.100    0.210    0.260
25%      4.015    3.775    3.743    3.692    3.625  ...    3.690    3.625    3.487    4.285    4.335
50%      6.965    6.805    6.690    6.395    6.450  ...    5.650    5.375    5.240    6.695    6.425
75%     10.957   11.045   11.285   11.310   10.695  ...   10.315    9.258    9.445   11.155   10.840
max     32.020   31.380   31.020   29.000   28.030  ...   27.040   26.910   28.470   29.220   33.560

[8 rows x 12 columns]
```
---
### Counting categorical values

Recall from the previous exercise that the unemployment DataFrame contains 182 rows of country data including country_code, country_name, continent, and unemployment percentages from 2010 through 2021.

You'd now like to explore the categorical data contained in unemployment to understand the data that it contains related to each continent.

The unemployment DataFrame has been loaded for you along with pandas as pd.

**_Instructions:_**
* Use a pandas function to count the values associated with each continent in the unemployment DataFrame.

```py
# Count the values associated with each continent in unemployment
print(unemployment['continent'].value_counts())
```
```
Africa           53
Asia             47
Europe           39
North America    18
South America    12
Oceania           8
Name: continent, dtype: int64
```
---
### Global unemployment in 2021

It's time to explore some of the numerical data in unemployment! What was typical unemployment in a given year? What was the minimum and maximum unemployment rate, and what did the distribution of the unemployment rates look like across the world? A histogram is a great way to get a sense of the answers to these questions.

Your task in this exercise is to create a histogram showing the distribution of global unemployment rates in 2021.

The unemployment DataFrame has been loaded for you along with pandas as pd.

**_Instructions:_**
* Import the required visualization libraries.
* Create a histogram of the distribution of 2021 unemployment percentages across all countries in unemployment; show a full percentage point in each bin.

```py
# Import the required visualization libraries
import seaborn as sns
import matplotlib.pyplot as plt

# Create a histogram of 2021 unemployment; show a full percent in each bin
sns.histplot(data=unemployment, x="2021", binwidth=1)
plt.show()
```
