Title: Data cleaning with Pandas
Author: [[Thinkerstellar]]
Tags: #programming #other 

[[pandas]]
# 1. Data Cleaning Basics lab
```python
import pandas as pd
df = pd.read_csv("file.csv")
df.shape
```

split the colum
```python
df["city"] = df["adress"].str.split(",", expand = True)[0]

df["state"] = df["adress"].str.split(",", expand = True)[1]
```

merging columns
```python
df["name"] = df["first_name"]+ " " +df["second_name"]
```

removing columns or rows
```python
df.drop("adress", axis = 1, inplace = True)
# if you want rows axis = 0
```

converting types
```python
df.dtypes # to check the type

df["salary"] = df["salary"].astype("float")
```

replacing values
```python
df["profession"] = df["profession"].replace({"engine":"eng", "doctor":"doc"})
```