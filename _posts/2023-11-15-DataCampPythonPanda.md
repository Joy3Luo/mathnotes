---
layout: post
title: DataCamp Data Manipulation with pandas
date: 2023-11-15 11:18 +0800
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

pandas is the world’s most popular Python library, used for everything from data manipulation to data analysis. In this course, you’ll learn how to manipulate DataFrames, as you extract, filter, and transform real-world datasets for analysis. Using pandas you’ll explore all the core data science concepts. Using real-world data, including Walmart sales figures and global temperature time series, you’ll learn how to import, clean, calculate statistics, and create visualizations—using pandas to add to the power of Python!

## Transforming DataFrames

Let’s master the pandas basics. Learn how to inspect DataFrames and perform fundamental manipulations, including sorting rows, subsetting, and adding new columns.

---
### Inspecting a DataFrame

When you get a new DataFrame to work with, the first thing you need to do is explore it and see what it contains. There are several useful methods and attributes for this.

* .head() returns the first few rows (the “head” of the DataFrame).
* .info() shows information on each of the columns, such as the data type and number of missing values.
* .shape returns the number of rows and columns of the DataFrame.
* .describe() calculates a few summary statistics for each column.

homelessness is a DataFrame containing estimates of homelessness in each U.S. state in 2018. The individual column is the number of homeless individuals not part of a family with children. The family_members column is the number of homeless individuals part of a family with children. The state_pop column is the state's total population.

pandas is imported for you.



**_Instructions:_**
* Print the head of the homelessness DataFrame.
* Print information about the column types and missing values in homelessness.
* Print the number of rows and columns in homelessness.
* Print some summary statistics that describe the homelessness DataFrame.

```py
# Print the head of the homelessness data
print(homelessness.head())

# Print information about homelessness
print(homelessness.info())

# Print the shape of homelessness
print(homelessness.shape)

# Print a description of homelessness
print(homelessness.describe())
```
```
              region        state  individuals  family_members  state_pop
0  East South Central     Alabama       2570.0           864.0    4887681
1             Pacific      Alaska       1434.0           582.0     735139
2            Mountain     Arizona       7259.0          2606.0    7158024
3  West South Central    Arkansas       2280.0           432.0    3009733
4             Pacific  California     109008.0         20964.0   39461588
<class 'pandas.core.frame.DataFrame'>
Int64Index: 51 entries, 0 to 50
Data columns (total 5 columns):
#   Column          Non-Null Count  Dtype  
---  ------          --------------  -----  
0   region          51 non-null     object
1   state           51 non-null     object
2   individuals     51 non-null     float64
3   family_members  51 non-null     float64
4   state_pop       51 non-null     int64  
dtypes: float64(2), int64(1), object(2)
memory usage: 2.4+ KB
None
(51, 5)
individuals  family_members  state_pop
count       51.000          51.000  5.100e+01
mean      7225.784        3504.882  6.406e+06
std      15991.025        7805.412  7.327e+06
min        434.000          75.000  5.776e+05
25%       1446.500         592.000  1.777e+06
50%       3082.000        1482.000  4.461e+06
75%       6781.500        3196.000  7.341e+06
max     109008.000       52070.000  3.946e+07
```
---
### Parts of a DataFrame

To better understand DataFrame objects, it's useful to know that they consist of three components, stored as attributes:

* .values: A two-dimensional NumPy array of values.
* .columns: An index of columns: the column names.
* .index: An index for the rows: either row numbers or row names.

You can usually think of indexes as a list of strings or numbers, though the pandas Index data type allows for more sophisticated options. (These will be covered later in the course.)

**_Instructions:_**
* Import pandas using the alias pd.
* Print a 2D NumPy array of the values in homelessness.
* Print the column names of homelessness.
* Print the index of homelessness.

```py
# Import pandas using the alias pd
import pandas as pd

# Print the values of homelessness
print(homelessness.values)

# Print the column index of homelessness
print(homelessness.columns)

# Print the row index of homelessness
print(homelessness.index)
```
```
[['East South Central' 'Alabama' 2570.0 864.0 4887681]
 ['Pacific' 'Alaska' 1434.0 582.0 735139]
 ['Mountain' 'Arizona' 7259.0 2606.0 7158024]
 ['West South Central' 'Arkansas' 2280.0 432.0 3009733]
 ['Pacific' 'California' 109008.0 20964.0 39461588]
 ['Mountain' 'Colorado' 7607.0 3250.0 5691287]
 ['New England' 'Connecticut' 2280.0 1696.0 3571520]
 ['South Atlantic' 'Delaware' 708.0 374.0 965479]
 ['South Atlantic' 'District of Columbia' 3770.0 3134.0 701547]
 ['South Atlantic' 'Florida' 21443.0 9587.0 21244317]
 ['South Atlantic' 'Georgia' 6943.0 2556.0 10511131]
 ['Pacific' 'Hawaii' 4131.0 2399.0 1420593]
 ['Mountain' 'Idaho' 1297.0 715.0 1750536]
 ['East North Central' 'Illinois' 6752.0 3891.0 12723071]
 ['East North Central' 'Indiana' 3776.0 1482.0 6695497]
 ['West North Central' 'Iowa' 1711.0 1038.0 3148618]
 ['West North Central' 'Kansas' 1443.0 773.0 2911359]
 ['East South Central' 'Kentucky' 2735.0 953.0 4461153]
 ['West South Central' 'Louisiana' 2540.0 519.0 4659690]
 ['New England' 'Maine' 1450.0 1066.0 1339057]
 ['South Atlantic' 'Maryland' 4914.0 2230.0 6035802]
 ['New England' 'Massachusetts' 6811.0 13257.0 6882635]
 ['East North Central' 'Michigan' 5209.0 3142.0 9984072]
 ['West North Central' 'Minnesota' 3993.0 3250.0 5606249]
 ['East South Central' 'Mississippi' 1024.0 328.0 2981020]
 ['West North Central' 'Missouri' 3776.0 2107.0 6121623]
 ['Mountain' 'Montana' 983.0 422.0 1060665]
 ['West North Central' 'Nebraska' 1745.0 676.0 1925614]
 ['Mountain' 'Nevada' 7058.0 486.0 3027341]
 ['New England' 'New Hampshire' 835.0 615.0 1353465]
 ['Mid-Atlantic' 'New Jersey' 6048.0 3350.0 8886025]
 ['Mountain' 'New Mexico' 1949.0 602.0 2092741]
 ['Mid-Atlantic' 'New York' 39827.0 52070.0 19530351]
 ['South Atlantic' 'North Carolina' 6451.0 2817.0 10381615]
 ['West North Central' 'North Dakota' 467.0 75.0 758080]
 ['East North Central' 'Ohio' 6929.0 3320.0 11676341]
 ['West South Central' 'Oklahoma' 2823.0 1048.0 3940235]
 ['Pacific' 'Oregon' 11139.0 3337.0 4181886]
 ['Mid-Atlantic' 'Pennsylvania' 8163.0 5349.0 12800922]
 ['New England' 'Rhode Island' 747.0 354.0 1058287]
 ['South Atlantic' 'South Carolina' 3082.0 851.0 5084156]
 ['West North Central' 'South Dakota' 836.0 323.0 878698]
 ['East South Central' 'Tennessee' 6139.0 1744.0 6771631]
 ['West South Central' 'Texas' 19199.0 6111.0 28628666]
 ['Mountain' 'Utah' 1904.0 972.0 3153550]
 ['New England' 'Vermont' 780.0 511.0 624358]
 ['South Atlantic' 'Virginia' 3928.0 2047.0 8501286]
 ['Pacific' 'Washington' 16424.0 5880.0 7523869]
 ['South Atlantic' 'West Virginia' 1021.0 222.0 1804291]
 ['East North Central' 'Wisconsin' 2740.0 2167.0 5807406]
 ['Mountain' 'Wyoming' 434.0 205.0 577601]]
Index(['region', 'state', 'individuals', 'family_members', 'state_pop'], dtype='object')
Int64Index([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48,
            49, 50],
           dtype='int64')
```
---
### Sorting rows

Finding interesting bits of data in a DataFrame is often easier if you change the order of the rows. You can sort the rows by passing a column name to .sort_values().

In cases where rows have the same value (this is common if you sort on a categorical variable), you may wish to break the ties by sorting on another column. You can sort on multiple columns in this way by passing a list of column names.

Sort on one column
`df.sort_values("breed")`

Sort on multiple columns
`df.sort_values(["breed", "weight_kg"])`

By combining .sort_values() with .head(), you can answer questions in the form, "What are the top cases where…?".

**_Instructions:_**
* Sort homelessness by the number of homeless individuals, from smallest to largest, and save this as homelessness_ind.
Print the head of the sorted DataFrame.

```py
# Sort homelessness by individuals
homelessness_ind = homelessness.sort_values('individuals')

# Print the top few rows
print(homelessness_ind.head())
```
```
                region         state  individuals  family_members  state_pop
50            Mountain       Wyoming        434.0           205.0     577601
34  West North Central  North Dakota        467.0            75.0     758080
7       South Atlantic      Delaware        708.0           374.0     965479
39         New England  Rhode Island        747.0           354.0    1058287
45         New England       Vermont        780.0           511.0     624358
```

**_Instructions:_**
* Sort homelessness by the number of homeless family_members in descending order, and save this as homelessness_fam.
Print the head of the sorted DataFrame.

```py
# Sort homelessness by descending family members
homelessness_fam = homelessness.sort_values('family_members', ascending = False)

# Print the top few rows
print(homelessness_fam.head())
```
```
                region          state  individuals  family_members  state_pop
32        Mid-Atlantic       New York      39827.0         52070.0   19530351
4              Pacific     California     109008.0         20964.0   39461588
21         New England  Massachusetts       6811.0         13257.0    6882635
9       South Atlantic        Florida      21443.0          9587.0   21244317
43  West South Central          Texas      19199.0          6111.0   28628666
```

**_Instructions:_**
* Sort homelessness first by region (ascending), and then by number of family members (descending). Save this as homelessness_reg_fam.
Print the head of the sorted DataFrame.

```py
# Sort homelessness by region, then descending family members
homelessness_reg_fam = homelessness.sort_values(['region','family_members'], ascending = [True, False])
# Print the top few rows
print(homelessness_reg_fam.head())
```
```
                region      state  individuals  family_members  state_pop
13  East North Central   Illinois       6752.0          3891.0   12723071
35  East North Central       Ohio       6929.0          3320.0   11676341
22  East North Central   Michigan       5209.0          3142.0    9984072
49  East North Central  Wisconsin       2740.0          2167.0    5807406
14  East North Central    Indiana       3776.0          1482.0    6695497
```
---
### Subsetting columns

When working with data, you may not need all of the variables in your dataset. Square brackets ([]) can be used to select only the columns that matter to you in an order that makes sense to you. To select only "col_a" of the DataFrame df, use `df["col_a"]`

To select "col_a" and "col_b" of df, use `df[["col_a", "col_b"]]`

**_Instructions:_**
* Create a DataFrame called individuals that contains only the individuals column of homelessness.
Print the head of the result.

```py
# Select the individuals column
individuals = homelessness['individuals']

# Print the head of the result
print(individuals.head())
```
```
0      2570.0
1      1434.0
2      7259.0
3      2280.0
4    109008.0
Name: individuals, dtype: float64
```
**_Instructions:_**
* Create a DataFrame called state_fam that contains only the state and family_members columns of homelessness, in that order.
Print the head of the result.

```py
# Select the state and family_members columns
state_fam = homelessness[['state','family_members']]

# Print the head of the result
print(state_fam.head())
```
```
        state  family_members
0     Alabama           864.0
1      Alaska           582.0
2     Arizona          2606.0
3    Arkansas           432.0
4  California         20964.0
```
**_Instructions:_**
* Create a DataFrame called ind_state that contains the individuals and state columns of homelessness, in that order.
Print the head of the result.

```py
# Select only the individuals and state columns, in that order
ind_state = homelessness[['individuals','state']]

# Print the head of the result
print(ind_state.head())
```
```
   individuals       state
0       2570.0     Alabama
1       1434.0      Alaska
2       7259.0     Arizona
3       2280.0    Arkansas
4     109008.0  California
```
---
### Subsetting rows

A large part of data science is about finding which bits of your dataset are interesting. One of the simplest techniques for this is to find a subset of rows that match some criteria. This is sometimes known as filtering rows or selecting rows.

There are many ways to subset a DataFrame, perhaps the most common is to use relational operators to return True or False for each row, then pass that inside square brackets.

```
dogs[dogs["height_cm"] > 60]
dogs[dogs["color"] == "tan"]
```

You can filter for multiple conditions at once by using the "bitwise and" operator, &.

`dogs[(dogs["height_cm"] > 60) & (dogs["color"] == "tan")]`

**_Instructions:_**
* Filter homelessness for cases where the number of individuals is greater than ten thousand, assigning to ind_gt_10k. View the printed result.

```py
# Filter for rows where individuals is greater than 10000
ind_gt_10k = homelessness[homelessness['individuals']> 10000]

# See the result
print(ind_gt_10k)
```
```
                region       state  individuals  family_members  state_pop
4              Pacific  California     109008.0         20964.0   39461588
9       South Atlantic     Florida      21443.0          9587.0   21244317
32        Mid-Atlantic    New York      39827.0         52070.0   19530351
37             Pacific      Oregon      11139.0          3337.0    4181886
43  West South Central       Texas      19199.0          6111.0   28628666
47             Pacific  Washington      16424.0          5880.0    7523869
```
**_Instructions:_**
* Filter homelessness for cases where the USA Census region is "Mountain", assigning to mountain_reg. View the printed result.

```py
# Filter for rows where region is Mountain
mountain_reg = homelessness[homelessness['region']=='Mountain']

# See the result
print(mountain_reg)
```
```
      region       state  individuals  family_members  state_pop
2   Mountain     Arizona       7259.0          2606.0    7158024
5   Mountain    Colorado       7607.0          3250.0    5691287
12  Mountain       Idaho       1297.0           715.0    1750536
26  Mountain     Montana        983.0           422.0    1060665
28  Mountain      Nevada       7058.0           486.0    3027341
31  Mountain  New Mexico       1949.0           602.0    2092741
44  Mountain        Utah       1904.0           972.0    3153550
50  Mountain     Wyoming        434.0           205.0     577601
```
**_Instructions:_**
* Filter homelessness for cases where the number of family_members is less than one thousand and the region is "Pacific", assigning to fam_lt_1k_pac. View the printed result.

```py
# Filter for rows where family_members is less than 1000
# and region is Pacific
fam_lt_1k_pac = homelessness[(homelessness['family_members']<1000) & (homelessness['region'] == 'Pacific')]

# See the result
print(fam_lt_1k_pac)
```
```
region   state  individuals  family_members  state_pop
1  Pacific  Alaska       1434.0           582.0     735139
```
---
### Subsetting rows by categorical variables

Subsetting data based on a categorical variable often involves using the "or" operator (|) to select rows from multiple categories. This can get tedious when you want all states in one of three different regions, for example. Instead, use the .isin() method, which will allow you to tackle this problem by writing one condition instead of three separate ones.

```
colors = ["brown", "black", "tan"]
condition = dogs["color"].isin(colors)
dogs[condition]
```

**_Instructions:_**
* Filter homelessness for cases where the USA census region is "South Atlantic" or it is "Mid-Atlantic", assigning to south_mid_atlantic. View the printed result.

```py
# Subset for rows in South Atlantic or Mid-Atlantic regions
set = ['South Atlantic', 'Mid-Atlantic']
south_mid_atlantic = homelessness[homelessness['region'].isin(set)]

# See the result
print(south_mid_atlantic)
```
```
            region                 state  individuals  family_members  state_pop
7   South Atlantic              Delaware        708.0           374.0     965479
8   South Atlantic  District of Columbia       3770.0          3134.0     701547
9   South Atlantic               Florida      21443.0          9587.0   21244317
10  South Atlantic               Georgia       6943.0          2556.0   10511131
20  South Atlantic              Maryland       4914.0          2230.0    6035802
30    Mid-Atlantic            New Jersey       6048.0          3350.0    8886025
32    Mid-Atlantic              New York      39827.0         52070.0   19530351
33  South Atlantic        North Carolina       6451.0          2817.0   10381615
38    Mid-Atlantic          Pennsylvania       8163.0          5349.0   12800922
40  South Atlantic        South Carolina       3082.0           851.0    5084156
46  South Atlantic              Virginia       3928.0          2047.0    8501286
48  South Atlantic         West Virginia       1021.0           222.0    1804291
```
**_Instructions:_**
* Filter homelessness for cases where the USA census state is in the list of Mojave states, canu, assigning to mojave_homelessness. View the printed result.

```py
# The Mojave Desert states
canu = ["California", "Arizona", "Nevada", "Utah"]

# Filter for rows in the Mojave Desert states
mojave_homelessness = homelessness[homelessness['state'].isin(canu)]

# See the result
print(mojave_homelessness)
```
```
      region       state  individuals  family_members  state_pop
2   Mountain     Arizona       7259.0          2606.0    7158024
4    Pacific  California     109008.0         20964.0   39461588
28  Mountain      Nevada       7058.0           486.0    3027341
44  Mountain        Utah       1904.0           972.0    3153550
```
---
### Adding new columns

You aren't stuck with just the data you are given. Instead, you can add new columns to a DataFrame. This has many names, such as transforming, mutating, and feature engineering.

You can create new columns from scratch, but it is also common to derive them from other columns, for example, by adding columns together or by changing their units.

**_Instructions:_**
* Add a new column to homelessness, named total, containing the sum of the individuals and family_members columns.
* Add another column to homelessness, named p_individuals, containing the proportion of homeless people in each state who are individuals.

```py
# Add total col as sum of individuals and family_members
homelessness['total'] = homelessness['individuals']+homelessness['family_members']

# Add p_individuals col as proportion of total that are individuals
homelessness['p_individuals'] = homelessness['individuals'] / homelessness['total']

# See the result
print(homelessness)
```
```
               region                 state  individuals  family_members  state_pop     total  p_individuals
0   East South Central               Alabama       2570.0           864.0    4887681    3434.0          0.748
1              Pacific                Alaska       1434.0           582.0     735139    2016.0          0.711
2             Mountain               Arizona       7259.0          2606.0    7158024    9865.0          0.736
3   West South Central              Arkansas       2280.0           432.0    3009733    2712.0          0.841
4              Pacific            California     109008.0         20964.0   39461588  129972.0          0.839
5             Mountain              Colorado       7607.0          3250.0    5691287   10857.0          0.701
6          New England           Connecticut       2280.0          1696.0    3571520    3976.0          0.573
7       South Atlantic              Delaware        708.0           374.0     965479    1082.0          0.654
8       South Atlantic  District of Columbia       3770.0          3134.0     701547    6904.0          0.546
9       South Atlantic               Florida      21443.0          9587.0   21244317   31030.0          0.691
10      South Atlantic               Georgia       6943.0          2556.0   10511131    9499.0          0.731
11             Pacific                Hawaii       4131.0          2399.0    1420593    6530.0          0.633
12            Mountain                 Idaho       1297.0           715.0    1750536    2012.0          0.645
13  East North Central              Illinois       6752.0          3891.0   12723071   10643.0          0.634
14  East North Central               Indiana       3776.0          1482.0    6695497    5258.0          0.718
15  West North Central                  Iowa       1711.0          1038.0    3148618    2749.0          0.622
16  West North Central                Kansas       1443.0           773.0    2911359    2216.0          0.651
17  East South Central              Kentucky       2735.0           953.0    4461153    3688.0          0.742
18  West South Central             Louisiana       2540.0           519.0    4659690    3059.0          0.830
19         New England                 Maine       1450.0          1066.0    1339057    2516.0          0.576
20      South Atlantic              Maryland       4914.0          2230.0    6035802    7144.0          0.688
21         New England         Massachusetts       6811.0         13257.0    6882635   20068.0          0.339
22  East North Central              Michigan       5209.0          3142.0    9984072    8351.0          0.624
23  West North Central             Minnesota       3993.0          3250.0    5606249    7243.0          0.551
24  East South Central           Mississippi       1024.0           328.0    2981020    1352.0          0.757
25  West North Central              Missouri       3776.0          2107.0    6121623    5883.0          0.642
26            Mountain               Montana        983.0           422.0    1060665    1405.0          0.700
27  West North Central              Nebraska       1745.0           676.0    1925614    2421.0          0.721
28            Mountain                Nevada       7058.0           486.0    3027341    7544.0          0.936
29         New England         New Hampshire        835.0           615.0    1353465    1450.0          0.576
30        Mid-Atlantic            New Jersey       6048.0          3350.0    8886025    9398.0          0.644
31            Mountain            New Mexico       1949.0           602.0    2092741    2551.0          0.764
32        Mid-Atlantic              New York      39827.0         52070.0   19530351   91897.0          0.433
33      South Atlantic        North Carolina       6451.0          2817.0   10381615    9268.0          0.696
34  West North Central          North Dakota        467.0            75.0     758080     542.0          0.862
35  East North Central                  Ohio       6929.0          3320.0   11676341   10249.0          0.676
36  West South Central              Oklahoma       2823.0          1048.0    3940235    3871.0          0.729
37             Pacific                Oregon      11139.0          3337.0    4181886   14476.0          0.769
38        Mid-Atlantic          Pennsylvania       8163.0          5349.0   12800922   13512.0          0.604
39         New England          Rhode Island        747.0           354.0    1058287    1101.0          0.678
40      South Atlantic        South Carolina       3082.0           851.0    5084156    3933.0          0.784
41  West North Central          South Dakota        836.0           323.0     878698    1159.0          0.721
42  East South Central             Tennessee       6139.0          1744.0    6771631    7883.0          0.779
43  West South Central                 Texas      19199.0          6111.0   28628666   25310.0          0.759
44            Mountain                  Utah       1904.0           972.0    3153550    2876.0          0.662
45         New England               Vermont        780.0           511.0     624358    1291.0          0.604
46      South Atlantic              Virginia       3928.0          2047.0    8501286    5975.0          0.657
47             Pacific            Washington      16424.0          5880.0    7523869   22304.0          0.736
48      South Atlantic         West Virginia       1021.0           222.0    1804291    1243.0          0.821
49  East North Central             Wisconsin       2740.0          2167.0    5807406    4907.0          0.558
50            Mountain               Wyoming        434.0           205.0     577601     639.0          0.679
```
---
### Combo-attack!

You've seen the four most common types of data manipulation: sorting rows, subsetting columns, subsetting rows, and adding new columns. In a real-life data analysis, you can mix and match these four manipulations to answer a multitude of questions.

In this exercise, you'll answer the question, "Which state has the highest number of homeless individuals per 10,000 people in the state?" Combine your new pandas skills to find out.

**_Instructions:_**
* Add a column to homelessness, indiv_per_10k, containing the number of homeless individuals per ten thousand people in each state.
* Subset rows where indiv_per_10k is higher than 20, assigning to high_homelessness.
* Sort high_homelessness by descending indiv_per_10k, assigning to high_homelessness_srt.
* Select only the state and indiv_per_10k columns of high_homelessness_srt and save as result. Look at the result.

```py
# Create indiv_per_10k col as homeless individuals per 10k state pop
homelessness["indiv_per_10k"] = 10000 * homelessness['individuals'] / homelessness['state_pop']

# Subset rows for indiv_per_10k greater than 20
high_homelessness = homelessness[homelessness['indiv_per_10k']>20]

# Sort high_homelessness by descending indiv_per_10k
high_homelessness_srt = high_homelessness.sort_values('indiv_per_10k', ascending = False)

# From high_homelessness_srt, select the state and indiv_per_10k cols
result = high_homelessness_srt[['state','indiv_per_10k']]

# See the result
print(result)
```
```
state  indiv_per_10k
8   District of Columbia         53.738
11                Hawaii         29.079
4             California         27.624
37                Oregon         26.636
28                Nevada         23.314
47            Washington         21.829
32              New York         20.392
```
---
## Aggregating DataFrames
---
### Mean and median

Summary statistics are exactly what they sound like - they summarize many numbers in one statistic. For example, mean, median, minimum, maximum, and standard deviation are summary statistics. Calculating summary statistics allows you to get a better sense of your data, even if there's a lot of it.

**_Instructions:_**
* Explore your new DataFrame first by printing the first few rows of the sales DataFrame.
* Print information about the columns in sales.
* Print the mean of the weekly_sales column.
* Print the median of the weekly_sales column.

```py
# Print the head of the sales DataFrame
print(sales.head())

# Print the info about the sales DataFrame
print(sales.info())

# Print the mean of weekly_sales
print(sales['weekly_sales'].mean())

# Print the median of weekly_sales
print(sales['weekly_sales'].median())
```
```
   store type  department       date  weekly_sales  is_holiday  temperature_c  fuel_price_usd_per_l  unemployment
0      1    A           1 2010-02-05      24924.50       False          5.728                 0.679         8.106
1      1    A           1 2010-03-05      21827.90       False          8.056                 0.693         8.106
2      1    A           1 2010-04-02      57258.43       False         16.817                 0.718         7.808
3      1    A           1 2010-05-07      17413.94       False         22.528                 0.749         7.808
4      1    A           1 2010-06-04      17558.09       False         27.050                 0.715         7.808
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 10774 entries, 0 to 10773
Data columns (total 9 columns):
#   Column                Non-Null Count  Dtype         
---  ------                --------------  -----         
0   store                 10774 non-null  int64         
1   type                  10774 non-null  object        
2   department            10774 non-null  int32         
3   date                  10774 non-null  datetime64[ns]
4   weekly_sales          10774 non-null  float64       
5   is_holiday            10774 non-null  bool          
6   temperature_c         10774 non-null  float64       
7   fuel_price_usd_per_l  10774 non-null  float64       
8   unemployment          10774 non-null  float64       
dtypes: bool(1), datetime64[ns](1), float64(4), int32(1), int64(1), object(1)
memory usage: 641.9+ KB
None
23843.95014850566
12049.064999999999
```
---
### Summarizing dates

Summary statistics can also be calculated on date columns that have values with the data type datetime64. Some summary statistics — like mean — don't make a ton of sense on dates, but others are super helpful, for example, minimum and maximum, which allow you to see what time range your data covers.

**_Instructions:_**
* Print the maximum of the date column.
* Print the minimum of the date column.

```py
# Print the maximum of the date column
print(sales['date'].max())

# Print the minimum of the date column
print(sales['date'].min())
```
```
2012-10-26 00:00:00
2010-02-05 00:00:00
```
---
### Efficient summaries

While pandas and NumPy have tons of functions, sometimes, you may need a different function to summarize your data.

The .agg() method allows you to apply your own custom functions to a DataFrame, as well as apply functions to more than one column of a DataFrame at once, making your aggregations super-efficient. For example,

`df['column'].agg(function)`

In the custom function for this exercise, "IQR" is short for inter-quartile range, which is the 75th percentile minus the 25th percentile. It's an alternative to standard deviation that is helpful if your data contains outliers.

**_Instructions:_**
* Use the custom iqr function defined for you along with .agg() to print the IQR of the temperature_c column of sales.

```py
# A custom IQR function
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

# Print IQR of the temperature_c column
print(sales['temperature_c'].agg(iqr))
```
```
16.583333333333336
```
**_Instructions:_**
* Update the column selection to use the custom iqr function with .agg() to print the IQR of temperature_c, fuel_price_usd_per_l, and unemployment, in that order.

```py
# A custom IQR function
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

# Update to print IQR of temperature_c, fuel_price_usd_per_l, & unemployment
print(sales[["temperature_c", 'fuel_price_usd_per_l', 'unemployment']].agg(iqr))
```
```
temperature_c           16.583
fuel_price_usd_per_l     0.073
unemployment             0.565
dtype: float64
```
**_Instructions:_**
* Update the aggregation functions called by .agg(): include iqr and np.median in that order.

```py
# Import NumPy and create custom IQR function
import numpy as np
def iqr(column):
    return column.quantile(0.75) - column.quantile(0.25)

# Update to print IQR and median of temperature_c, fuel_price_usd_per_l, & unemployment
print(sales[["temperature_c", "fuel_price_usd_per_l", "unemployment"]].agg([iqr, np.median]))
```
```
        temperature_c  fuel_price_usd_per_l  unemployment
iqr            16.583                 0.073         0.565
median         16.967                 0.743         8.099
```
---
### Cumulative statistics

Cumulative statistics can also be helpful in tracking summary statistics over time. In this exercise, you'll calculate the cumulative sum and cumulative max of a department's weekly sales, which will allow you to identify what the total sales were so far as well as what the highest weekly sales were so far.

A DataFrame called sales_1_1 has been created for you, which contains the sales data for department 1 of store 1. pandas is loaded as pd.

**_Instructions:_**
* Sort the rows of sales_1_1 by the date column in ascending order.
* Get the cumulative sum of weekly_sales and add it as a new column of sales_1_1 called cum_weekly_sales.
* Get the cumulative maximum of weekly_sales, and add it as a column called cum_max_sales.
* Print the date, weekly_sales, cum_weekly_sales, and cum_max_sales columns.

```py
# Sort sales_1_1 by date
sales_1_1 = sales_1_1.sort_values('date')

# Get the cumulative sum of weekly_sales, add as cum_weekly_sales col
sales_1_1['cum_weekly_sales'] = sales_1_1['weekly_sales'].cumsum()

# Get the cumulative max of weekly_sales, add as cum_max_sales col
sales_1_1['cum_max_sales'] = sales_1_1['weekly_sales'].cummax()

# See the columns you calculated
print(sales_1_1[["date", "weekly_sales", "cum_weekly_sales", "cum_max_sales"]])
```
```
         date  weekly_sales  cum_weekly_sales  cum_max_sales
0  2010-02-05      24924.50          24924.50       24924.50
1  2010-03-05      21827.90          46752.40       24924.50
2  2010-04-02      57258.43         104010.83       57258.43
3  2010-05-07      17413.94         121424.77       57258.43
4  2010-06-04      17558.09         138982.86       57258.43
5  2010-07-02      16333.14         155316.00       57258.43
6  2010-08-06      17508.41         172824.41       57258.43
7  2010-09-03      16241.78         189066.19       57258.43
8  2010-10-01      20094.19         209160.38       57258.43
9  2010-11-05      34238.88         243399.26       57258.43
10 2010-12-03      22517.56         265916.82       57258.43
11 2011-01-07      15984.24         281901.06       57258.43
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
