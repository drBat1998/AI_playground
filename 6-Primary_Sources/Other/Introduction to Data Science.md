Title: Introduction to Data Science
Author: [[]]
Tags: #other #programming #bioinfo 


### Ch. 2 R basics
objects
``` R
a <- 1
# or
a = 1
```
data 
```r
data()
```

Data types
- str
- numeric
- character 
- logical
- df
- factor
	- levels(df$column)
- list
- matrix
- vectors
	- names, similar to a dictionary in some way
		- codes <- c(italy = 380, canada = 124, egypt = 818)
```r
codes <- c(380, 124, 818)
country <- c("italy","canada","egypt")
names(codes) <- country

```
sequence
seq(1, 10, 0.5)

Subsetting
	codes[c(1,3)]
	codes[1:2]
	codes["canada"]
	codes[c("egypt","italy")]

Sorting
```r
library(dslabs)
data(murders)
sort(murders$total)
order(x)
max(murders$total)
which.max(murders$total)
rank(x)
```

 Vector arithmetics
``` r
inches <- c(69, 62, 66, 70, 70, 73, 67, 73, 67, 70)
inches * 2.54
#>  [1] 175 157 168 178 178 185 170 185 170 178

inches - 69
#>  [1]  0 -7 -3  1  1  4 -2  4 -2  1

murder_rate <- murders$total / murders$population * 100000

```
Subsetting with logicals
``` r
ind <- murder_rate < 0.71

ind <- murder_rate <= 0.71

murders$state[ind]
#> [1] "Hawaii"        "Iowa"          "New Hampshire" "North Dakota" 
#> [5] "Vermont"
```

Logical operators
``` r
TRUE & TRUE
#> [1] TRUE
TRUE & FALSE
#> [1] FALSE
FALSE & FALSE
#> [1] FALSE


```
which
Suppose we want to look up California’s murder rate. For this type of operation, it is convenient to convert vectors of logicals into indexes instead of keeping long vectors of logicals. The function which tells us which entries of a logical vector are TRUE. So we can type:
``` r
ind <- which(murders$state == "California")
murder_rate[ind]
#> [1] 3.37
```
match
If instead of just one state we want to find out the murder rates for several states, say New York, Florida, and Texas, we can use the function match. This function tells us which indexes of a second vector match each of the entries of a first vector:
``` r
ind <- match(c("New York", "Florida", "Texas"), murders$state)
ind
#> [1] 33 10 44
```
%in%
If rather than an index we want a logical that tells us whether or not each element of a first vector is in a second, we can use the function %in%. Let’s imagine you are not sure if Boston, Dakota, and Washington are states. You can find out like this:
``` r
c("Boston", "Dakota", "Washington") %in% murders$state
#> [1] FALSE FALSE  TRUE
```

Basic plots
``` r
hist(x)

murders$rate <- with(murders, total / population * 100000)
boxplot(rate~region, data = murders)

image(x)
```

### Chapter 3 Programming basics
if-else
``` r
a <- 0

if(a!=0){
print(1/a)
} else {
print("No reciprocal for 0")
}
#> [1] "No reciprocal for 0."
```

``` r
library(dslabs)
data(murders)
murder_rate <- murders$total / murders$population*100000

ind <- which.min(murder_rate)

if(murder_rate[ind] < 0.5){
  print(murders$state[ind]) 
} else{
  print("No state has murder rate that low")
}
#> [1] "Vermont"

if(murder_rate[ind] < 0.25){
  print(murders$state[ind]) 
} else{
  print("No state has a murder rate that low.")
}
#> [1] "No state has a murder rate that low."

a <- 0
ifelse(a > 0, 1/a, NA)
#> [1] NA
```

Defining functions
``` r
avg <- function(x){
  s <- sum(x)
  n <- length(x)
  s/n
}
```

For-loops
``` r
for(i in 1:5){
  print(i)
}
#> [1] 1
#> [1] 2
#> [1] 3
#> [1] 4
#> [1] 5
```

``` r
m <- 25
s_n <- vector(length = m) # create an empty vector
for(n in 1:m){
  s_n[n] <- compute_s_n(n)
}
```
### Chapter 4 The tidyverse
dplyr

mutate to create or edit columns
``` r
murders |>
	mutate(rate = total/population *10000)
```

subsetting with filter
``` r 
murders |> 
	filter(rate <= 0.71)
	
## != for removing the row 
no_florida <- filter(murders, state != "Florida")
## %in% to select a specific list of rows
filter(murders, state %in% c("New York", "Texas"))
```

select columns with select
``` r
murders |> 
	select(murders, state, region, rate)
```

original data → select → filter 
 ``` r
 murders |> select(state, region, rate) |> filter(rate <= 0.71)
#>           state        region  rate
#> 1        Hawaii          West 0.515
#> 2          Iowa North Central 0.689
#> 3 New Hampshire     Northeast 0.380
#> 4  North Dakota North Central 0.595
#> 5       Vermont     Northeast 0.320
 ```

summarize

``` r
s <- heights |> 
  filter(sex == "Female") |>
  summarize(average = mean(height), standard_deviation = sd(height))
s
#>   average standard_deviation
#> 1    64.9               3.76
```
``` r
median_min_max <- function(x){
  qs <- quantile(x, c(0.5, 0, 1))
  data.frame(median = qs[1], minimum = qs[2], maximum = qs[3])
}
heights |> 
  filter(sex == "Female") |>
  summarize(median_min_max(height))
#>   median minimum maximum
#> 1     65      51      79
```

Group then summarize with group_by
``` r
heights |> 
  group_by(sex) |>
  summarize(average = mean(height), standard_deviation = sd(height))
#> # A tibble: 2 × 3
#>   sex    average standard_deviation
#>   <fct>    <dbl>              <dbl>
#> 1 Female    64.9               3.76
#> 2 Male      69.3               3.61
```
 Here we show a useful trick for accessing values stored in data when using pipes: when a data object is piped that object and its columns can be accessed using the pull function. To understand what we mean take a look at this line of code:
``` r
us_murder_rate |> pull(rate)
#> [1] 3.03
```

Sorting data frames
``` r
murders |>
  arrange(population) |>
  head()
```

The `case_when` function is useful for vectorizing conditional statements. It is similar to ifelse but can output any number of values, as opposed to just TRUE or FALSE. Here is an example splitting numbers into negative, positive, and 0:
``` r
x <- c(-2, -1, 0, 1, 2)
case_when(x < 0 ~ "Negative", 
          x > 0 ~ "Positive", 
          TRUE  ~ "Zero")
#> [1] "Negative" "Negative" "Zero"     "Positive" "Positive"
```

``` r
murders |> 
  mutate(group = case_when(
    abb %in% c("ME", "NH", "VT", "MA", "RI", "CT") ~ "New England",
    abb %in% c("WA", "OR", "CA") ~ "West Coast",
    region == "South" ~ "South",
    TRUE ~ "Other")) |>
  group_by(group) |>
  summarize(rate = sum(total) / sum(population) * 10^5) 
#> # A tibble: 4 × 2
#>   group        rate
#>   <chr>       <dbl>
#> 1 New England  1.72
#> 2 Other        2.71
#> 3 South        3.63
#> 4 West Coast   2.90
```

### Chapter 5 Importing data
Paths and the working directory
``` r
filename <- "murders.csv"
dir <- system.file("extdata", package = "dslabs") 
fullpath <- file.path(dir, filename)
file.copy(fullpath, "murders.csv")
```
The working directory
We highly recommend only writing relative paths in your code. The reason is that full paths are unique to your computer and you want your code to be portable. You can get the full path of your working directory without writing out explicitly by using the getwd function.

``` r
wd <- getwd()
```
If you need to change your working directory, you can use the function setwd or you can change it through RStudio by clicking on “Session”.



readr
- read_table txt
- read_csv csv
- read_csv2 csv
- read_tsv tsv
- read_delim txt

readxl
- read_excel xls, xlsx


Downloading files
``` r
url <- "https://raw.githubusercontent.com/rafalab/dslabs/master/inst/
extdata/murders.csv"

dat <- read_csv(url)

```
## Chapter 6 data.table
## Chapter 7 Introduction to data visualization

## Chapter 8 ggplot2
In ``ggplot2`` we create graphs by adding layers. Layers can define geometries, compute summary statistics, define what scales to use, or even change styles. To add layers, we use the symbol +. In general, a line of code will look like this:

``` r
murders |> ggplot() + 
  geom_point(aes(x = population/10^6, y = total))
```

Global versus local aesthetic mappings

Scales
First, our desired scales are in log-scale. This is not the default, so this change needs to be added through a scales layer. A quick look at the cheat sheet reveals the scale_x_continuous function lets us control the behavior of scales. We use them like this:
``` r
p + geom_point(size = 3) +  
  geom_text(nudge_x = 0.05) + 
  scale_x_continuous(trans = "log10") +
  scale_y_continuous(trans = "log10") 

```

 Labels and titles
 ``` r
 +
  xlab("Populations in millions (log scale)") + 
  ylab("Total number of murders (log scale)") +
  ggtitle("US Gun Murders in 2010")
 ```
Categories as colors
``` r
p + geom_point(aes(col=region), size = 3)

```

## Chapter 9 Visualizing data distributions
## Chapter 10 Data visualization in practice
aes(color)
``` r
filter(gapminder, year == 1962) |>
  ggplot(aes(fertility, life_expectancy, color = continent)) +
  geom_point()
```
facet_grid
``` r
filter(gapminder, year%in%c(1962, 2012)) |>
  ggplot(aes(fertility, life_expectancy, col = continent)) +
  geom_point() +
  facet_grid(year~continent)
```
filter %in%
``` r
years <- c(1962, 1980, 1990, 2000, 2012)
continents <- c("Europe", "Asia")
gapminder |> 
  filter(year %in% years & continent %in% continents) |>
  ggplot( aes(fertility, life_expectancy, col = continent)) +
  geom_point() +
  facet_wrap(~year) 
```
log change
``` r
library(ggridges)
p <- gapminder |> 
  filter(year == past_year & !is.na(dollars_per_day)) |>
  ggplot(aes(dollars_per_day, group)) + 
  scale_x_continuous(trans = "log2") 
p  + geom_density_ridges() 
```

## Chapter 12 Summary Statistics
The distribution is symmetric, centered at the average, and most values (about 95%) are within 2 SDs from the average. Here is what the normal distribution looks like when the average is 0 and the SD is 1.



# Links
https://rafalab.dfci.harvard.edu/dsbook/r-basics.html