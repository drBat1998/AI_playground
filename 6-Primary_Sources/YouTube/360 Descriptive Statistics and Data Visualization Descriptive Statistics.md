Title: 360 Descriptive Statistics and Data Visualization Descriptive Statistics
Author: [[DigitalSreeni]]
Tags: #python #statistics #youtube 


# Notes
Range = Max-Min
Variance = average squared deviation from the mean
SD = square root of variance

IQR( Interquartile range) is distance between first quartile and third quartile. 
Outliers if x < Q1 -1.5 * IQR or x > Q3 +1.5 * IQR

Coefficent of variation 
CV= sd/mean * 100 %
allows comparison between different variables.

Correlation analysis
from -1 to 1
1 perfect correlation 
`+` positive
`-` negatice
0 - no correlation

Normal distribution
	symetric, bell shaped curve
	mean = median = mode
	1 sd - 68% , 2 sd - 95%, and 3 sd - 99.7%
Non-normal 
- skewed 
	- positive - extend to the right
	- negative - extend to the left
	- zero - symmetric
- hevy-tailed or light tailed
	- positive - more outliers
	- negative - fewer outliers
- multimodal

Testing for normality
- Q-Q plots, or histograms
- Shapiro-Wilk test, Anderson-Darlinkg

Data transformation techniques
- log transformation - right skewed, multiplicative relationships
- square root - count data, moderate right skew
- box-cox - family of power transformation
- inverse - strong right skew

``` python
# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
```

``` python 
# This is the Wisconsin Breast Cancer Diagnostic dataset
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data"
column_names = ['ID', 'Diagnosis'] + [
    # Mean values
    'radius_mean', 'texture_mean', 'perimeter_mean', 'area_mean',
    'smoothness_mean', 'compactness_mean', 'concavity_mean', 'concave_points_mean',
    'symmetry_mean', 'fractal_dimension_mean',
    # Standard error values
    'radius_se', 'texture_se', 'perimeter_se', 'area_se',
    'smoothness_se', 'compactness_se', 'concavity_se', 'concave_points_se',
    'symmetry_se', 'fractal_dimension_se',
    # Worst values
    'radius_worst', 'texture_worst', 'perimeter_worst', 'area_worst',
    'smoothness_worst', 'compactness_worst', 'concavity_worst', 'concave_points_worst',
    'symmetry_worst', 'fractal_dimension_worst'
]
cancer_data = pd.read_csv(url, names=column_names, na_values='?')

# Display the first few rows of the dataset
print("First 5 rows of the dataset:")
print(cancer_data.head())

# Basic dataset information
print("\nDataset Information:")
cancer_data.info()

# Check for missing values
print("\nMissing values per column:")
print(cancer_data.isnull().sum())
```

``` python
# Select a few key numerical columns for demonstration
numerical_features = ["", ""]

def central_tendency_stats(data, column):
 """Calculate and display all measures of central tendency for a column."""
    values = data[column]
    
     # Calculate different measures
    mean_val = values.mean()
    median_val = values.median()
    mode_val = values.mode()[0]  # Mode can have multiple values, take the first one

 # Display results
    print(f"Statistics for {column}:")
    print(f"Mean: {mean_val:.4f}")
    print(f"Median: {median_val:.4f}")
    print(f"Mode: {mode_val:.4f}")
    
    # Visual representation of mean, median and mode
    plt.figure(figsize=(10, 6))
    sns.histplot(values, kde=True)
    plt.axvline(mean_val, color='r', linestyle='--', label=f'Mean: {mean_val:.2f}')
    plt.axvline(median_val, color='g', linestyle='-.', label=f'Median: {median_val:.2f}')
    plt.axvline(mode_val, color='b', linestyle=':', label=f'Mode: {mode_val:.2f}')
    plt.title(f'Distribution of {column} with Central Tendency Measures')
    plt.legend()
    plt.show()
    
     # Explanation
    print("\nInterpretation:")
    if abs(mean_val - median_val) < 0.01 * abs(mean_val):
        print("The mean and median are very close, suggesting a relatively symmetric distribution.")
    elif mean_val > median_val:
        print("The mean is greater than the median, suggesting a right-skewed (positively skewed) distribution.")
        print("This means there are some larger values pulling the mean upward.")
    else:
        print("The median is greater than the mean, suggesting a left-skewed (negatively skewed) distribution.")
        print("This means there are some smaller values pulling the mean downward.")

    if abs(mode_val - median_val) < 0.01 * abs(median_val):
        print("The mode is close to the median, which is typical in many distributions.")
    print("\n")
```
loop 
``` python
# Apply the function to each selected column
for feature in numerical_features:
    central_tendency_stats(cancer_data, feature)
```

```

Open In Colab
https://youtu.be/HGXp30b3Uj8

Descriptive Statistics and Data Visualization
Part 2 of the Statistical Analysis in Python Tutorial Series


# Import necessary libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
     

# Set visualization style consistent with your first tutorial
sns.set(style="whitegrid")
plt.rcParams['figure.figsize'] = (12, 8)
plt.rcParams['font.size'] = 12
     

# Load the UCI Breast Cancer Wisconsin dataset
# This is the Wisconsin Breast Cancer Diagnostic dataset
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data"
column_names = ['ID', 'Diagnosis'] + [
    # Mean values
    'radius_mean', 'texture_mean', 'perimeter_mean', 'area_mean',
    'smoothness_mean', 'compactness_mean', 'concavity_mean', 'concave_points_mean',
    'symmetry_mean', 'fractal_dimension_mean',
    # Standard error values
    'radius_se', 'texture_se', 'perimeter_se', 'area_se',
    'smoothness_se', 'compactness_se', 'concavity_se', 'concave_points_se',
    'symmetry_se', 'fractal_dimension_se',
    # Worst values
    'radius_worst', 'texture_worst', 'perimeter_worst', 'area_worst',
    'smoothness_worst', 'compactness_worst', 'concavity_worst', 'concave_points_worst',
    'symmetry_worst', 'fractal_dimension_worst'
]
cancer_data = pd.read_csv(url, names=column_names, na_values='?')

# Display the first few rows of the dataset
print("First 5 rows of the dataset:")
print(cancer_data.head())

# Basic dataset information
print("\nDataset Information:")
cancer_data.info()
     

# Check for missing values
print("\nMissing values per column:")
print(cancer_data.isnull().sum())
     
Measures of Central Tendency

# Select a few key numerical columns for demonstration
numerical_features = ['radius_mean', 'texture_mean', 'perimeter_mean', 'area_mean', 'smoothness_mean']

# function to display all measures of central tendency for a column
def central_tendency_stats(data, column):
    """Calculate and display all measures of central tendency for a column."""
    values = data[column]

    # Calculate different measures
    mean_val = values.mean()
    median_val = values.median()
    mode_val = values.mode()[0]  # Mode can have multiple values, take the first one

    # Weighted mean example (using radius_mean as weights for demonstration)
    # Compute weighted average of each column values.
    # For all columns except, radius_mean, use values from radius_mean as weights. FOr radius_mean, use area_mean as weights (to avoid self-weighting)
    if column != 'radius_mean':
        weights = data['radius_mean']
        weighted_mean = np.average(values, weights=weights)
    else:
        weighted_mean = np.average(values, weights=data['area_mean'])

    # Display results
    print(f"Statistics for {column}:")
    print(f"Mean: {mean_val:.4f}")
    print(f"Median: {median_val:.4f}")
    print(f"Mode: {mode_val:.4f}")
    print(f"Weighted Mean: {weighted_mean:.4f}")

    # Visual representation of mean, median and mode
    plt.figure(figsize=(10, 6))
    sns.histplot(values, kde=True)
    plt.axvline(mean_val, color='r', linestyle='--', label=f'Mean: {mean_val:.2f}')
    plt.axvline(median_val, color='g', linestyle='-.', label=f'Median: {median_val:.2f}')
    plt.axvline(mode_val, color='b', linestyle=':', label=f'Mode: {mode_val:.2f}')
    plt.title(f'Distribution of {column} with Central Tendency Measures')
    plt.legend()
    plt.show()

    # Explanation
    print("\nInterpretation:")
    if abs(mean_val - median_val) < 0.01 * abs(mean_val):
        print("The mean and median are very close, suggesting a relatively symmetric distribution.")
    elif mean_val > median_val:
        print("The mean is greater than the median, suggesting a right-skewed (positively skewed) distribution.")
        print("This means there are some larger values pulling the mean upward.")
    else:
        print("The median is greater than the mean, suggesting a left-skewed (negatively skewed) distribution.")
        print("This means there are some smaller values pulling the mean downward.")

    if abs(mode_val - median_val) < 0.01 * abs(median_val):
        print("The mode is close to the median, which is typical in many distributions.")
    print("\n")

# Apply the function to each selected column
for feature in numerical_features:
    central_tendency_stats(cancer_data, feature)
     

# Create a comparison plot of means for malignant vs benign tumors
def compare_means_by_diagnosis(data, features):
    """Compare means of features between malignant and benign tumors."""
    # Convert diagnosis to binary (M = Malignant, B = Benign)
    data['Diagnosis_Binary'] = data['Diagnosis'].map({'M': 'Malignant', 'B': 'Benign'})

    # Calculate means by diagnosis
    grouped_means = data.groupby('Diagnosis_Binary')[features].mean()

    # Plot
    plt.figure(figsize=(12, 6))
    grouped_means.T.plot(kind='bar', rot=45)
    plt.title('Comparison of Feature Means by Diagnosis')
    plt.ylabel('Mean Value')
    plt.xlabel('Features')
    plt.xticks(rotation=45, ha='right')
    plt.tight_layout()
    plt.legend(title='Diagnosis')
    plt.show()

    # Return the grouped means for further analysis
    return grouped_means

# Compare means for selected features
group_means = compare_means_by_diagnosis(cancer_data, numerical_features)
print("Mean values by diagnosis group:")
print(group_means)
print("\nObservation: Note the differences in mean values between benign and malignant tumors.")
print("These differences might be statistically significant and useful for classification.")
     
Measures of Dispersion

# Create a function to display all measures of dispersion for a column
def dispersion_stats(data, column):
    """Calculate and display all measures of dispersion for a column."""
    values = data[column]

    # Calculate different measures
    range_val = values.max() - values.min()
    variance = values.var()
    std_dev = values.std()

    # Calculate quartiles and IQR
    q1 = values.quantile(0.25)
    q3 = values.quantile(0.75)
    iqr = q3 - q1

    # Calculate coefficient of variation (CV)
    cv = (std_dev / values.mean()) * 100

    # Display results
    print(f"Dispersion Statistics for {column}:")
    print(f"Range: {range_val:.4f}")
    print(f"Variance: {variance:.4f}")
    print(f"Standard Deviation: {std_dev:.4f}")
    print(f"Interquartile Range (IQR): {iqr:.4f}")
    print(f"Coefficient of Variation: {cv:.2f}%")

    # Visual representation of dispersion
    plt.figure(figsize=(14, 6))

    # Create two subplots
    plt.subplot(1, 2, 1)
    sns.boxplot(y=values)
    plt.title(f'Boxplot of {column}')
    plt.ylabel('Value')

    plt.subplot(1, 2, 2)
    sns.histplot(values, kde=True)
    plt.axvline(values.mean(), color='r', linestyle='--',
                label=f'Mean: {values.mean():.2f}')
    plt.axvline(values.mean() + std_dev, color='g', linestyle='-.',
               label=f'Mean + SD: {values.mean() + std_dev:.2f}')
    plt.axvline(values.mean() - std_dev, color='g', linestyle='-.',
               label=f'Mean - SD: {values.mean() - std_dev:.2f}')
    plt.title(f'Distribution of {column} with Standard Deviation')
    plt.legend()

    plt.tight_layout()
    plt.show()

    # Explanation
    print("\nInterpretation:")
    print(f"Range: The difference between the maximum and minimum values is {range_val:.4f}.")
    print(f"Standard Deviation: On average, values deviate from the mean by approximately {std_dev:.4f}.")
    print(f"IQR: The middle 50% of the data falls within a range of {iqr:.4f}.")

    # Interpretation of Coefficient of Variation
    if cv < 10:
        print("Coefficient of Variation: The data shows low variability relative to the mean.")
    elif cv < 30:
        print("Coefficient of Variation: The data shows moderate variability relative to the mean.")
    else:
        print("Coefficient of Variation: The data shows high variability relative to the mean.")
    print("\n")

# Apply the function to each selected column
for feature in numerical_features:
    dispersion_stats(cancer_data, feature)
     

# Compare dispersion by diagnosis
def compare_dispersion_by_diagnosis(data, features):
    """Compare dispersion measures between malignant and benign tumors."""
    # Convert diagnosis to binary
    data['Diagnosis_Binary'] = data['Diagnosis'].map({'M': 'Malignant', 'B': 'Benign'})

    # Calculate standard deviations by diagnosis
    grouped_std = data.groupby('Diagnosis_Binary')[features].std()

    # Calculate coefficient of variation
    grouped_mean = data.groupby('Diagnosis_Binary')[features].mean()
    grouped_cv = (grouped_std / grouped_mean) * 100

    # Plot standard deviations
    # Plot standard deviations and CV on separate subplots
    fig, axes = plt.subplots(nrows=2, ncols=1, figsize=(12, 10))

    grouped_std.T.plot(kind='bar', rot=45, ax=axes[0])
    axes[0].set_title('Comparison of Standard Deviations by Diagnosis')
    axes[0].set_ylabel('Standard Deviation')
    axes[0].tick_params(axis='x', rotation=45)
    axes[0].legend(title='Diagnosis')

    grouped_cv.T.plot(kind='bar', rot=45, ax=axes[1])
    axes[1].set_title('Comparison of Coefficient of Variation by Diagnosis')
    axes[1].set_ylabel('CV (%)')
    axes[1].set_xlabel('Features')
    axes[1].tick_params(axis='x', rotation=45)
    axes[1].legend(title='Diagnosis')

    plt.tight_layout()
    plt.show()

    # Return the grouped stats for further analysis
    return grouped_std, grouped_cv

# Compare dispersion for selected features
group_std, group_cv = compare_dispersion_by_diagnosis(cancer_data, numerical_features)
print("Standard deviation values by diagnosis group:")
print(group_std)
print("\nCoefficient of Variation values by diagnosis group:")
print(group_cv)
print("\nObservation: Notice how variability differs between benign and malignant tumors.")
print("Higher variability in one group might indicate less predictable or more diverse cellular characteristics.")

     
Advanced Data Visualization

# Convert diagnosis to numeric for correlation analysis
cancer_data['Diagnosis_Numeric'] = cancer_data['Diagnosis'].map({'M': 1, 'B': 0})

# Select features for visualization
visualization_features = ['radius_mean', 'texture_mean', 'perimeter_mean', 'area_mean', 'smoothness_mean', 'Diagnosis_Numeric']

# Create a correlation matrix
correlation_matrix = cancer_data[visualization_features].corr()

# Create a heatmap of correlations
plt.figure(figsize=(10, 8))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt=".2f",
            xticklabels=visualization_features,
            yticklabels=visualization_features)
plt.title('Correlation Matrix of Selected Features')
plt.tight_layout()
plt.show()

print("Explanation of Correlation Matrix:")
print("The correlation matrix shows the relationship strength between variables.")
print("Values range from -1 to 1:")
print("  1: Perfect positive correlation (one increases, the other increases)")
print("  0: No linear correlation (no clear linear relationship)")
print(" -1: Perfect negative correlation (one increases, the other decreases)")
print("\nNotice which features correlate most strongly with diagnosis.")
     

# Create a pairplot to visualize relationships between features
plt.figure(figsize=(16, 12))
sns.pairplot(cancer_data[visualization_features],
             hue='Diagnosis_Numeric',
             palette={0: 'green', 1: 'red'},
             hue_order=[0, 1])
plt.suptitle('Pairplot of Selected Features by Diagnosis', y=1.02, fontsize=16)
plt.show()

print("Explanation of Pairplot:")
print("The pairplot shows relationships between pairs of variables and their distributions.")
print("Diagonal plots show the distribution of each variable.")
print("Off-diagonal plots show the relationship between two variables.")
print("Points are colored by diagnosis (green for benign, red for malignant).")
print("This helps identify potential patterns or clusters that differentiate between diagnoses.")
     

# Advanced visualization: Box plots with swarm plots
plt.figure(figsize=(15, 10))
for i, feature in enumerate(numerical_features, 1):
    plt.subplot(2, 3, i)
    # Combine boxplot and swarmplot for a richer visualization
    sns.boxplot(x='Diagnosis', y=feature, data=cancer_data, palette={'M': 'red', 'B': 'blue'})
    sns.swarmplot(x='Diagnosis', y=feature, data=cancer_data, color='black', alpha=0.5, size=3)
    plt.title(f'Distribution of {feature} by Diagnosis')
    plt.xlabel('Diagnosis (M=Malignant, B=Benign)')
    plt.ylabel(feature)

plt.tight_layout()
plt.suptitle('Box Plots with Data Points for Selected Features', y=1.02, fontsize=16)
plt.show()

print("Explanation of Box Plots with Swarm Plots:")
print("Box plots show the median (middle line), quartiles (box), and range (whiskers) of each group.")
print("The overlaid points show the actual distribution of individual observations.")
print("This combination helps visualize both the summary statistics and the full data distribution.")
print("We can observe differences in both central tendency and dispersion between benign and malignant tumors.")
     

# Violin plots for comparing distributions
plt.figure(figsize=(15, 10))
for i, feature in enumerate(numerical_features, 1):
    plt.subplot(2, 3, i)
    sns.violinplot(x='Diagnosis', y=feature, data=cancer_data, palette={'M': 'red', 'B': 'blue'}, inner='quartile')
    plt.title(f'Violin Plot of {feature} by Diagnosis')
    plt.xlabel('Diagnosis (M=Malignant, B=Benign)')
    plt.ylabel(feature)

plt.tight_layout()
plt.suptitle('Violin Plots for Selected Features', y=1.02, fontsize=16)
plt.show()

print("Explanation of Violin Plots:")
print("Violin plots combine box plots with density plots to show the distribution shape.")
print("Wider sections represent more frequent values, while narrower sections are less common.")
print("The white dot represents the median, the black box shows the interquartile range.")
print("These plots are excellent for comparing distributions between groups.")
print("Note the different shapes, which reveal how values are distributed for each diagnosis group.")
     
Statistical Summary by Groups

# Group by diagnosis and calculate descriptive statistics
grouped_stats = cancer_data.groupby('Diagnosis')[numerical_features].describe()

print("Comprehensive Statistical Summary by Diagnosis:")
print(grouped_stats)
     
Create a simplified and more readable summary


summary_dict = {}

for feature in numerical_features:
    # Calculate stats for benign
    benign_stats = cancer_data[cancer_data['Diagnosis'] == 'B'][feature].agg(['mean', 'median', 'std', 'min', 'max']).to_dict()
    # Calculate stats for malignant
    malignant_stats = cancer_data[cancer_data['Diagnosis'] == 'M'][feature].agg(['mean', 'median', 'std', 'min', 'max']).to_dict()

    # Add prefixes to distinguish the groups
    benign_renamed = {f'Benign_{k}': v for k, v in benign_stats.items()}
    malignant_renamed = {f'Malignant_{k}': v for k, v in malignant_stats.items()}

    # Combine the stats
    summary_dict[feature] = {**benign_renamed, **malignant_renamed}

# Convert to dataframe
simple_stats = pd.DataFrame(summary_dict).T

print("\nSimplified Statistical Summary (Features as Columns):")
print(simple_stats)

print("\nKey Observations from Group Comparisons:")
for feature in numerical_features:
    b_mean = cancer_data[cancer_data['Diagnosis'] == 'B'][feature].mean()
    m_mean = cancer_data[cancer_data['Diagnosis'] == 'M'][feature].mean()

    percent_diff = abs((m_mean - b_mean) / b_mean) * 100

    if m_mean > b_mean:
        comparison = "higher"
    else:
        comparison = "lower"

    print(f"For {feature}, malignant tumors have {comparison} values (by {percent_diff:.1f}%) than benign tumors.")

     
Non-Normal Data and Outliers

# Function to check for normality visually and with Shapiro-Wilk test
def check_normality(data, column):
    """Check if data follows a normal distribution using QQ-plot and Shapiro-Wilk test."""
    values = data[column]

    # Create a figure with QQ-plot
    plt.figure(figsize=(12, 5))

    plt.subplot(1, 2, 1)
    stats.probplot(values, dist="norm", plot=plt)
    plt.title(f'Q-Q Plot for {column}')

    plt.subplot(1, 2, 2)
    sns.histplot(values, kde=True)
    plt.title(f'Distribution of {column}')

    plt.tight_layout()
    plt.show()

    # Perform Shapiro-Wilk test for normality
    statistic, p_value = stats.shapiro(values)

    print(f"Normality check for {column}:")
    print(f"Shapiro-Wilk test: statistic = {statistic:.4f}, p-value = {p_value:.8f}")

    if p_value < 0.05:
        print("The data significantly deviates from a normal distribution (p < 0.05).")
    else:
        print("The data appears to follow a normal distribution (p >= 0.05).")

    # Calculate skewness and kurtosis
    skewness = stats.skew(values)
    kurtosis = stats.kurtosis(values)

    print(f"Skewness: {skewness:.4f}")
    if abs(skewness) < 0.5:
        print("  The distribution is approximately symmetric.")
    elif skewness > 0.5:
        print("  The distribution is right-skewed (positively skewed).")
    else:  # skewness < -0.5
        print("  The distribution is left-skewed (negatively skewed).")

    print(f"Kurtosis: {kurtosis:.4f}")
    if abs(kurtosis) < 0.5:
        print("  The distribution has a similar tail weight as the normal distribution.")
    elif kurtosis > 0.5:
        print("  The distribution is leptokurtic (heavier tails, more outliers than normal).")
    else:  # kurtosis < -0.5
        print("  The distribution is platykurtic (lighter tails, fewer outliers than normal).")
    print("\n")

# Check normality for the first 3 features
for feature in numerical_features[:3]:
    check_normality(cancer_data, feature)

     


# Outlier detection and visualization
def detect_outliers(data, column):
    """Detect and visualize outliers using the IQR method."""
    values = data[column]

    # Calculate Q1, Q3, and IQR
    q1 = values.quantile(0.25)
    q3 = values.quantile(0.75)
    iqr = q3 - q1

    # Define outlier boundaries
    lower_bound = q1 - 1.5 * iqr
    upper_bound = q3 + 1.5 * iqr

    # Find outliers
    outliers = values[(values < lower_bound) | (values > upper_bound)]

    print(f"Outlier detection for {column}:")
    print(f"Number of outliers: {len(outliers)}")
    print(f"Percentage of outliers: {(len(outliers) / len(values)) * 100:.2f}%")
    print(f"Outlier boundaries: Lower = {lower_bound:.4f}, Upper = {upper_bound:.4f}")

    if len(outliers) > 0:
        print("Outlier values:")
        print(outliers.values)

    # Visualize with box plot
    plt.figure(figsize=(12, 6))

    plt.subplot(1, 2, 1)
    sns.boxplot(y=values)
    plt.title(f'Box Plot of {column} Showing Outliers')
    plt.ylabel('Value')

    plt.subplot(1, 2, 2)
    sns.histplot(values, kde=True)
    plt.axvline(lower_bound, color='r', linestyle='--', label=f'Lower bound: {lower_bound:.2f}')
    plt.axvline(upper_bound, color='r', linestyle='--', label=f'Upper bound: {upper_bound:.2f}')
    plt.title(f'Distribution of {column} with Outlier Boundaries')
    plt.legend()

    plt.tight_layout()
    plt.show()

    # Return the outliers
    return outliers

# Detect outliers for each feature
for feature in numerical_features:
    outliers = detect_outliers(cancer_data, feature)


     
Next tutorial preview:
Understanding Data Distributions:

We'll dive deeper into normal vs. non-normal distributions techniques for testing normality, and data transformation methods using the Wine Quality dataset.
```
# Links
previous: [[359 Introduction to Statistical Analysis in Python]]
https://youtu.be/HGXp30b3Uj8?si=gfvX_G1RzKQfXu4o