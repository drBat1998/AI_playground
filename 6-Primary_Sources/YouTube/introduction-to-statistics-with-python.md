Title: introduction-to-statistics-with-python
Author: [[Swiss Institute of Bioinformatics]]
Tags: #python


# 01_data_manipulation_and_representation

basic information about a dataset
```python
numberRows, numberCols = df.shape
df.columns
# list the types
df.dtypes
```
accessing specific parts of the data
```python
df["column_name"] #or 
df.column_name
```
slice through `.loc`
```python
df.loc[0:3, :] #first 4 rows, all columns
df.loc[0:3, ["total","town name"]] #first 4 rows, columns total and town name
df.loc[ : , 'Total' ] ### all rows, column 'Total'
```
slice through 'masks'
```python
maskVD = df.canton == "VD" # or df["conton"]="VD"

```
cool way to apply the mask by .loc
```python
df.loc[ maskVD, ['town name','canton','canton name'] ]
```
combine two masks with logical and (&) or logical or (|)
```python
# towns in the canton of Zurich and with more than 10 000 registered inhabitants
mask = (df.canton == 'ZH') & ( df.Total >= 10000  ) 

df.loc[ mask , ]
```

create a new column in dataframe
```python
df["new_column"] = df.old_column + shit
```

to remove a column
```python
df.drop(columns = "name", inplace = True)

```

data description 
```python
df.describe()
```

``` python
sns.histplot(kde = True, color = "red').set_title("hist shit")

# Set up a figure with multiple panels, here a 2 by 2 grid
f, axes = plt.subplots( 2, 2, figsize=(7, 7) )			 

			 # Plot a simple histogram with binsize determined automatically
sns.histplot(dfFractions['0-14 y.o.'], kde=False, color="b", ax=axes[0, 0]).set_title('automatic')

# Plot a simple histogram with binsize 5, 10 , 1000
sns.histplot(dfFractions['0-14 y.o.'], bins=5   , kde=False, color="b", ax=axes[0, 1]).set_title('5 bins')
sns.histplot(dfFractions['0-14 y.o.'], bins=10  , kde=False, color="b", ax=axes[1, 0]).set_title('10 bins')
sns.histplot(dfFractions['0-14 y.o.'], bins=1000 , kde=False, color="b", ax=axes[1, 1]).set_title('1000 bins')
```
to create a line in histplot for marking mean mode or..
```python
import seaborn as sns
import matplotlib.pyplot as plt

# Here we just define a small function for plotting a distribution with the mean median and mode 
def plotWithMeanMedianMode( dat , ax):

    mode=dat.mode()[0] #we only select the first mode
    mean=dat.mean()
    median=dat.median()

    sns.histplot( dat , ax=ax , kde=True) # line for histogram and density line

    ax.axvline(mean, color='r', linestyle='--' , label='mean')
    ax.axvline(median, color='g', linestyle='-' , label = "median")
    ax.axvline(mode, color='b', linestyle='-' , label = "mode ")
    ax.legend()


f, axes = plt.subplots( 3, 1, figsize=(15, 10) )

plotWithMeanMedianMode( dfFractions['0-14 y.o.'] , ax=axes[0])
plotWithMeanMedianMode( dfFractions['Foreigner'] , ax=axes[1])
plotWithMeanMedianMode( dfFractions['Reformed'] , ax=axes[2])
plt.show()
```
categorical data

we could create a categorical variable column from existing columns
```python
dfFractions['majority religion'] = dfFractions.loc[ : , ['Reformed','Catholic', 'Other'] ].idxmax(axis=1)
```

Computing a summary statistics on a pandas DataFrame is done **using the `df.groupby(...)` method and the applying some function** to the result of that grouping.

```python
dfFractions.groupby('majority language')['Catholic'].mean() ## mean fraction of caholics in towns depending on the majority language
```

```python
def getSmallestTown( data ):
    ''' returns the name and population of the town with minimal number of inhabitants '''
    indexsmallestTown = data.Total.idxmin()
    return data['town name'][indexsmallestTown] , data.Total[indexsmallestTown]

grouped.apply(getSmallestTown) ## name and population of the town with minimal number of inhabitants for each canton
```

`catplot` is the best way to visualize any categorical variables
The `kind` argument let's you control the overall look of the plot. I
It can be:
* 'strip' : this is the default, showing all data points. 
* **'box'** : the famous boxplot
* **'violin'** : an alternative to the boxplot using density lines
* **'bar'** : the (in)famous barplot
* 'swarm' : similar to 'strip' but with another way of aranging the points
* 'boxen' : some intermediary between a boxplot and a violin plot
* 'point' : alternative to the barplot where only the top point is shown

Be aware to specify 
kind
orient 
height
aspect(aka weight)

```python
kinds = ['box','violin','bar','boxen','strip','point']#,'swarm'] # swarm takes a long time to compute


for i,k in enumerate(kinds):
    sns.catplot( x = 'Male' , y='majority religion' ,  data=dfFractions , kind = k ,height=2, aspect=5 )

# note 2 arguments here :
# * height : height of the plot
# * aspect : widht/height ratio. -> higher aspect = wider figure
```

>[!allart]
>Boxplot is a powerful tool for representing categorical values, however, boxplot have trouble with multimodal data representation.


violin-plots
[+] plot density line
[-] better work with large data
[-] gives strange results when the represented values are bounded

```python
sns.catplot( x = 'German speakers' , y='majority religion' , 
            data=dfFractions , kind = 'violin' ,height=2, aspect=5 , cut=0) # cut should solve 
```
barplots and their error bars
This representation is widely used, but it is, demonstrably, a less than optimal way of representing a distribution. 
At its code, it is a representation of two summary statistics:
* the **mean**, which is the size of the bar
* an **error value** which can be:
    * range : bars extend from smallest to largest value
    * standard deviation ($sigma$): square root of the variance
    * standard error of the mean (SEM): $sem = \frac{\sigma}{\sqrt{n}}$
    * 95% confidence interval (CI): $1.96 * \frac{\sigma}{\sqrt{n}}$

The standard deviation is a measure of the variability in the data, while the **standard error of the mean is a measure of the precision of the estimate of the mean**.

Barplots :
* Contain the same amount of information as a purely numeric summary (mean ± error)
* **Avoid it if possible**
* Always indicate what type of error bars you are using
* Many articles have been written on the subject of bar charts and possible alternatives, e.g. [a Nature Biomedical Engineering Editorial](https://www.nature.com/articles/s41551-017-0079), [Stret & Gehlenborg (2014)](https://www.nature.com/articles/nmeth.2807), [a Nature Methods Editorial](https://www.nature.com/articles/nmeth.2837), [Drummond & Vowler (2011)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3087125/) and [Weissgerber et al (2015)](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1002128)

```python
kinds = ['box','violin','bar','boxen','strip','point']#,'swarm'] # swarm takes a long time to compute

categorizations=["majority language","majority religion"]

## uncomment this to switch the categories
#categorizations = categorizations[::-1]

represented_variable="Total" 

for i,k in enumerate(kinds):
    g=sns.catplot( x = represented_variable , y= categorizations[0] , hue= categorizations[1] ,  
                data=dfFractions , kind = k , orient='h',height=2, aspect=5 )
    g.set(xscale="log")

```


to save your data-set to a file use

`df.to_csv("data/new_shit")`

and for figures

```python

plot_name.savefig("output.tiff")
```

```python
# For multipanel figures :
f, axes = plt.subplots( 2, 2, figsize=(7, 7) )

sns.histplot(dfFractions['0-14 y.o.'], kde=False, color="b", ax=axes[0, 0]).set_title('automatic')
sns.histplot(dfFractions['0-14 y.o.'], bins=5   , kde=False, color="b", ax=axes[0, 1]).set_title('5 bins')
sns.histplot(dfFractions['0-14 y.o.'], bins=10  , kde=False, color="b", ax=axes[1, 0]).set_title('10 bins')
sns.histplot(dfFractions['0-14 y.o.'], bins=1000 , kde=False, color="b", ax=axes[1, 1]).set_title('1000 bins')
plt.tight_layout()# this makes the panels margins and setup more graceful

f.savefig('output_multipanel.pdf')
```

Graphical representations are instrumental to both support the message we want to convey from our analysis and help us investigate our data. However, not all way of representing data are equal.

[Cleveland et al. 1984](https://info.sice.indiana.edu/~katy/S637-S11/cleveland84.pdf) tested, among others, the capacity of respondent to assess the ratio between different quantities shown of a graph.

They distinguish:
* **position judgment** : judging using an aligned axis
* **length judgment** : judging using a non aligned axis
* **angle judgment** : judging from angles only

*Position judgements are more accurate* than length judgements
* For position judgements, as the distance between the points along an axis perpendicular to the “common scale” increases, the accuracy decreases
* Position judgements are more accurate than angle judgements

[[Why barpots are nonsense or use two or more ways to represent your data]]
# 02_distribution_and_statistical_tests

A probability distribution is like a map that shows all the possible outcomes of something random (like flipping a coin or rolling a dice) and tells you how likely each outcome is.

Most distributions have a certain number of **parameters** that may control their overall **shape, location or scale**. For normal distribution they are mean and its standard deviation
```python
print("scaled difference between population and sample mean: {:.3f}".format(( population_mean - sample_mean )/population_mean ))
```
In this normal law:
 * the mean is equal to the **mean of the original distribution**  
 * the standard deviation that depends on the **standard deviation of the original deviation divided by the square root of $n$**. == standard error of the mean

[[standard error of the mean]] 

Using the notation we introduced earlier this looks like:

$$\bar{x} \sim N(m , \frac{s}{\sqrt{n}} )$$

, where $\bar{x}$ is the sample mean, and $m$ $s$ respectively are the mean and the standard deviation of the population.
However, note that **this only works if the sample size is large enough**. 
The central limit theorem let's us perform inferences even when the underlying distribution is unknown, howver it is still an approximation so **when it is known, we should prefer using the actual original distribution.**  




# Links
https://youtu.be/AiKeNJnfkZk?si=WfNs0vdUzhpS_nAk