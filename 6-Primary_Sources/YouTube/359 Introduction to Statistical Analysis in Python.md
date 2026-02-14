Title: 359 Introduction to Statistical Analysis in Python
Author: [[DigitalSreeni]]
Tags: #statistics #youtube 


# Notes
Parametric tests:
- Assume the data is normally distributed 
- more powerful when assumptions are met
- t-test, ANOVA

Non-parametric tests:
- make fewer assumptions about the data distribution
- Often use ranks rather than actual values
- Kruskal-Wallis, Spearman

You have to choose the right statistical test and, more importantly right question

Two population
    Parametric
		Independent t-test
		Paired t-test
		F-test
    Non-parametric
		Wilcoxon signed-rank test
		Kolmogorov-Smirnov test
Three or more
	Parametric
		One-way ANOVA
		Repeated measures ANOVA
		Factorial ANOVA
	Non-parametric
		Kruskal-Wallis test
		Fiedman test

Core libraries
- NumPy
- SciPy
- pandas
- statsmodels
- scikit-learn
- matplotlib/seaborn

For descriptive statistics, the best way to start in Python is:
```python
dataset.describe()
heart_data.info()
heart_data.isnull().sum()
```
The describe() function provides a quick statistical summary of your data:
- count: Number of non-missing values for each variable
- mean: The average value (sum of all values divided by count)
- std: Standard deviation, which measures how spread out the values are from the mean
- min: The minimum (smallest) value in the dataset
- 25%: The first quartile (Q1) - 25% of values fall below this number
- 50%: The median or second quartile (Q2) - the middle value when ordered
- 75%: The third quartile (Q3) - 75% of values fall below this number
- max: The maximum (largest) value in the dataset

Visualizing distribution

Find the missing values through .isnull()
And then fill if with .fillna()

```python
# Display the first few rows of the dataset
heart_data.head()

# Basic dataset information
heart_data.info()

# Check for missing values
print("\nMissing values per column:")
print(heart_data.isnull().sum())
```
```python

# Convert target variable to binary (0 = no disease, 1 = disease)
heart_data['target'] = heart_data['target'].apply(lambda x: 0 if x == 0 else 1)

# Convert sex to categorical for better interpretability
heart_data['sex'] = heart_data['sex'].map({0: 'Female', 1: 'Male'})

# Create a simple histogram of age
plt.figure(figsize=(10, 6))
sns.histplot(heart_data['age'], kde=True)
plt.title('Distribution of Age in Heart Disease Dataset')
plt.xlabel('Age (years)')
plt.ylabel('Frequency')
plt.axvline(heart_data['age'].mean(), color='r', linestyle='--',
            label=f'Mean: {heart_data["age"].mean():.2f}')
plt.axvline(heart_data['age'].median(), color='g', linestyle='-.',
            label=f'Median: {heart_data["age"].median():.2f}')
plt.legend()
plt.show()
```
```python
numerical_cols = heart_data.select_dtypes(include=['float64', 'int64']).columns
correlation_matrix = heart_data[numerical_cols].corr()
```
[[Slice only numeric values in Python]]
# Links
next:  [[360 Descriptive Statistics and Data Visualization Descriptive Statistics]]

https://youtu.be/ZEocIzTVyhU?si=UQQJK6wVygAfttdv
