---
layout: post
title: DataCamp Data Supervised Learning with scikit-learn
date: 2024-05-05 11:18 +0800
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

**Course Description**

Grow your machine learning skills with scikit-learn and discover how to use this popular Python library to train models using labeled data. In this course, you'll learn how to make powerful predictions, such as whether a customer is will churn from your business, whether an individual has diabetes, and even how to tell classify the genre of a song. Using real-world datasets, you'll find out how to build predictive models, tune their parameters, and determine how well they will perform with unseen data.

## Classification
---
### scikit-learn syntax

```py
from sklearn.module import Model
model = Model()
model.fit(X, y)
predictions = model.predict(X_new)
print(predictions)
```
```
array([0, 0, 0, 0, 1, 0])
```
### Using scikit-learn to fit a classifier
```py
from sklearn.neighbors import KNeighborsClassifier

X = churn_df[["total_day_charge", "total_eve_charge"]].values
y = churn_df["churn"].values

print(X.shape, y.shape)
```
```
(3333, 2), (3333,)
```
```py
knn = KNeighborsClassifier(n_neighbors=15)
knn.fit(X, y)
```
### Predicting on unlabeled data
```py
X_new = np.array([[56.8, 17.5], [24.4, 24.1], [50.1, 10.9]])
print(X_new.shape)
```
```
(3, 2)
```
```py
predictions = knn.predict(X_new)
print('Predictions: {}'.format(predictions))
```
```
Predictions: [1 0 0]
```
---
### k-Nearest Neighbors: Fit

In this exercise, you will build your first classification model using the churn_df dataset, which has been preloaded for the remainder of the chapter.

The target, "churn", needs to be a single column with the same number of observations as the feature data. The feature data has already been converted into numpy arrays.

**_Instructions:_**
* Import KNeighborsClassifier from sklearn.neighbors.
* Instantiate a KNeighborsClassifier called knn with 6 neighbors.
* Fit the classifier to the data using the .fit() method.

```py
# Import KNeighborsClassifier
from sklearn.neighbors import KNeighborsClassifier

y = churn_df["churn"].values
X = churn_df[["account_length", "customer_service_calls"]].values

# Create a KNN classifier with 6 neighbors
knn = KNeighborsClassifier(n_neighbors=6)

# Fit the classifier to the data
knn.fit(X, y)
```
---
### k-Nearest Neighbors: Predict

Now you have fit a KNN classifier, you can use it to predict the label of new data points. All available data was used for training, however, fortunately, there are new observations available. These have been preloaded for you as X_new.

The model knn, which you created and fit the data in the last exercise, has been preloaded for you. You will use your classifier to predict the labels of a set of new data points:

```
X_new = np.array([[30.0, 17.5],
                  [107.0, 24.1],
                  [213.0, 10.9]])
```
**_Instructions:_**
* Create y_pred by predicting the target values of the unseen features X_new.
* Print the predicted labels for the set of predictions.

```py
# Predict the labels for the X_new
y_pred = knn.predict(X_new)

# Print the predictions
print("Predictions: {}".format(y_pred))
```
```
Predictions: [0 1 0]
```
---
### Train/test split
```py
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y,
                                  test_size=0.3, random_state=21, stratify=y)

knn = KNeighborsClassifier(n_neighbors=6)
knn.fit(X_train, y_train)
print(knn.score(X_test, y_test))
```
```
0.8800599700149925
```

### Model complexity

Larger k = less complex model = can cause underfitting
Smaller k = more complex model = can lead to overfitting

### Model complexity and over/underfitting
```py
train_accuracies = {}
test_accuracies = {}

neighbors = np.arange(1, 26)
for neighbor in neighbors:    
  knn = KNeighborsClassifier(n_neighbors=neighbor)    
  knn.fit(X_train, y_train)    
  train_accuracies[neighbor] = knn.score(X_train, y_train)    
  test_accuracies[neighbor] = knn.score(X_test, y_test)
```

### Plotting our result
```py
splt.figure(figsize=(8, 6))
plt.title("KNN: Varying Number of Neighbors")
plt.plot(neighbors, train_accuracies.values(), label="Training Accuracy")
plt.plot(neighbors, test_accuracies.values(), label="Testing Accuracy")
plt.legend()
plt.xlabel("Number of Neighbors")
plt.ylabel("Accuracy")
plt.show()
```
---
### Train/test split + computing accuracy

It's time to practice splitting your data into training and test sets with the churn_df dataset!

NumPy arrays have been created for you containing the features as X and the target variable as y.

**_Instructions:_**
* Import train_test_split from sklearn.model_selection.
* Split X and y into training and test sets, setting test_size equal to 20%, random_state to 42, and ensuring the target label proportions reflect that of the original dataset.
* Fit the knn model to the training data.
* Compute and print the model's accuracy for the test data.

```py
# Import the module
from sklearn.model_selection import train_test_split

X = churn_df.drop("churn", axis=1).values
y = churn_df["churn"].values

# Split into training and test sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)
knn = KNeighborsClassifier(n_neighbors=5)

# Fit the classifier to the training data
knn.fit(X_train, y_train)

# Print the accuracy
print(knn.score(X_test, y_test))
```
```
0.8740629685157422
```
---
### Overfitting and underfitting

Interpreting model complexity is a great way to evaluate supervised learning performance. Your aim is to produce a model that can interpret the relationship between features and the target variable, as well as generalize well when exposed to new observations.

The training and test sets have been created from the churn_df dataset and preloaded as X_train, X_test, y_train, and y_test.

In addition, KNeighborsClassifier has been imported for you along with numpy as np.

**_Instructions:_**
* Create neighbors as a numpy array of values from 1 up to and including 12.
* Instantiate a KNN classifier, with the number of neighbors equal to the neighbor iterator.
* Fit the model to the training data.
* Calculate accuracy scores for the training set and test set separately using the .score() method, and assign the results to the index of the train_accuracies and test_accuracies dictionaries, respectively.

```py
# Create neighbors
neighbors = np.arange(1, 13)
train_accuracies = {}
test_accuracies = {}

for neighbor in neighbors:

	# Set up a KNN Classifier
	knn = KNeighborsClassifier(n_neighbors=neighbor)

	# Fit the model
	knn.fit(X_train, y_train)

	# Compute accuracy
	train_accuracies[neighbor] = knn.score(X_train, y_train)  
	test_accuracies[neighbor] = knn.score(X_test, y_test)
print(neighbors, '\n', train_accuracies, '\n', test_accuracies)
```
```
[ 1  2  3  4  5  6  7  8  9 10 11 12]
 {1: 1.0, 2: 0.887943971985993, 3: 0.9069534767383692, 4: 0.8734367183591796, 5: 0.8829414707353677, 6: 0.8689344672336168, 7: 0.8754377188594297, 8: 0.8659329664832416, 9: 0.8679339669834918, 10: 0.8629314657328664, 11: 0.864432216108054, 12: 0.8604302151075538}
 {1: 0.7871064467766117, 2: 0.8500749625187406, 3: 0.8425787106446777, 4: 0.856071964017991, 5: 0.8553223388305847, 6: 0.861319340329835, 7: 0.863568215892054, 8: 0.8605697151424287, 9: 0.8620689655172413, 10: 0.8598200899550225, 11: 0.8598200899550225, 12: 0.8590704647676162}
```
---
### Visualizing model complexity

Now you have calculated the accuracy of the KNN model on the training and test sets using various values of n_neighbors, you can create a model complexity curve to visualize how performance changes as the model becomes less complex!

The variables neighbors, train_accuracies, and test_accuracies, which you generated in the previous exercise, have all been preloaded for you. You will plot the results to aid in finding the optimal number of neighbors for your model.

**_Instructions:_**
* Add a title "KNN: Varying Number of Neighbors".
* Plot the .values() method of train_accuracies on the y-axis against neighbors on the x-axis, with a label of "Training Accuracy".
* Plot the .values() method of test_accuracies on the y-axis against neighbors on the x-axis, with a label of "Testing Accuracy".

```py
# Add a title
plt.title("KNN: Varying Number of Neighbors")

# Plot training accuracies
plt.plot(neighbors, train_accuracies.values(), label="Training Accuracy")

# Plot test accuracies
plt.plot(neighbors, test_accuracies.values(), label="Testing Accuracy")

plt.legend()
plt.xlabel("Number of Neighbors")
plt.ylabel("Accuracy")

# Display the plot
plt.show()
```
---
## Regression
---
### Predicting blood glucose levels
```py
import pandas as pd
diabetes_df = pd.read_csv("diabetes.csv")
print(diabetes_df.head())
```

### Creating feature and target arrays
```py
X = diabetes_df.drop("glucose", axis=1).values
y = diabetes_df["glucose"].values
print(type(X), type(y))
```

```
<class 'numpy.ndarray'> <class 'numpy.ndarray'>
```

### Making predictions from a single feature

```py
X_bmi = X[:, 3]
print(y.shape, X_bmi.shape)
```
```
(752,) (752,)
```
```py
X_bmi = X_bmi.reshape(-1, 1)
print(X_bmi.shape)
```
```
(752, 1)
```

### Plotting glucose vs. body mass index
```py
import matplotlib.pyplot as plt
plt.scatter(X_bmi, y)
plt.ylabel("Blood Glucose (mg/dl)")
plt.xlabel("Body Mass Index")
plt.show()
```

### Fitting a regression model
```py
from sklearn.linear_model import LinearRegression

reg = LinearRegression()
reg.fit(X_bmi, y)

predictions = reg.predict(X_bmi)
plt.scatter(X_bmi, y)
plt.plot(X_bmi, predictions)
plt.ylabel("Blood Glucose (mg/dl)")
plt.xlabel("Body Mass Index")
plt.show()
```
---
### Creating features

In this chapter, you will work with a dataset called sales_df, which contains information on advertising campaign expenditure across different media types, and the number of dollars generated in sales for the respective campaign. The dataset has been preloaded for you. Here are the first two rows:

```
     tv        radio      social_media    sales
1    13000.0   9237.76    2409.57         46677.90
2    41000.0   15886.45   2913.41         150177.83
```
You will use the advertising expenditure as features to predict sales values, initially working with the "radio" column. However, before you make any predictions you will need to create the feature and target arrays, reshaping them to the correct format for scikit-learn.

**_Instructions:_**
* Create X, an array of the values from the sales_df DataFrame's "radio" column.
* Create y, an array of the values from the sales_df DataFrame's "sales" column.
* Reshape X into a two-dimensional NumPy array.

```py
import numpy as np

# Create X from the radio column's values
X = sales_df['radio'].values

# Create y from the sales column's values
y = sales_df['sales'].values

# Reshape X
X = X.reshape(-1, 1)

# Check the shape of the features and targets
print(X.shape, y.shape)
```
```
(4546, 1) (4546,)
```
---
### Building a linear regression model

Now you have created your feature and target arrays, you will train a linear regression model on all feature and target values.

As the goal is to assess the relationship between the feature and target values there is no need to split the data into training and test sets.

X and y have been preloaded for you as follows:
```
y = sales_df["sales"].values
X = sales_df["radio"].values.reshape(-1, 1)
```

**_Instructions:_**
* Import LinearRegression.
* Instantiate a linear regression model.
* Predict sales values using X, storing as predictions.

```py
# Import LinearRegression
from sklearn.linear_model import LinearRegression

# Create the model
reg = LinearRegression()

# Fit the model to the data
reg.fit(X,y)

# Make predictions
predictions = reg.predict(X)

print(predictions[:5])
```
```
[ 95491.17119147 117829.51038393 173423.38071499 291603.11444202 111137.28167129]
```
---
### Visualizing a linear regression model

Now you have built your linear regression model and trained it using all available observations, you can visualize how well the model fits the data. This allows you to interpret the relationship between radio advertising expenditure and sales values.

The variables X, an array of radio values, y, an array of sales values, and predictions, an array of the model's predicted values for y given X, have all been preloaded for you from the previous exercise.

**_Instructions:_**
* Import matplotlib.pyplot as plt.
* Create a scatter plot visualizing y against X, with observations in blue.
* Draw a red line plot displaying the predictions against X.

```py
# Import matplotlib.pyplot
import matplotlib.pyplot as plt

# Create scatter plot
plt.scatter(X, y, color="blue")

# Create line plot
plt.plot(X, predictions, color="red")
plt.xlabel("Radio Expenditure ($)")
plt.ylabel("Sales ($)")

# Display the plot
plt.show()
```
---
### Linear regression using all features
```py
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

reg_all = LinearRegression()
reg_all.fit(X_train, y_train)
y_pred = reg_all.predict(X_test)
```

### R-squared in scikit-learn
```py
reg_all.score(X_test, y_test)
```
```
0.356302876407827
```

### RMSE in scikit-learn
```py
from sklearn.metrics import mean_squared_error
mean_squared_error(y_test, y_pred, squared=False)
```
```
24.028109426907236
```
---
### Fit and predict for regression

Now you have seen how linear regression works, your task is to create a multiple linear regression model using all of the features in the sales_df dataset, which has been preloaded for you. As a reminder, here are the first two rows:
```
     tv        radio      social_media    sales
1    13000.0   9237.76    2409.57         46677.90
2    41000.0   15886.45   2913.41         150177.83
```
You will then use this model to predict sales based on the values of the test features.

LinearRegression and train_test_split have been preloaded for you from their respective modules.

**_Instructions:_**
* Create X, an array containing values of all features in sales_df, and y, containing all values from the "sales" column.
* Instantiate a linear regression model.
* Fit the model to the training data.
* Create y_pred, making predictions for sales using the test features.

```py
# Create X and y arrays
X = sales_df.drop("sales", axis=1).values
y = sales_df["sales"].values

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

# Instantiate the model
reg = LinearRegression()

# Fit the model to the data
reg.fit(X_train,y_train)

# Make predictions
y_pred = reg.predict(X_test)
print("Predictions: {}, Actual Values: {}".format(y_pred[:2], y_test[:2]))
```
```
Predictions: [53176.66154234 70996.19873235], Actual Values: [55261.28 67574.9 ]
```
---
### Regression performance

Now you have fit a model, reg, using all features from sales_df, and made predictions of sales values, you can evaluate performance using some common regression metrics.

The variables X_train, X_test, y_train, y_test, and y_pred, along with the fitted model, reg, all from the last exercise, have been preloaded for you.

Your task is to find out how well the features can explain the variance in the target values, along with assessing the model's ability to make predictions on unseen data.

**_Instructions:_**
* Import mean_squared_error.
* Calculate the model's R-squared score by passing the test feature values and the test target values to an appropriate method.
* Calculate the model's root mean squared error using y_test and y_pred.
* Print r_squared and rmse.

```py
# Import mean_squared_error
from sklearn.metrics import mean_squared_error

# Compute R-squared
r_squared = reg.score(X_test, y_test)

# Compute RMSE
rmse = mean_squared_error(y_test, y_pred,squared=False)

# Print the metrics
print("R^2: {}".format(r_squared))
print("RMSE: {}".format(rmse))
```
```
R^2: 0.9990165886162027
RMSE: 2942.372219812037
```
---
### Cross-validation in scikit-learn
```py
from sklearn.model_selection import cross_val_score, KFold
kf = KFold(n_splits=6, shuffle=True, random_state=42)
reg = LinearRegression()
cv_results = cross_val_score(reg, X, y, cv=kf)
```

###Evaluating cross-validation peformance
```py
print(cv_results)
```
```
[0.70262578, 0.7659624, 0.75188205, 0.76914482, 0.72551151, 0.73608277]
```
```py
print(np.mean(cv_results), np.std(cv_results))
```
```
0.7418682216666667 0.023330243960652888
```
```py
print(np.quantile(cv_results, [0.025, 0.975]))
```
```
array([0.7054865, 0.76874702])
```
---
### Cross-validation for R-squared

Cross-validation is a vital approach to evaluating a model. It maximizes the amount of data that is available to the model, as the model is not only trained but also tested on all of the available data.

In this exercise, you will build a linear regression model, then use 6-fold cross-validation to assess its accuracy for predicting sales using social media advertising expenditure. You will display the individual score for each of the six-folds.

The sales_df dataset has been split into y for the target variable, and X for the features, and preloaded for you. LinearRegression has been imported from sklearn.linear_model.

**_Instructions:_**
* Import KFold and cross_val_score.
* Create kf by calling KFold(), setting the number of splits to six, shuffle to True, and setting a seed of 5.
* Perform cross-validation using reg on X and y, passing kf to cv.

```py
# Import the necessary modules
from sklearn.model_selection import cross_val_score, KFold

# Create a KFold object
kf = KFold(n_splits=6, shuffle=True, random_state=5)

reg = LinearRegression()

# Compute 6-fold cross-validation scores
cv_scores = cross_val_score(reg, X, y, cv=kf)

# Print scores
print(cv_scores)
```
```
[0.74451678 0.77241887 0.76842114 0.7410406  0.75170022 0.74406484]
```
---
### Analyzing cross-validation metrics

Now you have performed cross-validation, it's time to analyze the results.

You will display the mean, standard deviation, and 95% confidence interval for cv_results, which has been preloaded for you from the previous exercise.

numpy has been imported for you as np.

**_Instructions:_**
* Calculate and print the mean of the results.
* Calculate and print the standard deviation of cv_results.
* Display the 95% confidence interval for your results using np.quantile()

```py
# Print the mean
print(np.mean(cv_results))

# Print the standard deviation
print(np.std(cv_results))

# Print the 95% confidence interval
print(np.quantile(cv_results, [0.025, 0.975]))
```
```
0.7536937416666666
0.012305386274436092
[0.74141863 0.77191915]
```
---
