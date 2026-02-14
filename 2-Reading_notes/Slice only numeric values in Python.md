Title: Slice only numeric values in Python
Tags: #reading_note #python 


# Notes
```python
numerical_cols = heart_data.select_dtypes(include=['float64', 'int64']).columns
correlation_matrix = heart_data[numerical_cols].corr()
```

# Summary

# Links
[[359 Introduction to Statistical Analysis in Python]]