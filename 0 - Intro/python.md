

## Data analysis
## Pandas
```python
import pandas as pd
```
## Import data
read csv
```python
pd.read_csv("file.csv")
```
read exel
```python
pd.read_excel("file.xls", sheet_name = "Sheet1")
```
read sql
```python
from sqlalchemy import create_engine
engine = create_engine("sqlite:///:memory:")

pd.read_sql("SELECT * FROM my_table", engine)

pd.read_sql_query("SELECT * FROM my_table", engine)

df.to_sql("myDf", engine)
```

## Selection
``` python
df["b"]
df[1:]
```
by position
```python
df.iloc[[0],[0]]
```
by label
```python
df.loc[[0],["COuntry"]]
```

boolean indexing
```python
s[(s < -1) | (s > 2)]
df[df["Population"]>12000]
```

## Basic information
```python
df.shape
df.index
df.columns
df.info()
df.count()
```
summary
```python
df.sum()
df.min()
df.max()
df.describe()
df.mean()
df.median()
```


## Function and applying function
```python
f = lambda x: x*2

df.apply(f)
df.applymap(f)
```