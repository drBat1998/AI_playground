Title: koggle pandas
Author: [[koggle.com]]
Tags: #other 


# Notes
#### 1. Creating, Reading and Writing
```python
data = pd.read_csv("")


data.shape

data.head()

animals.to_csv("cows_and_goats.csv")
```
#### 2.Indexing, Selecting & Assigning
access the column
```python
data.column
data["column"]
```

loc and iloc
index-based selection
first row of the data
```python
data.iloc[0]
```
Both loc and iloc are row-first, column-second.
``` python
data.iloc[:,0] # all rows, first column

data.iloc[:3,0] # all rows to third exept third, first column

data.iloc[1:3, 0] # all rows from second to third exept third, first column

data.iloc[[0, 1, 2], 0] # list of values you need, first column

# Finally, it's worth knowing that negative numbers can be used in selection. This will start counting forwards from the end of the values. So for example here are the last five elements of the dataset.
data.iloc[-5:]
```
Label-based selection 
loc
```python
data.loc[0, "country"]
```

iloc vs loc
iloc select values exept the last 
loc selct all values
if you use iloc[0:1000] you would select 1000 values, while if you use loc[0:1000] you would select 1001.

Set index 
```python
reviews.set_index("title")
```

Conditional selection
```python
reviews.loc[reviews.country == 'Italy']

& #and

| # or
```
isin - to find specific values inside the data
```python
data.loc[data.country.isin(["Italy"])]
```

isnull and notnull
```python
reviews.loc[reviews.price.notnull()]

```
#### 3. Summary Functions and Maps
describe shows descriptive statistic
```python
reviews.points.describe()
```
To see a list of unique values we can use the unique() function:
```python
reviews.taster_name.unique()

```
To see a list of unique values and how often they occur in the dataset, we can use the value_counts() method:
```python
reviews.taster_name.value_counts()
```
Mapping
map()
apply()

```python
def remean_points(row):
    row.points = row.points - review_points_mean
    return row

reviews.apply(remean_points, axis='columns')
```
#### 4. Grouping and Sorting
groupby() created a group of reviews which allotted the same point values to the given wines.
```python
reviews.groupby('points').points.count()

```
You can think of each group we generate as being a slice of our DataFrame containing only data with values that match.
Another groupby() method worth mentioning is agg(), which lets you run a bunch of different functions on your DataFrame simultaneously. 
```python
reviews.groupby(['country']).price.agg([len, min, max])

```

Sorting
```python
countries_reviewed.sort_values(by='len')

countries_reviewed.sort_values(by='len', ascending=False)



```
#### 5. Data Types and Missing Values
dtype
```python
reviews.price.dtype
```
isnull
```python
reviews[pd.isnull(reviews.country)]
```
fillna
```python
reviews.region_2.fillna("Unknown")
```
replace
```python
reviews.taster_twitter_handle.replace("@kerinokeefe", "@kerino")
```

#### 6. Renaming and Combining
```python
reviews.rename(columns={'points': 'score'})
```

```python
pd.concat([canadian_youtube, british_youtube])

```

```python
left = canadian_youtube.set_index(['title', 'trending_date'])
right = british_youtube.set_index(['title', 'trending_date'])

left.join(right, lsuffix='_CAN', rsuffix='_UK')

```
# Links
https://www.kaggle.com/learn/pandas