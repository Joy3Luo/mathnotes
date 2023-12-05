---
layout: post
title: DataCamp Joining Data with pandas
date: 2023-12-04 11:18 +0800
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

Being able to combine and work with multiple datasets is an essential skill for any aspiring Data Scientist. pandas is a crucial cornerstone of the Python data science ecosystem, with Stack Overflow recording 5 million views for pandas questions. Learn to handle multiple DataFrames by combining, organizing, joining, and reshaping them using pandas. You'll work with datasets from the World Bank and the City Of Chicago. You will finish the course with a solid skillset for data-joining in pandas.

## Data Merging Basics
---
### Your first inner join

You have been tasked with figuring out what the most popular types of fuel used in Chicago taxis are. To complete the analysis, you need to merge the taxi_owners and taxi_veh tables together on the vid column. You can then use the merged table along with the .value_counts() method to find the most common fuel_type.

Since you'll be working with pandas throughout the course, the package will be preloaded for you as pd in each exercise in this course. Also the taxi_owners and taxi_veh DataFrames are loaded for you.

**_Instructions:_**
* Merge taxi_owners with taxi_veh on the column vid, and save the result to taxi_own_veh.

```py
# Merge the taxi_owners and taxi_veh tables
taxi_own_veh = taxi_owners.merge(taxi_veh, on = 'vid')

# Print the column names of the taxi_own_veh
print(taxi_own_veh.columns)
```
```
Index(['rid', 'vid', 'owner_x', 'address', 'zip', 'make', 'model', 'year', 'fuel_type', 'owner_y'], dtype='object')
```
**_Instructions:_**
* Set the left and right table suffixes for overlapping columns of the merge to _own and _veh, respectively.

```py
# Merge the taxi_owners and taxi_veh tables setting a suffix
taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid', suffixes=('_own','_veh'))

# Print the column names of taxi_own_veh
print(taxi_own_veh.columns)
```
```
Index(['rid', 'vid', 'owner_own', 'address', 'zip', 'make', 'model', 'year', 'fuel_type', 'owner_veh'], dtype='object')
```
**_Instructions:_**
* Select the fuel_type column from taxi_own_veh and print the value_counts() to find the most popular fuel_types used.

```py
# Merge the taxi_owners and taxi_veh tables setting a suffix
taxi_own_veh = taxi_owners.merge(taxi_veh, on='vid', suffixes=('_own','_veh'))

# Print the value_counts to find the most popular fuel_type
print(taxi_own_veh['fuel_type'].value_counts())
```
```
HYBRID                    2792
GASOLINE                   611
FLEX FUEL                   89
COMPRESSED NATURAL GAS      27
Name: fuel_type, dtype: int64
```
---
### Inner joins and number of rows returned

All of the merges you have studied to this point are called inner joins. It is necessary to understand that inner joins only return the rows with matching values in both tables. You will explore this further by reviewing the merge between the wards and census tables, then comparing it to merges of copies of these tables that are slightly altered, named wards_altered, and census_altered. The first row of the wards column has been changed in the altered tables. You will examine how this affects the merge between them. The tables have been loaded for you.

For this exercise, it is important to know that the wards and census tables start with 50 rows.

**_Instructions:_**
* Merge wards and census on the ward column and save the result to wards_census.

```py
# Merge the wards and census tables on the ward column
wards_census = wards.merge(census, on = 'ward')

# Print the shape of wards_census
print('wards_census table shape:', wards_census.shape)
```
```
wards_census table shape: (50, 9)
```
**_Instructions:_**
* Merge the wards_altered and census tables on the ward column, and notice the difference in returned rows.

```py
# Print the first few rows of the wards_altered table to view the change
print(wards_altered[['ward']].head())

# Merge the wards_altered and census tables on the ward column
wards_altered_census = wards_altered.merge(census, on = 'ward')

# Print the shape of wards_altered_census
print('wards_altered_census table shape:', wards_altered_census.shape)
```
```
ward
0   61
1    2
2    3
3    4
4    5
wards_altered_census table shape: (49, 9)
```
**_Instructions:_**
* Merge the wards and census_altered tables on the ward column, and notice the difference in returned rows.

```py
# Print the first few rows of the census_altered table to view the change
print(census_altered[['ward']].head())

# Merge the wards and census_altered tables on the ward column
wards_census_altered = wards.merge(census_altered, on = 'ward')

# Print the shape of wards_census_altered
print('wards_census_altered table shape:', wards_census_altered.shape)
```
```
   ward
0  None
1     2
2     3
3     4
4     5
wards_census_altered table shape: (49, 9)
```
---
### One-to-many merge

A business may have one or multiple owners. In this exercise, you will continue to gain experience with one-to-many merges by merging a table of business owners, called biz_owners, to the licenses table. Recall from the video lesson, with a one-to-many relationship, a row in the left table may be repeated if it is related to multiple rows in the right table. In this lesson, you will explore this further by finding out what is the most common business owner title. (i.e., secretary, CEO, or vice president)

The licenses and biz_owners DataFrames are loaded for you.

**_Instructions:_**
* Starting with the licenses table on the left, merge it to the biz_owners table on the column account, and save the results to a variable named licenses_owners.Group licenses_owners by title and count the number of accounts for each title. Save the result as counted_df
* Group licenses_owners by title and count the number of accounts for each title. Save the result as counted_df
* Sort counted_df by the number of accounts in descending order, and save this as a variable named sorted_df.
* Use the .head() method to print the first few rows of the sorted_df.

```py
# Merge the licenses and biz_owners table on account
licenses_owners = licenses.merge(biz_owners, on = 'account')

# Group the results by title then count the number of accounts
counted_df = licenses_owners.groupby('title').agg({'account':'count'})

# Sort the counted_df in desending order
sorted_df = counted_df.sort_values(by='account', ascending=False)

# Use .head() method to print the first few rows of sorted_df
print(sorted_df.head())
```
```
                 account
title                   
PRESIDENT           6259
SECRETARY           5205
SOLE PROPRIETOR     1658
OTHER               1200
VICE PRESIDENT       970
```
---
