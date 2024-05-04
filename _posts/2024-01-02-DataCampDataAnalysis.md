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
---
### Finding the number of unique values

You would like to practice some of the categorical data manipulation and analysis skills that you've just seen. To help identify which data could be reformatted to extract value, you are going to find out which non-numeric columns in the planes dataset have a large number of unique values.

**_Instructions:_**
* Filter planes for columns that are of "object" data type.
* Loop through the columns in the dataset.
* Add the column iterator to the print statement, then call the function to return the number of unique values in the column.

```py
# Filter the DataFrame for object columns
non_numeric = planes.select_dtypes("object")

# Loop through columns
for col in non_numeric.columns:

  # Print the number of unique values
  print(f"Number of unique values in {col} column: ", non_numeric[col].nunique())
```
---
### Flight duration categories

As you saw, there are 362 unique values in the "Duration" column of planes. Calling planes["Duration"].head(), we see the following values:
```
0        19h
1     5h 25m
2     4h 45m
3     2h 25m
4    15h 30m
Name: Duration, dtype: object
```

Looks like this won't be simple to convert to numbers. However, you could categorize flights by duration and examine the frequency of different flight lengths!

You'll create a "Duration_Category" column in the planes DataFrame. Before you can do this you'll need to create a list of the values you would like to insert into the DataFrame, followed by the existing values that these should be created from.

**_Instructions:_**
* Create a list of categories containing "Short-haul", "Medium", and "Long-haul".
* Create short_flights, a string to capture values of "0h", "1h", "2h", "3h", or "4h" taking care to avoid values such as "10h".
* Create medium_flights to capture any values between five and nine hours. Create long_flights to capture any values from 10 hours to 16 hours inclusive.

```py
# Create a list of categories
flight_categories = ["Short-haul", "Medium", "Long-haul"]

# Create short-haul values
short_flights = "^0h|^1h|^2h|^3h|^4h"

# Create medium-haul values
medium_flights = "^5h|^6h|^7h|^8h|^9h"

# Create long-haul values
long_flights = "10h|11h|12h|13h|14h|15h|16h"
```
---
### Adding duration categories

Now that you've set up the categories and values you want to capture, it's time to build a new column to analyze the frequency of flights by duration!

The variables flight_categories, short_flights, medium_flights, and long_flights that you previously created are available to you.

**_Instructions:_**
* Create conditions, a list containing subsets of planes["Duration"] based on short_flights, medium_flights, and long_flights.
* Create the "Duration_Category" column by calling a function that accepts your conditions list and flight_categories, setting values not found to "Extreme duration".
* Create a plot showing the count of each category.

```py
# Create conditions for values in flight_categories to be created
conditions = [
    (planes["Duration"].str.contains(short_flights)),
    (planes["Duration"].str.contains(medium_flights)),
    (planes["Duration"].str.contains(long_flights))
]

# Apply the conditions list to the flight_categories
planes["Duration_Category"] = np.select(conditions, flight_categories,default="Extreme duration")

# Plot the counts of each category
sns.countplot(data=planes, x="Duration_Category")
plt.show()
```
---
### Flight duration

You would like to analyze the duration of flights, but unfortunately, the "Duration" column in the planes DataFrame currently contains string values.

You'll need to clean the column and convert it to the correct data type for analysis.

**_Instructions:_**
* Print the first five values of the "Duration" column.
* Remove "h" from the column.
* Convert the column to float data type. Plot a histogram of "Duration" values.

```py
# Preview the column
print(planes["Duration"].head())

# Remove the string character
planes["Duration"] = planes["Duration"].str.replace("h", "")

# Convert to float data type
planes["Duration"] = planes["Duration"].astype(float)

# Plot a histogram
sns.histplot(data = planes, x = "Duration")
plt.show()
```
---
### Adding descriptive statistics

Now "Duration" and "Price" both contain numeric values in the planes DataFrame, you would like to calculate summary statistics for them that are conditional on values in other columns.

**_Instructions:_**
* Add a column to planes containing the standard deviation of "Price" based on "Airline".

```py
# Price standard deviation by Airline
planes["airline_price_st_dev"] = planes.groupby("Airline")["Price"].transform(lambda x: x.std())

print(planes[["Airline", "airline_price_st_dev"]].value_counts())
```
```
Airline            airline_price_st_dev
Jet Airways        4230.749                3685
IndiGo             2266.754                1981
Air India          3865.872                1686
Multiple carriers  3763.675                1148
SpiceJet           1790.852                 787
Vistara            2864.268                 455
Air Asia           2016.739                 309
GoAir              2790.815                 182
dtype: int64
```

**_Instructions:_**
* Calculate the median for "Duration" by "Airline", storing it as a column called "airline_median_duration".

```py
# Median Duration by Airline
planes["airline_median_duration"] = planes.groupby("Airline")["Duration"].transform(lambda x: x.median())

print(planes[["Airline","airline_median_duration"]].value_counts())
```
```
Airline            airline_median_duration
Jet Airways        13.333                     3685
IndiGo             2.917                      1981
Air India          15.917                     1686
Multiple carriers  10.250                     1148
SpiceJet           2.500                       787
Vistara            3.167                       455
Air Asia           2.833                       309
GoAir              5.167                       182
dtype: int64
```

**_Instructions:_**
* Find the mean "Price" by "Destination", saving it as a column called "price_destination_mean".

```py
# Mean Price by Destination
planes["price_destination_mean"] = planes.groupby("Destination")["Price"].transform(lambda x: x.mean())

print(planes[["Destination","price_destination_mean"]].value_counts())
```
```
Destination  price_destination_mean
Cochin       10506.993                 4391
Banglore     9132.225                  2773
Delhi        5157.794                  1219
New Delhi    11738.589                  888
Hyderabad    5025.210                   673
Kolkata      4801.490                   369
dtype: int64
```
---
### Identifying outliers

You've proven that you recognize what to do when presented with outliers, but can you identify them using visualizations?

Try to figure out if there are outliers in the "Price" or "Duration" columns of the planes DataFrame.

matplotlib.pyplot and seaborn have been imported for you as plt and sns respectively.

**_Instructions:_**
* Plot the distribution of "Price" column from planes.
* Display the descriptive statistics for flight duration.
*

```py
# Plot a histogram of flight prices
sns.histplot(data=planes, x="Price")
plt.show()

# Display descriptive statistics for flight duration
print(planes["Duration"].describe())
```
```
count    10446.000
mean        10.724
std          8.472
min          0.083
25%          2.833
50%          8.667
75%         15.500
max         47.667
Name: Duration, dtype: float64
```
---
### Removing outliers

While removing outliers isn't always the way to go, for your analysis, you've decided that you will only include flights where the "Price" is not an outlier.

Therefore, you need to find the upper threshold and then use it to remove values above this from the planes DataFrame.

**_Instructions:_**
* Find the 75th and 25th percentiles, saving as price_seventy_fifth and price_twenty_fifth respectively.
* Calculate the IQR, storing it as prices_iqr.
* Calculate the upper and lower outlier thresholds. Remove the outliers from planes.

```py
# Find the 75th and 25th percentiles
price_seventy_fifth = planes["Price"].quantile(0.75)
price_twenty_fifth = planes["Price"].quantile(0.25)

# Calculate iqr
prices_iqr = price_upper_perc - price_lower_perc

# Calculate the thresholds
upper = price_seventy_fifth + (1.5 * prices_iqr)
lower = price_twenty_fifth - (1.5 * prices_iqr)

# Subset the data
planes = planes[(planes["Price"] > lower) & (planes["Price"] < upper)]

print(planes["Price"].describe())
```
```
count     9959.000
mean      8875.161
std       4057.202
min       1759.000
25%       5228.000
50%       8283.000
75%      12284.000
max      23001.000
Name: Price, dtype: float64
```
---
## Relationships in Data
---
### Importing DateTime data

You'll now work with the entire divorce dataset! The data describes Mexican marriages dissolved between 2000 and 2015. It contains marriage and divorce dates, education level, birthday, income for each partner, and marriage duration, as well as the number of children the couple had at the time of divorce.

The column names and data types are as follows:

```
divorce_date          object
dob_man               object
education_man         object
income_man           float64
dob_woman             object
education_woman       object
income_woman         float64
marriage_date         object
marriage_duration    float64
num_kids             float64
```
It looks like there is a lot of date information in this data that is not yet a DateTime data type! Your task is to fix that so that you can explore patterns over time.

**_Instructions:_**
* Import divorce.csv, saving as a DataFrame, divorce; indicate in the import function that the divorce_date, dob_man, dob_woman, and marriage_date columns should be imported as DateTime values.

```py
# Import divorce.csv, parsing the appropriate columns as dates in the import
divorce = pd.read_csv('divorce.csv', parse_dates=["divorce_date", "dob_man", "dob_woman", "marriage_date"])
print(divorce.dtypes)
```
---
### Updating data type to DateTime

Now, the divorce DataFrame has been loaded for you, but one column is stored as a string that should be DateTime data. Which one is it? Once you've identified the column, you'll update it so that you can explore it more closely in the next exercise.

**_Instructions:_**
* Convert the marriage_date column of the divorce DataFrame to DateTime values.

```py
# Convert the marriage_date column to DateTime values
divorce["marriage_date"] = pd.to_datetime(divorce["marriage_date"])
```
---
### Visualizing relationships over time

Now that your date data is saved as DateTime data, you can explore patterns over time! Does the year that a couple got married have a relationship with the number of children that the couple has at the time of divorce? Your task is to find out!

The divorce DataFrame (with all dates formatted as DateTime data types) has been loaded for you. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns.

**_Instructions:_**
* Define a column called marriage_year, which contains just the year portion of the marriage_date column.
* Create a line plot showing the average number of kids a couple had during their marriage, arranged by the year that the couple got married.

```py
# Define the marriage_year column
divorce["marriage_year"] = divorce["marriage_date"].dt.year

# Create a line plot showing the average number of kids by year
sns.lineplot(data=divorce, x="marriage_year", y ="num_kids")
plt.show()
```
---
### Visualizing variable relationships

In the last exercise, you may have noticed that a longer marriage_duration is correlated with having more children, represented by the num_kids column. The correlation coefficient between the marriage_duration and num_kids variables is 0.45.

In this exercise, you'll create a scatter plot to visualize the relationship between these variables. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns.

**_Instructions:_**
* Create a scatterplot showing marriage_duration on the x-axis and num_kids on the y-axis.

```py
# Create the scatterplot
sns.scatterplot(data=divorce, x='marriage_duration',y='num_kids')
plt.show()
```
---
### Visualizing multiple variable relationships

Seaborn's .pairplot() is excellent for understanding the relationships between several or all variables in a dataset by aggregating pairwise scatter plots in one visual.

Your task is to use a pairplot to compare the relationship between marriage_duration and income_woman. pandas has been loaded as pd, matplotlib.pyplot has been loaded as plt, and Seaborn has been loaded as sns.

**_Instructions:_**
* Create a pairplot to visualize the relationships between income_woman and marriage_duration in the divorce DataFrame.

```py
# Create a pairplot for income_woman and marriage_duration
sns.pairplot(data=divorce, vars=["income_woman","marriage_duration"])
plt.show()
```
---
### Categorial data in scatter plots

In the video, we explored how men's education and age at marriage related to other variables in our dataset, the divorce DataFrame. Now, you'll take a look at how women's education and age at marriage relate to other variables!

Your task is to create a scatter plot of each woman's age and income, layering in the categorical variable of education level for additional context.

**_Instructions:_**
* Create a scatter plot that shows woman_age_marriage on the x-axis and income_woman on the y-axis; each data point should be colored based on the woman's level of education, represented by education_woman.

```py
# Create the scatter plot
sns.scatterplot(data=divorce, x='woman_age_marriage', y='income_woman', hue='education_woman')
plt.show()
```
---
### Exploring with KDE plots

Kernel Density Estimate (KDE) plots are a great alternative to histograms when you want to show multiple distributions in the same visual.

Suppose you are interested in the relationship between marriage duration and the number of kids that a couple has. Since values in the num_kids column range only from one to five, you can plot the KDE for each value on the same plot.

**_Instructions:_**
* Create a KDE plot that shows marriage_duration on the x-axis and a different colored line for each possible number of children that a couple might have, represented by num_kids.
* Update the code for the KDE plot from the previous step to show a cumulative distribution function for each number of children a couple has.

```py
# Update the KDE plot to show a cumulative distribution function
sns.kdeplot(data=divorce, x="marriage_duration", hue="num_kids", cut=0, cumulative=True)
plt.show()
```
---
## Turning Exploratory Analysis into Action
---
### Checking for class imbalance

The 2022 Kaggle Survey captures information about data scientists' backgrounds, preferred technologies, and techniques. It is seen as an accurate view of what is happening in data science based on the volume and profile of responders.

**_Instructions:_**
* Print the relative frequency of the "Job_Category" column from salaries DataFrame.

```py
# Print the relative frequency of Job_Category
print(salaries['Job_Category'].value_counts(normalize=True))
```
```
Data Science        0.278
Data Engineering    0.273
Data Analytics      0.226
Machine Learning    0.120
Other               0.069
Managerial          0.034
Name: Job_Category, dtype: float64
```
---
### Cross-tabulation

Cross-tabulation can help identify how observations occur in combination.

Using the salaries dataset, which has been imported as a pandas DataFrame, you'll perform cross-tabulation on multiple variables, including the use of aggregation, to see the relationship between "Company_Size" and other variables.

**_Instructions:_**
* Perform cross-tabulation, setting "Company_Size" as the index, and the columns to classes in "Experience".
* Cross-tabulate "Job_Category" and classes of "Company_Size" as column names.
* Update pd.crosstab() to return the mean "Salary_USD" values.

```py
# Cross-tabulate Company_Size and Experience
print(pd.crosstab(salaries["Company_Size"], salaries["Experience"]))

# Cross-tabulate Job_Category and Company_Size
print(pd.crosstab(salaries["Job_Category"], salaries["Company_Size"]))

# Cross-tabulate Job_Category and Company_Size
print(pd.crosstab(salaries["Job_Category"], salaries["Company_Size"],
            values=salaries["Salary_USD"], aggfunc="mean"))
```
```
Experience    EN  EX  MI   SE
Company_Size                 
L             24   7  49   44
M             25   9  58  136
S             18   1  21   15

Company_Size       L   M   S
Job_Category                
Data Analytics    23  61   8
Data Engineering  28  72  11
Data Science      38  59  16
Machine Learning  17  19  13
Managerial         5   8   1
Other             13   9   6

Company_Size               L           M          S
Job_Category                                       
Data Analytics    112851.749   95912.685  53741.877
Data Engineering  118939.035  121287.061  86927.136
Data Science       96489.520  116044.456  62241.749
Machine Learning  140779.492  100794.237  78812.586
Managerial        190551.449  150713.628  31484.700
Other              92873.911   89750.579  69871.248
```
