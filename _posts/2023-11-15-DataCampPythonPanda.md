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
### Dropping duplicates

Removing duplicates is an essential skill to get accurate counts because often, you don't want to count the same thing multiple times. In this exercise, you'll create some new DataFrames using unique values from sales.

**_Instructions:_**
* Remove rows of sales with duplicate pairs of store and type and save as store_types and print the head.
* Remove rows of sales with duplicate pairs of store and department and save as store_depts and print the head.
* Subset the rows that are holiday weeks using the is_holiday column, and drop the duplicate dates, saving as holiday_dates.
* Select the date column of holiday_dates, and print.

```py
# Drop duplicate store/type combinations
store_types = sales.drop_duplicates(subset = ['store','type'])
print(store_types.head())

# Drop duplicate store/department combinations
store_depts = sales.drop_duplicates(subset=['store','department'])
print(store_depts.head())

# Subset the rows where is_holiday is True and drop duplicate dates
holiday_dates = sales[sales['is_holiday'] == True].drop_duplicates(subset = 'date')

# Print date col of holiday_dates
print(holiday_dates['date'])
```
```
store type  department       date  weekly_sales  is_holiday  temperature_c  fuel_price_usd_per_l  unemployment
0         1    A           1 2010-02-05      24924.50       False          5.728                 0.679         8.106
901       2    A           1 2010-02-05      35034.06       False          4.550                 0.679         8.324
1798      4    A           1 2010-02-05      38724.42       False          6.533                 0.686         8.623
2699      6    A           1 2010-02-05      25619.00       False          4.683                 0.679         7.259
3593     10    B           1 2010-02-05      40212.84       False         12.411                 0.782         9.765
store type  department       date  weekly_sales  is_holiday  temperature_c  fuel_price_usd_per_l  unemployment
0       1    A           1 2010-02-05      24924.50       False          5.728                 0.679         8.106
12      1    A           2 2010-02-05      50605.27       False          5.728                 0.679         8.106
24      1    A           3 2010-02-05      13740.12       False          5.728                 0.679         8.106
36      1    A           4 2010-02-05      39954.04       False          5.728                 0.679         8.106
48      1    A           5 2010-02-05      32229.38       False          5.728                 0.679         8.106
498    2010-09-10
691    2011-11-25
2315   2010-02-12
6735   2012-09-07
6810   2010-12-31
6815   2012-02-10
6820   2011-09-09
Name: date, dtype: datetime64[ns]
```
---
### Counting categorical variables

Counting is a great way to get an overview of your data and to spot curiosities that you might not notice otherwise. In this exercise, you'll count the number of each type of store and the number of each department number using the DataFrames you created in the previous exercise:

```
# Drop duplicate store/type combinations
store_types = sales.drop_duplicates(subset=["store", "type"])

# Drop duplicate store/department combinations
store_depts = sales.drop_duplicates(subset=["store", "department"])
```

The store_types and store_depts DataFrames you created in the last exercise are available, and pandas is imported as pd.

**_Instructions:_**
* Count the number of stores of each store type in store_types.
* Count the proportion of stores of each store type in store_types.
* Count the number of different departments in store_depts, sorting the counts in descending order.
* Count the proportion of different departments in store_depts, sorting the proportions in descending order.

```py
# Count the number of stores of each type
store_counts = store_types['type'].value_counts()
print(store_counts)

# Get the proportion of stores of each type
store_props = store_types['type'].value_counts(normalize = True)
print(store_props)

# Count the number of each department number and sort
dept_counts_sorted = store_depts['department'].value_counts(sort = True)
print(dept_counts_sorted)

# Get the proportion of departments of each number and sort
dept_props_sorted = store_depts['department'].value_counts(sort=True, normalize=True)
print(dept_props_sorted)
```
```
A    11
B     1
Name: type, dtype: int64
A    0.917
B    0.083
Name: type, dtype: float64
1     12
55    12
72    12
71    12
67    12
      ..
37    10
48     8
50     6
39     4
43     2
Name: department, Length: 80, dtype: int64
1     0.013
55    0.013
72    0.013
71    0.013
67    0.013
      ...  
37    0.011
48    0.009
50    0.006
39    0.004
43    0.002
Name: department, Length: 80, dtype: float64
```
---
### What percent of sales occurred at each store type?

While .groupby() is useful, you can calculate grouped summary statistics without it.

Walmart distinguishes three types of stores: "supercenters," "discount stores," and "neighborhood markets," encoded in this dataset as type "A," "B," and "C." In this exercise, you'll calculate the total sales made at each store type, without using .groupby(). You can then use these numbers to see what proportion of Walmart's total sales were made at each type.

**_Instructions:_**
* Calculate the total weekly_sales over the whole dataset.
* Subset for type "A" stores, and calculate their total weekly sales.
* Do the same for type "B" and type "C" stores.
* Combine the A/B/C results into a list, and divide by sales_all to get the proportion of sales by type.

```py
# Calc total weekly sales
sales_all = sales["weekly_sales"].sum()

# Subset for type A stores, calc total weekly sales
sales_A = sales[sales["type"] == "A"]["weekly_sales"].sum()

# Subset for type B stores, calc total weekly sales
sales_B = sales[sales["type"] == "B"]["weekly_sales"].sum()

# Subset for type C stores, calc total weekly sales
sales_C = sales[sales["type"] == "C"]["weekly_sales"].sum()

# Get proportion for each type
sales_propn_by_type = [sales_A, sales_B, sales_C] /sales_all
print(sales_propn_by_type)
```
```
    [0.9097747 0.0902253 0.       ]
```
---
### Calculations with .groupby()

The .groupby() method makes life much easier. In this exercise, you'll perform the same calculations as last time, except you'll use the .groupby() method. You'll also perform calculations on data grouped by two variables to see if sales differ by store type depending on if it's a holiday week or not.

**_Instructions:_**
* Group sales by "type", take the sum of "weekly_sales", and store as sales_by_type.
* Calculate the proportion of sales at each store type by dividing by the sum of sales_by_type. Assign to sales_propn_by_type

```py
# Group by type; calc total weekly sales
sales_by_type = sales.groupby("type")["weekly_sales"].sum()

# Get proportion for each type
sales_propn_by_type = sales_by_type / sum(sales_by_type)
print(sales_propn_by_type)
```
```
type
A    0.91
B    0.09
Name: weekly_sales, dtype: float64
```
**_Instructions:_**
* Group sales by "type" and "is_holiday", take the sum of weekly_sales, and store as sales_by_type_is_holiday.

```py
# Group by type and is_holiday; calc total weekly sales
sales_by_type_is_holiday = sales.groupby(["type",'is_holiday'])["weekly_sales"].sum()
print(sales_by_type_is_holiday)
```
```
    type  is_holiday
    A     False         2.337e+08
          True          2.360e+04
    B     False         2.318e+07
          True          1.621e+03
    Name: weekly_sales, dtype: float64
```
---
### Multiple grouped summaries

Earlier in this chapter, you saw that the .agg() method is useful to compute multiple statistics on multiple variables. It also works with grouped data. NumPy, which is imported as np, has many different summary statistics functions, including: np.min, np.max, np.mean, and np.median.

**_Instructions:_**
* Import numpy with the alias np.
* Get the min, max, mean, and median of weekly_sales for each store type using .groupby() and .agg(). Store this as sales_stats. Make sure to use numpy functions!
* Get the min, max, mean, and median of unemployment and fuel_price_usd_per_l for each store type. Store this as unemp_fuel_stats.

```py
# Import numpy with the alias np
import numpy as np

# For each store type, aggregate weekly_sales: get min, max, mean, and median
sales_stats = sales.groupby('type')['weekly_sales'].agg([np.min,np.max,np.mean, np.median])

# Print sales_stats
print(sales_stats)

# For each store type, aggregate unemployment and fuel_price_usd_per_l: get min, max, mean, and median
unemp_fuel_stats = sales.groupby('type')[['unemployment','fuel_price_usd_per_l']].agg([np.min,np.max,np.mean, np.median])

# Print unemp_fuel_stats
print(unemp_fuel_stats)
```
```
            amin       amax       mean    median
    type                                        
    A    -1098.0  293966.05  23674.667  11943.92
    B     -798.0  232558.51  25696.678  13336.08
         unemployment                      fuel_price_usd_per_l                     
                 amin   amax   mean median                 amin   amax   mean median
    type                                                                            
    A           3.879  8.992  7.973  8.067                0.664  1.107  0.745  0.735
    B           7.170  9.765  9.279  9.199                0.760  1.108  0.806  0.803
```
---
### Pivoting on one variable

Pivot tables are the standard way of aggregating data in spreadsheets.

In pandas, pivot tables are essentially another way of performing grouped calculations. That is, the .pivot_table() method is an alternative to .groupby().

In this exercise, you'll perform calculations using .pivot_table() to replicate the calculations you performed in the last lesson using .groupby().

**_Instructions:_**
* Get the mean weekly_sales by type using .pivot_table() and store as mean_sales_by_type

```py
# Pivot for mean weekly_sales for each store type
mean_sales_by_type = sales.pivot_table(values = 'weekly_sales', index = 'type')

# Print mean_sales_by_type
print(mean_sales_by_type)
```
```
weekly_sales
type              
A        23674.667
B        25696.678
```
**_Instructions:_**
* Get the mean and median (using NumPy functions) of weekly_sales by type using .pivot_table() and store as mean_med_sales_by_type.

```py
# Import NumPy as np
import numpy as np

# Pivot for mean and median weekly_sales for each store type
mean_med_sales_by_type = sales.pivot_table(values='weekly_sales', index='type', aggfunc=[np.mean, np.median])

# Print mean_med_sales_by_type
print(mean_med_sales_by_type)
```
```
mean       median
weekly_sales weekly_sales
type                          
A       23674.667     11943.92
B       25696.678     13336.08
```
**_Instructions:_**
* Get the mean of weekly_sales by type and is_holiday using .pivot_table() and store as mean_sales_by_type_holiday.

```py
# Pivot for mean weekly_sales by store type and holiday
mean_sales_by_type_holiday = sales.pivot_table(values = 'weekly_sales', index='type', columns='is_holiday')

# Print mean_sales_by_type_holiday
print(mean_sales_by_type_holiday)
```
```
is_holiday      False     True
type                          
A           23768.584  590.045
B           25751.981  810.705
```
---
### Fill in missing values and sum values with pivot tables

The .pivot_table() method has several useful arguments, including fill_value and margins.

* fill_value replaces missing values with a real value (known as imputation). What to replace missing values with is a topic big enough to have its own course (Dealing with Missing Data in Python), but the simplest thing to do is to substitute a dummy value.

* margins is a shortcut for when you pivoted by two variables, but also wanted to pivot by each of those variables separately: it gives the row and column totals of the pivot table contents.

In this exercise, you'll practice using these arguments to up your pivot table skills, which will help you crunch numbers more efficiently!

**_Instructions:_**
* Print the mean weekly_sales by department and type, filling in any missing values with 0.

```py
# Print mean weekly_sales by department and type; fill missing values with 0
print(sales.pivot_table(values='weekly_sales',index='department',columns='type',fill_value=0))
```
```
type                 A           B
department                        
1            30961.725   44050.627
2            67600.159  112958.527
3            17160.003   30580.655
4            44285.399   51219.654
5            34821.011   63236.875
...                ...         ...
95          123933.787   77082.102
96           21367.043    9528.538
97           28471.267    5828.873
98           12875.423     217.428
99             379.124       0.000

[80 rows x 2 columns]
```
**_Instructions:_**
* Print the mean weekly_sales by department and type, filling in any missing values with 0 and summing all rows and columns.

```py
# Print the mean weekly_sales by department and type; fill missing values with 0s; sum all rows and cols
print(sales.pivot_table(values="weekly_sales", index="department", columns="type", fill_value=0,margins =True))
```
```
type                A           B        All
department                                  
1           30961.725   44050.627  32052.467
2           67600.159  112958.527  71380.023
3           17160.003   30580.655  18278.391
4           44285.399   51219.654  44863.254
5           34821.011   63236.875  37189.000
...               ...         ...        ...
96          21367.043    9528.538  20337.608
97          28471.267    5828.873  26584.401
98          12875.423     217.428  11820.590
99            379.124       0.000    379.124
All         23674.667   25696.678  23843.950

[81 rows x 3 columns]
```
---
## Slicing and Indexing DataFrames
---
### Setting and removing indexes

pandas allows you to designate columns as an index. This enables cleaner code when taking subsets (as well as providing more efficient lookup under some circumstances).

In this chapter, you'll be exploring temperatures, a DataFrame of average temperatures in cities around the world. pandas is loaded as pd.

**_Instructions:_**
* Set the index of temperatures to "city", assigning to temperatures_ind.
* Reset the index of temperatures_ind, keeping its contents.
* Reset the index of temperatures_ind, dropping its contents.

```py
# Look at temperatures
print(temperatures)

# Set the index of temperatures to city
temperatures_ind = temperatures.set_index('city')

# Look at temperatures_ind
print(temperatures_ind)

# Reset the temperatures_ind index, keeping its contents
print(temperatures_ind.reset_index())

# Reset the temperatures_ind index, dropping its contents
print(temperatures_ind.reset_index(drop=True))
```
```
            date     city        country  avg_temp_c
0     2000-01-01  Abidjan  Côte D'Ivoire      27.293
1     2000-02-01  Abidjan  Côte D'Ivoire      27.685
2     2000-03-01  Abidjan  Côte D'Ivoire      29.061
3     2000-04-01  Abidjan  Côte D'Ivoire      28.162
4     2000-05-01  Abidjan  Côte D'Ivoire      27.547
...          ...      ...            ...         ...
16495 2013-05-01     Xian          China      18.979
16496 2013-06-01     Xian          China      23.522
16497 2013-07-01     Xian          China      25.251
16498 2013-08-01     Xian          China      24.528
16499 2013-09-01     Xian          China         NaN

[16500 rows x 4 columns]
              date        country  avg_temp_c
city                                         
Abidjan 2000-01-01  Côte D'Ivoire      27.293
Abidjan 2000-02-01  Côte D'Ivoire      27.685
Abidjan 2000-03-01  Côte D'Ivoire      29.061
Abidjan 2000-04-01  Côte D'Ivoire      28.162
Abidjan 2000-05-01  Côte D'Ivoire      27.547
...            ...            ...         ...
Xian    2013-05-01          China      18.979
Xian    2013-06-01          China      23.522
Xian    2013-07-01          China      25.251
Xian    2013-08-01          China      24.528
Xian    2013-09-01          China         NaN

[16500 rows x 3 columns]
          city       date        country  avg_temp_c
0      Abidjan 2000-01-01  Côte D'Ivoire      27.293
1      Abidjan 2000-02-01  Côte D'Ivoire      27.685
2      Abidjan 2000-03-01  Côte D'Ivoire      29.061
3      Abidjan 2000-04-01  Côte D'Ivoire      28.162
4      Abidjan 2000-05-01  Côte D'Ivoire      27.547
...        ...        ...            ...         ...
16495     Xian 2013-05-01          China      18.979
16496     Xian 2013-06-01          China      23.522
16497     Xian 2013-07-01          China      25.251
16498     Xian 2013-08-01          China      24.528
16499     Xian 2013-09-01          China         NaN

[16500 rows x 4 columns]
            date        country  avg_temp_c
0     2000-01-01  Côte D'Ivoire      27.293
1     2000-02-01  Côte D'Ivoire      27.685
2     2000-03-01  Côte D'Ivoire      29.061
3     2000-04-01  Côte D'Ivoire      28.162
4     2000-05-01  Côte D'Ivoire      27.547
...          ...            ...         ...
16495 2013-05-01          China      18.979
16496 2013-06-01          China      23.522
16497 2013-07-01          China      25.251
16498 2013-08-01          China      24.528
16499 2013-09-01          China         NaN

[16500 rows x 3 columns]
```
---
### Subsetting with .loc[]

The killer feature for indexes is .loc[]: a subsetting method that accepts index values. When you pass it a single argument, it will take a subset of rows.

The code for subsetting using .loc[] can be easier to read than standard square bracket subsetting, which can make your code less burdensome to maintain.

pandas is loaded as pd. temperatures and temperatures_ind are available; the latter is indexed by city.

**_Instructions:_**
* Create a list called cities that contains "Moscow" and "Saint Petersburg".
* Use [] subsetting to filter temperatures for rows where the city column takes a value in the cities list.
* Use .loc[] subsetting to filter temperatures_ind for rows where the city is in the cities list.

```py
# Make a list of cities to subset on
cities = ["Moscow", "Saint Petersburg"]

# Subset temperatures using square brackets
print(temperatures[temperatures["city"].isin(cities)])

# Subset temperatures_ind using .loc[]
print(temperatures_ind.loc[cities])
```
```
date              city country  avg_temp_c
10725 2000-01-01            Moscow  Russia      -7.313
10726 2000-02-01            Moscow  Russia      -3.551
10727 2000-03-01            Moscow  Russia      -1.661
10728 2000-04-01            Moscow  Russia      10.096
10729 2000-05-01            Moscow  Russia      10.357
...          ...               ...     ...         ...
13360 2013-05-01  Saint Petersburg  Russia      12.355
13361 2013-06-01  Saint Petersburg  Russia      17.185
13362 2013-07-01  Saint Petersburg  Russia      17.234
13363 2013-08-01  Saint Petersburg  Russia      17.153
13364 2013-09-01  Saint Petersburg  Russia         NaN

[330 rows x 4 columns]
           date country  avg_temp_c
city                                           
Moscow           2000-01-01  Russia      -7.313
Moscow           2000-02-01  Russia      -3.551
Moscow           2000-03-01  Russia      -1.661
Moscow           2000-04-01  Russia      10.096
Moscow           2000-05-01  Russia      10.357
...                     ...     ...         ...
Saint Petersburg 2013-05-01  Russia      12.355
Saint Petersburg 2013-06-01  Russia      17.185
Saint Petersburg 2013-07-01  Russia      17.234
Saint Petersburg 2013-08-01  Russia      17.153
Saint Petersburg 2013-09-01  Russia         NaN

[330 rows x 3 columns]
```
---
### Setting multi-level indexes

Indexes can also be made out of multiple columns, forming a multi-level index (sometimes called a hierarchical index). There is a trade-off to using these.

The benefit is that multi-level indexes make it more natural to reason about nested categorical variables. For example, in a clinical trial, you might have control and treatment groups. Then each test subject belongs to one or another group, and we can say that a test subject is nested inside the treatment group. Similarly, in the temperature dataset, the city is located in the country, so we can say a city is nested inside the country.

The main downside is that the code for manipulating indexes is different from the code for manipulating columns, so you have to learn two syntaxes and keep track of how your data is represented.

pandas is loaded as pd. temperatures is available.

**_Instructions:_**
* Set the index of temperatures to the "country" and "city" columns, and assign this to temperatures_ind.
* Specify two country/city pairs to keep: "Brazil"/"Rio De Janeiro" and "Pakistan"/"Lahore", assigning to rows_to_keep.
* Print and subset temperatures_ind for rows_to_keep using .loc[].

```py
# Index temperatures by country & city
temperatures_ind = temperatures.set_index(['country','city'])

# List of tuples: Brazil, Rio De Janeiro & Pakistan, Lahore
rows_to_keep = [("Brazil", "Rio De Janeiro"), ("Pakistan", "Lahore")]

# Subset for rows to keep
print(temperatures_ind.loc[rows_to_keep])
```
```
date  avg_temp_c
country  city                                 
Brazil   Rio De Janeiro 2000-01-01      25.974
         Rio De Janeiro 2000-02-01      26.699
         Rio De Janeiro 2000-03-01      26.270
         Rio De Janeiro 2000-04-01      25.750
         Rio De Janeiro 2000-05-01      24.356
...                            ...         ...
Pakistan Lahore         2013-05-01      33.457
         Lahore         2013-06-01      34.456
         Lahore         2013-07-01      33.279
         Lahore         2013-08-01      31.511
         Lahore         2013-09-01         NaN

[330 rows x 2 columns]
```
---
### Sorting by index values

Previously, you changed the order of the rows in a DataFrame by calling .sort_values(). It's also useful to be able to sort by elements in the index. For this, you need to use .sort_index().

pandas is loaded as pd. temperatures_ind has a multi-level index of country and city, and is available.

**_Instructions:_**
* Sort temperatures_ind by the index values.
* Sort temperatures_ind by the index values at the "city" level.
* Sort temperatures_ind by ascending country then descending city.

```py
# Sort temperatures_ind by index values
print(temperatures_ind.sort_index())

# Sort temperatures_ind by index values at the city level
print(temperatures_ind.sort_index(level="city"))

# Sort temperatures_ind by country then descending city
print(temperatures_ind.sort_index(level=["country", "city"], ascending = [True, False]))
```
```
date  avg_temp_c
country     city                         
Afghanistan Kabul  2000-01-01       3.326
            Kabul  2000-02-01       3.454
            Kabul  2000-03-01       9.612
            Kabul  2000-04-01      17.925
            Kabul  2000-05-01      24.658
...                       ...         ...
Zimbabwe    Harare 2013-05-01      18.298
            Harare 2013-06-01      17.020
            Harare 2013-07-01      16.299
            Harare 2013-08-01      19.232
            Harare 2013-09-01         NaN

[16500 rows x 2 columns]
   date  avg_temp_c
country       city                          
Côte D'Ivoire Abidjan 2000-01-01      27.293
              Abidjan 2000-02-01      27.685
              Abidjan 2000-03-01      29.061
              Abidjan 2000-04-01      28.162
              Abidjan 2000-05-01      27.547
...                          ...         ...
China         Xian    2013-05-01      18.979
              Xian    2013-06-01      23.522
              Xian    2013-07-01      25.251
              Xian    2013-08-01      24.528
              Xian    2013-09-01         NaN

[16500 rows x 2 columns]
date  avg_temp_c
country     city                         
Afghanistan Kabul  2000-01-01       3.326
            Kabul  2000-02-01       3.454
            Kabul  2000-03-01       9.612
            Kabul  2000-04-01      17.925
            Kabul  2000-05-01      24.658
...                       ...         ...
Zimbabwe    Harare 2013-05-01      18.298
            Harare 2013-06-01      17.020
            Harare 2013-07-01      16.299
            Harare 2013-08-01      19.232
            Harare 2013-09-01         NaN

[16500 rows x 2 columns]
```
---
### Slicing index values

Slicing lets you select consecutive elements of an object using first:last syntax. DataFrames can be sliced by index values or by row/column number; we'll start with the first case. This involves slicing inside the .loc[] method.

Compared to slicing lists, there are a few things to remember.

* You can only slice an index if the index is sorted (using .sort_index()).

* To slice at the outer level, first and last can be strings.

* To slice at inner levels, first and last should be tuples.

* If you pass a single slice to .loc[], it will slice the rows.
pandas is loaded as pd. temperatures_ind has country and city in the index, and is available.

**_Instructions:_**
* Sort the index of temperatures_ind.
* Use slicing with .loc[] to get these subsets

```py
# Sort the index of temperatures_ind
temperatures_srt = temperatures_ind.sort_index()

# Subset rows from Pakistan to Russia
print(temperatures_srt.loc["Pakistan":"Russia"])

# Try to subset rows from Lahore to Moscow
print(temperatures_srt.loc["Lahore":"Moscow"])

# Subset rows from Pakistan, Lahore to Russia, Moscow
print(temperatures_srt.loc[("Pakistan", "Lahore"):("Russia", "Moscow")])
```
```
date  avg_temp_c
country  city                                   
Pakistan Faisalabad       2000-01-01      12.792
         Faisalabad       2000-02-01      14.339
         Faisalabad       2000-03-01      20.309
         Faisalabad       2000-04-01      29.072
         Faisalabad       2000-05-01      34.845
...                              ...         ...
Russia   Saint Petersburg 2013-05-01      12.355
         Saint Petersburg 2013-06-01      17.185
         Saint Petersburg 2013-07-01      17.234
         Saint Petersburg 2013-08-01      17.153
         Saint Petersburg 2013-09-01         NaN

[1155 rows x 2 columns]
date  avg_temp_c
country city                             
Mexico  Mexico     2000-01-01      12.694
        Mexico     2000-02-01      14.677
        Mexico     2000-03-01      17.376
        Mexico     2000-04-01      18.294
        Mexico     2000-05-01      18.562
...                       ...         ...
Morocco Casablanca 2013-05-01      19.217
        Casablanca 2013-06-01      23.649
        Casablanca 2013-07-01      27.488
        Casablanca 2013-08-01      27.952
        Casablanca 2013-09-01         NaN

[330 rows x 2 columns]
date  avg_temp_c
country  city                         
Pakistan Lahore 2000-01-01      12.792
         Lahore 2000-02-01      14.339
         Lahore 2000-03-01      20.309
         Lahore 2000-04-01      29.072
         Lahore 2000-05-01      34.845
...                    ...         ...
Russia   Moscow 2013-05-01      16.152
         Moscow 2013-06-01      18.718
         Moscow 2013-07-01      18.136
         Moscow 2013-08-01      17.485
         Moscow 2013-09-01         NaN

[660 rows x 2 columns]
```
---
### Slicing in both directions

You've seen slicing DataFrames by rows and by columns, but since DataFrames are two-dimensional objects, it is often natural to slice both dimensions at once. That is, by passing two arguments to .loc[], you can subset by rows and columns in one go.

pandas is loaded as pd. temperatures_srt is indexed by country and city, has a sorted index, and is available.

**_Instructions:_**
* Use .loc[] slicing to subset rows from India, Hyderabad to Iraq, Baghdad.
* Use .loc[] slicing to subset columns from date to avg_temp_c.
* Slice in both directions at once from Hyderabad to Baghdad, and date to avg_temp_c.

```py
# Subset rows from India, Hyderabad to Iraq, Baghdad
print(temperatures_srt.loc[("India", "Hyderabad"):("Iraq", "Baghdad")])

# Subset columns from date to avg_temp_c
print(temperatures_srt.loc[:,'date':'avg_temp_c'])

# Subset in both directions at once
print(temperatures_srt.loc[("India", "Hyderabad"):("Iraq", "Baghdad"),'date':'avg_temp_c'])
```
```
date  avg_temp_c
country city                            
India   Hyderabad 2000-01-01      23.779
        Hyderabad 2000-02-01      25.826
        Hyderabad 2000-03-01      28.821
        Hyderabad 2000-04-01      32.698
        Hyderabad 2000-05-01      32.438
...                      ...         ...
Iraq    Baghdad   2013-05-01      28.673
        Baghdad   2013-06-01      33.803
        Baghdad   2013-07-01      36.392
        Baghdad   2013-08-01      35.463
        Baghdad   2013-09-01         NaN

[2145 rows x 2 columns]
 date  avg_temp_c
country     city                         
Afghanistan Kabul  2000-01-01       3.326
            Kabul  2000-02-01       3.454
            Kabul  2000-03-01       9.612
            Kabul  2000-04-01      17.925
            Kabul  2000-05-01      24.658
...                       ...         ...
Zimbabwe    Harare 2013-05-01      18.298
            Harare 2013-06-01      17.020
            Harare 2013-07-01      16.299
            Harare 2013-08-01      19.232
            Harare 2013-09-01         NaN

[16500 rows x 2 columns]
date  avg_temp_c
country city                            
India   Hyderabad 2000-01-01      23.779
        Hyderabad 2000-02-01      25.826
        Hyderabad 2000-03-01      28.821
        Hyderabad 2000-04-01      32.698
        Hyderabad 2000-05-01      32.438
...                      ...         ...
Iraq    Baghdad   2013-05-01      28.673
        Baghdad   2013-06-01      33.803
        Baghdad   2013-07-01      36.392
        Baghdad   2013-08-01      35.463
        Baghdad   2013-09-01         NaN

[2145 rows x 2 columns]
```
---
### Slicing time series

Slicing is particularly useful for time series since it's a common thing to want to filter for data within a date range. Add the date column to the index, then use .loc[] to perform the subsetting. The important thing to remember is to keep your dates in ISO 8601 format, that is, "yyyy-mm-dd" for year-month-day, "yyyy-mm" for year-month, and "yyyy" for year.

Recall from Chapter 1 that you can combine multiple Boolean conditions using logical operators, such as &. To do so in one line of code, you'll need to add parentheses () around each condition.

pandas is loaded as pd and temperatures, with no index, is available.

**_Instructions:_**
* Use Boolean conditions, not .isin() or .loc[], and the full date "yyyy-mm-dd", to subset temperatures for rows in 2010 and 2011 and print the results.
* Set the index of temperatures to the date column and sort it.
* Use .loc[] to subset temperatures_ind for rows in 2010 and 2011.
* Use .loc[] to subset temperatures_ind for rows from Aug 2010 to Feb 2011.

```py
# Use Boolean conditions to subset temperatures for rows in 2010 and 2011
temperatures_bool = temperatures[(temperatures['date'] >= '2010') & (temperatures['date'] <= '2011-12-31')]
print(temperatures_bool)

# Set date as the index and sort the index
temperatures_ind = temperatures.set_index('date').sort_index()

# Use .loc[] to subset temperatures_ind for rows in 2010 and 2011
print(temperatures_ind.loc['2010':'2011-12-31'])

# Use .loc[] to subset temperatures_ind for rows from Aug 2010 to Feb 2011
print(temperatures_ind.loc['2010-08':'2011-02'])
```
```
date     city        country  avg_temp_c
120   2010-01-01  Abidjan  Côte D'Ivoire      28.270
121   2010-02-01  Abidjan  Côte D'Ivoire      29.262
122   2010-03-01  Abidjan  Côte D'Ivoire      29.596
123   2010-04-01  Abidjan  Côte D'Ivoire      29.068
124   2010-05-01  Abidjan  Côte D'Ivoire      28.258
...          ...      ...            ...         ...
16474 2011-08-01     Xian          China      23.069
16475 2011-09-01     Xian          China      16.775
16476 2011-10-01     Xian          China      12.587
16477 2011-11-01     Xian          China       7.543
16478 2011-12-01     Xian          China      -0.490

[2400 rows x 4 columns]
      city    country  avg_temp_c
date                                         
2010-01-01  Faisalabad   Pakistan      11.810
2010-01-01   Melbourne  Australia      20.016
2010-01-01   Chongqing      China       7.921
2010-01-01   São Paulo     Brazil      23.738
2010-01-01   Guangzhou      China      14.136
...                ...        ...         ...
2011-12-01      Nagoya      Japan       6.476
2011-12-01   Hyderabad      India      23.613
2011-12-01        Cali   Colombia      21.559
2011-12-01        Lima       Peru      18.293
2011-12-01     Bangkok   Thailand      25.021

[2400 rows x 3 columns]
    city        country  avg_temp_c
date                                           
2010-08-01  Calcutta          India      30.226
2010-08-01      Pune          India      24.941
2010-08-01     Izmir         Turkey      28.352
2010-08-01   Tianjin          China      25.543
2010-08-01    Manila    Philippines      27.101
...              ...            ...         ...
2011-02-01     Kabul    Afghanistan       3.914
2011-02-01   Chicago  United States       0.276
2011-02-01    Aleppo          Syria       8.246
2011-02-01     Delhi          India      18.136
2011-02-01   Rangoon          Burma      26.631

[700 rows x 3 columns]
```
---
### Subsetting by row/column number

The most common ways to subset rows are the ways we've previously discussed: using a Boolean condition or by index labels. However, it is also occasionally useful to pass row numbers.

This is done using .iloc[], and like .loc[], it can take two arguments to let you subset by rows and columns.

pandas is loaded as pd. temperatures (without an index) is available.

**_Instructions:_**
* Use .iloc[] on temperatures to take subsets.

```py
# Get 23rd row, 2nd column (index 22, 1)
print(temperatures.iloc[22, 1])

# Use slicing to get the first 5 rows
print(temperatures.iloc[:5])

# Use slicing to get columns 3 to 4
print(temperatures.iloc[:, 2:4])

# Use slicing in both directions at once
print(temperatures.iloc[:5, 2:4])
```
```
Abidjan
        date     city        country  avg_temp_c
0 2000-01-01  Abidjan  Côte D'Ivoire      27.293
1 2000-02-01  Abidjan  Côte D'Ivoire      27.685
2 2000-03-01  Abidjan  Côte D'Ivoire      29.061
3 2000-04-01  Abidjan  Côte D'Ivoire      28.162
4 2000-05-01  Abidjan  Côte D'Ivoire      27.547
             country  avg_temp_c
0      Côte D'Ivoire      27.293
1      Côte D'Ivoire      27.685
2      Côte D'Ivoire      29.061
3      Côte D'Ivoire      28.162
4      Côte D'Ivoire      27.547
...              ...         ...
16495          China      18.979
16496          China      23.522
16497          China      25.251
16498          China      24.528
16499          China         NaN

[16500 rows x 2 columns]
         country  avg_temp_c
0  Côte D'Ivoire      27.293
1  Côte D'Ivoire      27.685
2  Côte D'Ivoire      29.061
3  Côte D'Ivoire      28.162
4  Côte D'Ivoire      27.547
```
---
### Pivot temperature by city and year

It's interesting to see how temperatures for each city change over time—looking at every month results in a big table, which can be tricky to reason about. Instead, let's look at how temperatures change by year.

You can access the components of a date (year, month and day) using code of the form dataframe["column"].dt.component. For example, the month component is dataframe["column"].dt.month, and the year component is dataframe["column"].dt.year.

Once you have the year column, you can create a pivot table with the data aggregated by city and year, which you'll explore in the coming exercises.

pandas is loaded as pd. temperatures is available.

**_Instructions:_**
* Add a year column to temperatures, from the year component of the date column.
* Make a pivot table of the avg_temp_c column, with country and city as rows, and year as columns. Assign to temp_by_country_city_vs_year, and look at the result.

```py
# Add a year column to temperatures
temperatures['year'] = temperatures['date'].dt.year

# Pivot avg_temp_c by country and city vs year
temp_by_country_city_vs_year = temperatures.pivot_table('avg_temp_c', index=['country','city'],columns = 'year')

# See the result
print(temp_by_country_city_vs_year)
```
```
year                              2000    2001    2002    2003    2004  ...    2009    2010    2011    2012    2013
country       city                                                      ...                                        
Afghanistan   Kabul             15.823  15.848  15.715  15.133  16.128  ...  15.093  15.676  15.812  14.510  16.206
Angola        Luanda            24.410  24.427  24.791  24.867  24.216  ...  24.325  24.440  24.151  24.240  24.554
Australia     Melbourne         14.320  14.180  14.076  13.986  13.742  ...  14.647  14.232  14.191  14.269  14.742
              Sydney            17.567  17.854  17.734  17.592  17.870  ...  18.176  17.999  17.713  17.474  18.090
Bangladesh    Dhaka             25.905  25.931  26.095  25.927  26.136  ...  26.536  26.648  25.803  26.284  26.587
...                                ...     ...     ...     ...     ...  ...     ...     ...     ...     ...     ...
United States Chicago           11.090  11.703  11.532  10.482  10.943  ...  10.298  11.816  11.214  12.821  11.587
              Los Angeles       16.643  16.466  16.430  16.945  16.553  ...  16.677  15.887  15.875  17.090  18.121
              New York           9.969  10.931  11.252   9.836  10.389  ...  10.142  11.358  11.272  11.971  12.164
Vietnam       Ho Chi Minh City  27.589  27.832  28.065  27.828  27.687  ...  27.853  28.282  27.675  28.249  28.455
Zimbabwe      Harare            20.284  20.861  21.079  20.889  20.308  ...  20.524  21.166  20.782  20.523  19.756

[100 rows x 14 columns]
```
---
### Subsetting pivot tables

A pivot table is just a DataFrame with sorted indexes, so the techniques you have learned already can be used to subset them. In particular, the .loc[] + slicing combination is often helpful.

pandas is loaded as pd. temp_by_country_city_vs_year is available.

**_Instructions:_**
* Use .loc[] on temp_by_country_city_vs_year to take subsets.

```py
# Subset for Egypt to India
temp_by_country_city_vs_year.loc['Egypt':'India']

# Subset for Egypt, Cairo to India, Delhi
temp_by_country_city_vs_year.loc[('Egypt', 'Cairo'):('India','Delhi')]

# Subset for Egypt, Cairo to India, Delhi, and 2005 to 2010
temp_by_country_city_vs_year.loc[('Egypt', 'Cairo'):('India','Delhi'),'2005':'2010']
```
```
year                    2005    2006    2007    2008    2009    2010
country  city                                                       
Egypt    Cairo        22.006  22.050  22.361  22.644  22.625  23.718
         Gizeh        22.006  22.050  22.361  22.644  22.625  23.718
Ethiopia Addis Abeba  18.313  18.427  18.143  18.165  18.765  18.298
France   Paris        11.553  11.788  11.751  11.278  11.464  10.410
Germany  Berlin        9.919  10.545  10.883  10.658  10.062   8.607
India    Ahmadabad    26.828  27.283  27.511  27.049  28.096  28.018
         Bangalore    25.477  25.418  25.464  25.353  25.726  25.705
         Bombay       27.036  27.382  27.635  27.178  27.845  27.765
         Calcutta     26.729  26.986  26.585  26.522  27.153  27.289
         Delhi        25.716  26.366  26.146  25.675  26.554  26.520
```
---
### Calculating on a pivot table

Pivot tables are filled with summary statistics, but they are only a first step to finding something insightful. Often you'll need to perform further calculations on them. A common thing to do is to find the rows or columns where the highest or lowest value occurs.

Recall from Chapter 1 that you can easily subset a Series or DataFrame to find rows of interest using a logical condition inside of square brackets. For example: series[series > value].

pandas is loaded as pd and the DataFrame temp_by_country_city_vs_year is available.

**_Instructions:_**
* Calculate the mean temperature for each year, assigning to mean_temp_by_year.
* Filter mean_temp_by_year for the year that had the highest mean temperature.
* Calculate the mean temperature for each city (across columns), assigning to mean_temp_by_city.
* Filter mean_temp_by_city for the city that had the lowest mean temperature.

```py
# Get the worldwide mean temp by year
mean_temp_by_year = temp_by_country_city_vs_year.mean()

# Filter for the year that had the highest mean temp
print(mean_temp_by_year[mean_temp_by_year == mean_temp_by_year.max()])

# Get the mean temp by city
mean_temp_by_city = temp_by_country_city_vs_year.mean(axis="columns")

# Filter for the city that had the lowest mean temp
print(mean_temp_by_city[mean_temp_by_city == mean_temp_by_city.min()])
```
```
year
2013    20.312
dtype: float64
country  city  
China    Harbin    4.877
dtype: float64
```
---
## Creating and Visualizing DataFrames
---
### Which avocado size is most popular?

Avocados are increasingly popular and delicious in guacamole and on toast. The Hass Avocado Board keeps track of avocado supply and demand across the USA, including the sales of three different sizes of avocado. In this exercise, you'll use a bar plot to figure out which size is the most popular.

Bar plots are great for revealing relationships between categorical (size) and numeric (number sold) variables, but you'll often have to manipulate your data first in order to get the numbers you need for plotting.

pandas has been imported as pd, and avocados is available.

**_Instructions:_**
* Print the head of the avocados dataset. What columns are available?
* For each avocado size group, calculate the total number sold, storing as nb_sold_by_size.
* Create a bar plot of the number of avocados sold by size.

```py
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Look at the first few rows of data
print(avocados.head())

# Get the total number of avocados sold of each size
nb_sold_by_size = avocados.groupby('size')["nb_sold"]。sum()

# Create a bar plot of the number of avocados sold by size
nb_sold_by_size.plot(kind="bar")

# Show the plot
plt.show()
```
```
date          type  year  avg_price   size    nb_sold
0  2015-12-27  conventional  2015       0.95  small  9.627e+06
1  2015-12-20  conventional  2015       0.98  small  8.710e+06
2  2015-12-13  conventional  2015       0.93  small  9.855e+06
3  2015-12-06  conventional  2015       0.89  small  9.405e+06
4  2015-11-29  conventional  2015       0.99  small  8.095e+06
```
---
### Changes in sales over time

Line plots are designed to visualize the relationship between two numeric variables, where each data values is connected to the next one. They are especially useful for visualizing the change in a number over time since each time point is naturally connected to the next time point. In this exercise, you'll visualize the change in avocado sales over three years.

pandas has been imported as pd, and avocados is available.

**_Instructions:_**
* Get the total number of avocados sold on each date. The DataFrame has two rows for each date—one for organic, and one for conventional. Save this as nb_sold_by_date.
* Create a line plot of the number of avocados sold.
* Show the plot.

```py
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Get the total number of avocados sold on each date
nb_sold_by_date = avocados.groupby('date')['nb_sold'].sum()

# Create a line plot of the number of avocados sold by date
nb_sold_by_date.plot(kind = 'line')

# Show the plot
plt.show()
```
---
### Avocado supply and demand

Scatter plots are ideal for visualizing relationships between numerical variables. In this exercise, you'll compare the number of avocados sold to average price and see if they're at all related. If they're related, you may be able to use one number to predict the other.

matplotlib.pyplot has been imported as plt, pandas has been imported as pd, and avocados is available.

**_Instructions:_**
* Create a scatter plot with nb_sold on the x-axis and avg_price on the y-axis. Title it "Number of avocados sold vs. average price".

```py
# Scatter plot of avg_price vs. nb_sold with title
avocados.plot(x='nb_sold',y='avg_price', kind = 'scatter', title = "Number of avocados sold vs. average price")

# Show the plot
plt.show()
```
---
### Price of conventional vs. organic avocados

Creating multiple plots for different subsets of data allows you to compare groups. In this exercise, you'll create multiple histograms to compare the prices of conventional and organic avocados.

matplotlib.pyplot has been imported as plt and pandas has been imported as pd.

**_Instructions:_**
* Subset avocados for the conventional type, and the average price column. Create a histogram.
* Create a histogram of avg_price for organic type avocados.
* Add a legend to your plot, with the names "conventional" and "organic".

```py
# Histogram of conventional avg_price
avocados[avocados['type'] == 'conventional']['avg_price'].hist()

# Histogram of organic avg_price
avocados[avocados['type'] == 'organic']['avg_price'].hist()

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```

**_Instructions:_**
* Modify your code to adjust the transparency of both histograms to 0.5 to see how much overlap there is between the two distributions.

```py
# Modify histogram transparency to 0.5
avocados[avocados["type"] == "conventional"]["avg_price"].hist(alpha=0.5)

# Modify histogram transparency to 0.5
avocados[avocados["type"] == "organic"]["avg_price"].hist(alpha=0.5)

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```

**_Instructions:_**
* Modify your code to use 20 bins in both histograms.

```py
# Modify bins to 20
avocados[avocados["type"] == "conventional"]["avg_price"].hist(bins=20, alpha=0.5)

# Modify bins to 20
avocados[avocados["type"] == "organic"]["avg_price"].hist(bins=20, alpha=0.5)

# Add a legend
plt.legend(["conventional", "organic"])

# Show the plot
plt.show()
```
---
### Finding missing values

Missing values are everywhere, and you don't want them interfering with your work. Some functions ignore missing data by default, but that's not always the behavior you might want. Some functions can't handle missing values at all, so these values need to be taken care of before you can use them. If you don't know where your missing values are, or if they exist, you could make mistakes in your analysis. In this exercise, you'll determine if there are missing values in the dataset, and if so, how many.

pandas has been imported as pd and avocados_2016, a subset of avocados that contains only sales from 2016, is available.

**_Instructions:_**
* Print a DataFrame that shows whether each value in avocados_2016 is missing or not.
* Print a summary that shows whether any value in each column is missing or not.
* Create a bar plot of the total number of missing values in each column.

```py
# Import matplotlib.pyplot with alias plt
import matplotlib.pyplot as plt

# Check individual values for missing values
print(avocados_2016.isna())

# Check each column for missing values
print(avocados_2016.isna().any())

# Bar plot of missing values by variable
avocados_2016.isna().sum().plot(kind="bar")

# Show plot
plt.show()
```
---
### Removing missing values

Now that you know there are some missing values in your DataFrame, you have a few options to deal with them. One way is to remove them from the dataset completely. In this exercise, you'll remove missing values by removing all rows that contain missing values.

pandas has been imported as pd and avocados_2016 is available.

**_Instructions:_**
* Remove the rows of avocados_2016 that contain missing values and store the remaining rows in avocados_complete.
* Verify that all missing values have been removed from avocados_complete. Calculate each column that has NAs and print.

```py
# Remove rows with missing values
avocados_complete = avocados_2016.dropna()

# Check if any columns contain missing values
print(avocados_complete.isna().any())
```
```
date               False
avg_price          False
total_sold         False
small_sold         False
large_sold         False
xl_sold            False
total_bags_sold    False
small_bags_sold    False
large_bags_sold    False
xl_bags_sold       False
dtype: bool
```
---
### Replacing missing values

Another way of handling missing values is to replace them all with the same value. For numerical variables, one option is to replace values with 0— you'll do this here. However, when you replace missing values, you make assumptions about what a missing value means. In this case, you will assume that a missing number sold means that no sales for that avocado type were made that week.

In this exercise, you'll see how replacing missing values can affect the distribution of a variable using histograms. You can plot histograms for multiple variables at a time as follows:

`dogs[["height_cm", "weight_kg"]].hist()`

pandas has been imported as pd and matplotlib.pyplot has been imported as plt. The avocados_2016 dataset is available.

**_Instructions:_**
* A list has been created, cols_with_missing, containing the names of columns with missing values: "small_sold", "large_sold", and "xl_sold".
* Create a histogram of those columns.

```py
# List the columns with missing values
cols_with_missing = ["small_sold", "large_sold", "xl_sold"]

# Create histograms showing the distributions cols_with_missing
avocados_2016[cols_with_missing].hist()

# Show the plot
plt.show()
```
**_Instructions:_**
* Replace the missing values of avocados_2016 with 0s and store the result as avocados_filled.
* Create a histogram of the cols_with_missing columns of avocados_filled.

```py
# From previous step
cols_with_missing = ["small_sold", "large_sold", "xl_sold"]
avocados_2016[cols_with_missing].hist()
plt.show()

# Fill in missing values with 0
avocados_filled = avocados_2016.fillna(0)

# Create histograms of the filled columns
avocados_filled[cols_with_missing].hist()

# Show the plot
plt.show()
```
---
### List of dictionaries

You recently got some new avocado data from 2019 that you'd like to put in a DataFrame using the list of dictionaries method. Remember that with this method, you go through the data row by row.

date|small_sold	|large_sold
--|--|--
"2019-11-03"	|10376832	|7835071
"2019-11-10"	|10717154|	8561348

**_Instructions:_**
* Create a list of dictionaries with the new data called avocados_list.
* Convert the list into a DataFrame called avocados_2019.

```py
# Create a list of dictionaries with new data
avocados_list = [
    {'date': '2019-11-03', 'small_sold': 10376832, 'large_sold': 7835071},
    {'date': '2019-11-10', 'small_sold': 10717154, 'large_sold': 8561348},
]

# Convert list into DataFrame
avocados_2019 = pd.DataFrame(avocados_list)

# Print the new DataFrame
print(avocados_2019)
```
```
date  small_sold  large_sold
0  2019-11-03    10376832     7835071
1  2019-11-10    10717154     8561348
```
---
### Dictionary of lists

Some more data just came in! This time, you'll use the dictionary of lists method, parsing the data column by column.

date|small_sold	|large_sold
--|--|--
"2019-11-17"	|10859987	|7674135
"2019-12-01"	|9291631	|6238096

**_Instructions:_**
* Create a dictionary of lists with the new data called avocados_dict.
* Convert the dictionary to a DataFrame called avocados_2019.

```py
# Create a dictionary of lists with new data
avocados_dict = {
  "date": ["2019-11-17","2019-12-01"],
  "small_sold": [10859987,9291631],
  "large_sold": [7674135,6238096]
}

# Convert dictionary into DataFrame
avocados_2019 = pd.DataFrame(avocados_dict)

# Print the new DataFrame
print(avocados_2019)
```
```
date  small_sold  large_sold
0  2019-11-17    10859987     7674135
1  2019-12-01     9291631     6238096
```
---
### CSV to DataFrame

You work for an airline, and your manager has asked you to do a competitive analysis and see how often passengers flying on other airlines are involuntarily bumped from their flights. You got a CSV file (airline_bumping.csv) from the Department of Transportation containing data on passengers that were involuntarily denied boarding in 2016 and 2017, but it doesn't have the exact numbers you want. In order to figure this out, you'll need to get the CSV into a pandas DataFrame and do some manipulation!

pandas is imported for you as pd. "airline_bumping.csv" is in your working directory.

**_Instructions:_**
* Read the CSV file "airline_bumping.csv" and store it as a DataFrame called airline_bumping.
* Print the first few rows of airline_bumping.

```py
# Read CSV as DataFrame called airline_bumping
airline_bumping = pd.read_csv('airline_bumping.csv')

# Take a look at the DataFrame
print(airline_bumping.head())
```
```
             airline  year  nb_bumped  total_passengers
0    DELTA AIR LINES  2017        679          99796155
1     VIRGIN AMERICA  2017        165           6090029
2    JETBLUE AIRWAYS  2017       1475          27255038
3    UNITED AIRLINES  2017       2067          70030765
4  HAWAIIAN AIRLINES  2017         92           8422734
```
**_Instructions:_**
* For each airline group, select the nb_bumped, and total_passengers columns, and calculate the sum (for both years). Store this as airline_totals.

```py
# From previous step
airline_bumping = pd.read_csv("airline_bumping.csv")
print(airline_bumping.head())

# For each airline, select nb_bumped and total_passengers and sum
airline_totals = airline_bumping.groupby('airline')[['nb_bumped','total_passengers']].sum()
```
```
             airline  year  nb_bumped  total_passengers
0    DELTA AIR LINES  2017        679          99796155
1     VIRGIN AMERICA  2017        165           6090029
2    JETBLUE AIRWAYS  2017       1475          27255038
3    UNITED AIRLINES  2017       2067          70030765
4  HAWAIIAN AIRLINES  2017         92           8422734
```
**_Instructions:_**
* Create a new column of airline_totals called bumps_per_10k, which is the number of passengers bumped per 10,000 passengers in 2016 and 2017.

```py
# From previous steps
airline_bumping = pd.read_csv("airline_bumping.csv")
print(airline_bumping.head())
airline_totals = airline_bumping.groupby("airline")[["nb_bumped", "total_passengers"]].sum()

# Create new col, bumps_per_10k: no. of bumps per 10k passengers for each airline
airline_totals["bumps_per_10k"] = airline_totals["nb_bumped"] / airline_totals["total_passengers"] * 10000

# Print airline_totals
print(airline_totals)
```
```
                     nb_bumped  total_passengers  bumps_per_10k
airline                                                        
ALASKA AIRLINES           1392          36543121          0.381
AMERICAN AIRLINES        11115         197365225          0.563
DELTA AIR LINES           1591         197033215          0.081
EXPRESSJET AIRLINES       3326          27858678          1.194
FRONTIER AIRLINES         1228          22954995          0.535
HAWAIIAN AIRLINES          122          16577572          0.074
JETBLUE AIRWAYS           3615          53245866          0.679
SKYWEST AIRLINES          3094          47091737          0.657
SOUTHWEST AIRLINES       18585         228142036          0.815
SPIRIT AIRLINES           2920          32304571          0.904
UNITED AIRLINES           4941         134468897          0.367
VIRGIN AMERICA             242          12017967          0.201
```
---
### DataFrame to CSV

You're almost there! To make things easier to read, you'll need to sort the data and export it to CSV so that your colleagues can read it.

pandas as pd has been imported for you.

**_Instructions:_**
* Sort airline_totals by the values of bumps_per_10k from highest to lowest, storing as airline_totals_sorted.
* Print your sorted DataFrame.
* Save the sorted DataFrame as a CSV called "airline_totals_sorted.csv".

```py
# Create airline_totals_sorted
airline_totals_sorted = airline_totals.sort_values('bumps_per_10k', ascending=False)

# Print airline_totals_sorted
print(airline_totals_sorted)

# Save as airline_totals_sorted.csv
airline_totals_sorted.to_csv("airline_totals_sorted.csv")
```
```
                     nb_bumped  total_passengers  bumps_per_10k
airline                                                        
EXPRESSJET AIRLINES       3326          27858678          1.194
SPIRIT AIRLINES           2920          32304571          0.904
SOUTHWEST AIRLINES       18585         228142036          0.815
JETBLUE AIRWAYS           3615          53245866          0.679
SKYWEST AIRLINES          3094          47091737          0.657
AMERICAN AIRLINES        11115         197365225          0.563
FRONTIER AIRLINES         1228          22954995          0.535
ALASKA AIRLINES           1392          36543121          0.381
UNITED AIRLINES           4941         134468897          0.367
VIRGIN AMERICA             242          12017967          0.201
DELTA AIR LINES           1591         197033215          0.081
HAWAIIAN AIRLINES          122          16577572          0.074
```
Wrap-up

Congratulations! You’ve now covered the basics of using pandas.

Recap

In chapter 1, you saw how to subset and sort DataFrames and how to add new columns. In chapter 2, you saw several methods for aggregating and grouping data to calculate summary statistics. In chapter 3, you saw how using indexing and slicing allows for simpler subsetting. In chapter 4, you saw how to visualize a DataFrame, and how to read data from and write data to CSV files.

Congratulations!

Congratulations, and have fun learning!
