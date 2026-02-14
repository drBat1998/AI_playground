[[pandas]]
## Joining and splitting columns
```python
# Concatenate several columns into a single string column with .str.cat()
df["colum"].astype(str)\
.str.cat(df[["col1","col2"]].astype(str), sep = "-")
```

```python
# Split a column on a delimiter into several columns with .str.split(expand=True)
df[""].str.split(',', expand = True)
```

```python
# Combine several columns into a list column with .values.tolist()
movies[""] = movies[["","",""]]\
.values.tolist()
# Split a list column into separate columns with .to_list()

movies[[ "", "", ""]] = \
 movies[""].to_list()
```
## Melting and pivoting
