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
---
### Validating continents

Your colleague has informed you that the data on unemployment from countries in Oceania is not reliable, and you'd like to identify and exclude these countries from your unemployment data. The .isin() function can help with that!

Your task is to use .isin() to identify countries that are not in Oceania. These countries should return True while countries in Oceania should return False. This will set you up to use the results of .isin() to quickly filter out Oceania countries using Boolean indexing.

The unemployment DataFrame is available, and pandas has been imported as pd.

**_Instructions:_**
* Define a Series of Booleans describing whether or not each continent is outside of Oceania; call this Series not_oceania.
* Use Boolean indexing to print the unemployment DataFrame without any of the data related to countries in Oceania.

```py
# Define a Series describing whether each continent is outside of Oceania
not_oceania = ~unemployment["continent"].isin(["Oceania"])

# Print unemployment without records related to countries in Oceania
print(unemployment[not_oceania])
```
```
country_code          country_name      continent   2010   2011  ...   2017   2018   2019   2020   2021
0            AFG           Afghanistan           Asia  11.35  11.05  ...  11.18  11.15  11.22  11.71  13.28
1            AGO                Angola         Africa   9.43   7.36  ...   7.41   7.42   7.42   8.33   8.53
2            ALB               Albania         Europe  14.09  13.48  ...  13.62  12.30  11.47  13.33  11.82
3            ARE  United Arab Emirates           Asia   2.48   2.30  ...   2.46   2.35   2.23   3.19   3.36
4            ARG             Argentina  South America   7.71   7.18  ...   8.35   9.22   9.84  11.46  10.90
..           ...                   ...            ...    ...    ...  ...    ...    ...    ...    ...    ...
175          VNM               Vietnam           Asia   1.11   1.00  ...   1.87   1.16   2.04   2.39   2.17
178          YEM           Yemen, Rep.           Asia  12.83  13.23  ...  13.30  13.15  13.06  13.39  13.57
179          ZAF          South Africa         Africa  24.68  24.64  ...  27.04  26.91  28.47  29.22  33.56
180          ZMB                Zambia         Africa  13.19  10.55  ...  11.63  12.01  12.52  12.85  13.03
181          ZWE              Zimbabwe         Africa   5.21   5.37  ...   4.78   4.80   4.83   5.35   5.17

[174 rows x 15 columns]
```
---
### Validating range

Now it's time to validate our numerical data. We saw in the previous lesson using .describe() that the largest unemployment rate during 2021 was nearly 34 percent, while the lowest was just above zero.

Your task in this exercise is to get much more detailed information about the range of unemployment data using Seaborn's boxplot, and you'll also visualize the range of unemployment rates in each continent to understand geographical range differences.

unemployment is available, and the following have been imported for you: Seaborn as sns, matplotlib.pyplot as plt, and pandas as pd.

**_Instructions:_**
* Print the minimum and maximum unemployment rates, in that order, during 2021.
* Create a boxplot of 2021 unemployment rates, broken down by continent.

```py
# Print the minimum and maximum unemployment rates during 2021
print(unemployment['2021'].min(), unemployment['2021'].max())

# Create a boxplot of 2021 unemployment rates, broken down by continent
sns.boxplot(data = unemployment, x='2021', y = 'continent')
plt.show()
```
---
### Summaries with .groupby() and .agg()

In this exercise, you'll explore the means and standard deviations of the yearly unemployment data. First, you'll find means and standard deviations regardless of the continent to observe worldwide unemployment trends. Then, you'll check unemployment trends broken down by continent.

**_Instructions:_**
* Print the mean and standard deviation of the unemployment rates for each year.
* Print the mean and standard deviation of the unemployment rates for each year, grouped by continent.

```py
# Print the mean and standard deviation of rates by year
print(unemployment.agg(["mean", "std"]))

# Print yearly mean and standard deviation grouped by continent
print(unemployment.groupby('continent').agg(["mean", "std"]))
```
```
       2010   2011   2012   2013   2014  ...   2017   2018   2019   2020   2021
mean  8.409  8.315  8.318  8.345  8.180  ...  7.669  7.426  7.244  8.421  8.391
std   6.249  6.267  6.367  6.416  6.284  ...  5.902  5.819  5.697  6.041  6.067

[2 rows x 12 columns]

                 2010           2011           2012  ...   2019    2020           2021       
                 mean    std    mean    std    mean  ...    std    mean    std    mean    std
continent                                            ...                                     
Africa          9.344  7.411   9.369  7.402   9.241  ...  7.455  10.308  7.928  10.474  8.132
Asia            6.241  5.146   5.942  4.780   5.835  ...  5.254   7.012  5.700   6.906  5.415
Europe         11.008  6.392  10.948  6.540  11.326  ...  4.125   7.471  4.071   7.415  3.948
North America   8.663  5.116   8.563  5.377   8.449  ...  4.770   9.298  4.963   9.155  5.076
Oceania         3.623  2.055   3.647  2.008   4.104  ...  2.369   4.274  2.617   4.280  2.672
South America   6.871  2.807   6.518  2.802   6.411  ...  3.380  10.275  3.411   9.924  3.612

[6 rows x 24 columns]
```
---
### Named aggregations

You've seen how .groupby() and .agg() can be combined to show summaries across categories. Sometimes, it's helpful to name new columns when aggregating so that it's clear in the code output what aggregations are being applied and where.

Your task is to create a DataFrame called continent_summary which shows a row for each continent. The DataFrame columns will contain the mean unemployment rate for each continent in 2021 as well as the standard deviation of the 2021 employment rate. And of course, you'll rename the columns so that their contents are clear!

**_Instructions:_**
* Create a column called mean_rate_2021 which shows the mean 2021 unemployment rate for each continent.
* Create a column called std_rate_2021 which shows the standard deviation of the 2021 unemployment rate for each continent.

```py
continent_summary = unemployment.groupby("continent").agg(
    # Create the mean_rate_2021 column
    mean_rate_2021 = ('2021','mean'),
    # Create the std_rate_2021 column
    std_rate_2021 = ('2021','std')
)
print(continent_summary)
```
```
               mean_rate_2021  std_rate_2021
continent                                   
Africa                 10.474          8.132
Asia                    6.906          5.415
Europe                  7.415          3.948
North America           9.155          5.076
Oceania                 4.280          2.672
South America           9.924          3.612
```
---
### Visualizing categorical summaries

As you've learned in this chapter, Seaborn has many great visualizations for exploration, including a bar plot for displaying an aggregated average value by category of data.

In Seaborn, bar plots include a vertical bar indicating the 95% confidence interval for the categorical mean. Since confidence intervals are calculated using both the number of values and the variability of those values, they give a helpful indication of how much data can be relied upon.

Your task is to create a bar plot to visualize the means and confidence intervals of unemployment rates across the different continents.

**_Instructions:_**
* Create a bar plot showing continents on the x-axis and their respective average 2021 unemployment rates on the y-axis.

```py
# Create a bar plot of continents and their average unemployment
sns.barplot(data = unemployment, x="continent", y="2021")
plt.show()
```
---
## Addressing missing data
---
### Dealing with missing data

It is important to deal with missing data before starting your analysis.

One approach is to drop missing values if they account for a small proportion, typically five percent, of your data.

Working with a dataset on plane ticket prices, stored as a pandas DataFrame called planes, you'll need to count the number of missing values across all columns, calculate five percent of all values, use this threshold to remove observations, and check how many missing values remain in the dataset.

**_Instructions:_**
* Print the number of missing values in each column of the DataFrame.
* Calculate how many observations five percent of the planes DataFrame is equal to.
* Create cols_to_drop by applying boolean indexing to columns of the DataFrame with missing values less than or equal to the threshold. Use this filter to remove missing values and save the updated DataFrame.

```py
# Count the number of missing values in each column
print(planes.isna().sum())

# Find the five percent threshold
threshold = len(planes) * 0.05

# Create a filter
cols_to_drop = planes.columns[planes.isna().sum() <= threshold]

# Drop missing values for columns below the threshold
planes.dropna(subset=cols_to_drop, inplace=True)

print(planes.isna().sum())
```
```
Airline            427
Date_of_Journey    322
Source             187
Destination        347
Route              256
Dep_Time           260
Arrival_Time       194
Duration           214
Total_Stops        212
Additional_Info    589
Price              616
dtype: int64
Airline              0
Date_of_Journey      0
Source               0
Destination          0
Route                0
Dep_Time             0
Arrival_Time         0
Duration             0
Total_Stops          0
Additional_Info    300
Price              368
dtype: int64
```
---
### Strategies for remaining missing data

The five percent rule has worked nicely for your planes dataset, eliminating missing values from nine out of 11 columns!

Now, you need to decide what to do with the "Additional_Info" and "Price" columns, which are missing 300 and 368 values respectively.

You'll first take a look at what "Additional_Info" contains, then visualize the price of plane tickets by different airlines.

The following imports have been made for you:

```
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
```

**_Instructions:_**
* Print the values and frequencies of "Additional_Info".
* Create a boxplot of "Price" by "Airline".

```py
# Check the values of the Additional_Info column
print(planes["Additional_Info"].value_counts())

# Create a box plot of Price by Airline
sns.boxplot(data=planes, x='Airline', y='Price')

plt.show()
```
```
No info                         6399
In-flight meal not included     1525
No check-in baggage included     258
1 Long layover                    14
Change airports                    7
No Info                            2
Business class                     1
Red-eye flight                     1
2 Long layover                     1
Name: Additional_Info, dtype: int64
```
---
### Imputing missing plane prices

Now there's just one column with missing values left!

You've removed the "Additional_Info" column from planes—the last step is to impute the missing data in the "Price" column of the dataset.

As a reminder, you generated this boxplot, which suggested that imputing the median price based on the "Airline" is a solid approach!

**_Instructions:_**
* Group planes by airline and calculate the median price.
* Convert the grouped median prices to a dictionary.
* Conditionally impute missing values for "Price" by mapping values in the "Airline column" based on prices_dict. Check for remaining missing values.

```py
# Calculate median plane ticket prices by Airline
airline_prices = planes.groupby("Airline")["Price"].median()

print(airline_prices)

# Convert to a dictionary
prices_dict = airline_prices.to_dict()

# Map the dictionary to the missing values
planes["Price"] = planes["Price"].fillna(planes["Airline"].map(prices_dict))

# Check for missing values
print(planes.isna().sum())
```
```
Airline
Air Asia              5192.0
Air India             9443.0
GoAir                 5003.5
IndiGo                5054.0
Jet Airways          11507.0
Multiple carriers    10197.0
SpiceJet              3873.0
Vistara               8028.0
Name: Price, dtype: float64
Airline            0
Date_of_Journey    0
Source             0
Destination        0
Route              0
Dep_Time           0
Arrival_Time       0
Duration           0
Total_Stops        0
Price              0
dtype: int64
```
