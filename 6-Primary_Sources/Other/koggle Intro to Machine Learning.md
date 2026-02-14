Title: koggle Intro to Machine Learning
Author: [[koggle.com]]
Tags: #other #AI 


# Notes
#### 1. How Models Work
#### 2. Basic Data Exploration
```python
melbourne_data.describe()

```
#### 3. Your First Machine Learning Model
``` python
# dropna drops missing values (think of na as "not available")
melbourne_data = melbourne_data.dropna(axis=0)
```
```python
# Selecting the prediction target
y = melbourne_data.Price

```
```python
# select features
melbourne_features = ['Rooms', 'Bathroom', 'Landsize', 'Lattitude', 'Longtitude']

X = melbourne_data[melbourne_features]

```
The steps to building and using a model are:
1. Define: What type of model will it be? A decision tree? Some other type of model? Some other parameters of the model type are specified too.
2. Fit: Capture patterns from provided data. This is the heart of modeling.
3. Predict: Just what it sounds like
4. Evaluate: Determine how accurate the model's predictions are.
```python
from sklearn.tree import DecisionTreeRegressor

# Define model. Specify a number for random_state to ensure same results each run
melbourne_model = DecisionTreeRegressor(random_state=1)

# Fit model
melbourne_model.fit(X, y)
```
Many machine learning models allow some randomness in model training. Specifying a number for random_state ensures you get the same results in each run. This is considered a good practice.
```python
print("Making predictions for the following 5 houses:")
print(X.head())
print("The predictions are")
print(melbourne_model.predict(X.head()))
```
#### 4. Model Validation
Mean Absolute Error (also called MAE) -> On average, our predictions are off by about X.
```python
from sklearn.metrics import mean_absolute_error

predicted_home_prices = melbourne_model.predict(X)
mean_absolute_error(y, predicted_home_prices)
```
The scikit-learn library has a function train_test_split to break up the data into two pieces. We'll use some of that data as training data to fit the model, and we'll use the other data as validation data to calculate mean_absolute_error.
```python
from sklearn.model_selection import train_test_split

# split data into training and validation data, for both features and target
# The split is based on a random number generator. Supplying a numeric value to
# the random_state argument guarantees we get the same split every time we
# run this script.
train_X, val_X, train_y, val_y = train_test_split(X, y, random_state = 0)
# Define model
melbourne_model = DecisionTreeRegressor()
# Fit model
melbourne_model.fit(train_X, train_y)

# get predicted prices on validation data
val_predictions = melbourne_model.predict(val_X)
print(mean_absolute_error(val_y, val_predictions))
```
#### 5. Underfitting and Overfitting
Overfiting is where a model matches the training data almost perfectly, but does poorly in validation and other new data. Overfitting: capturing spurious patterns that won't recur in the future, leading to less accurate predictions, or

Underfitting is when a model fails to capture important distictions and patterns in the data. Underfitting: failing to capture relevant patterns, again leading to less accurate predictions.
``` python
from sklearn.metrics import mean_absolute_error
from sklearn.tree import DecisionTreeRegressor

def get_mae(max_leaf_nodes, train_X, val_X, train_y, val_y):
    model = DecisionTreeRegressor(max_leaf_nodes=max_leaf_nodes, random_state=0)
    model.fit(train_X, train_y)
    preds_val = model.predict(val_X)
    mae = mean_absolute_error(val_y, preds_val)
    return(mae)
```


# Links
https://www.kaggle.com/learn/intro-to-machine-learning