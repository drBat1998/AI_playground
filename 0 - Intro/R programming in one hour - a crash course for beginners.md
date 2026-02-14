Title: R programming in one hour - a crash course for beginners
Author: [[RProgramming101]]
Tags: #R #statistics 

# Notes
tidyverse 
- filter() - select information that we are interested in
- mutate() - change or add a column 
- select() - select specific columns
- arrange()
```R
dataframe %>%
	filter(height>150 & mass < 200)%>%
	mutate(height_in_meters = height/100)%>%
	select(height_in_meters, mass)%>%
	arrange(mass)%>%
	View()
```

## Explore
glimpse(data) - gives information about columns, including names, type, first values
head(data) - first five rows of your data
class(data$column) - give information about the class of variable
length()
names() - name of columns
unique() - unique categories in variables

how to find missing data
```R
missing <- !complete.cases(msleep) # give opposite to complete columns
msleep[missing, ] # show all missing data.
```

## Clean
 select() - select specific columns
 select(ends_with("color")) - select columns whose names end by color
 rename() - changing variable name

```R
data$column <- as.factor(data$column) # to assign factor, aka categorical variables to the variable.
```
changing factor levels
```R
levels(df$sex)
mutate(sex= factor (sex, levels = c("male", "female")))
```
Recode data
consistently rename values
```R
data %>%
	select(sex)%>%
	mutate(sex = recode(sex, "male"= "man",
							"female" = "woman"))
```

Dealing with missing values
1. na.rm
2. drop_na

Duplicates 
distinict()
# Links
https://youtu.be/eR-XRSKsuR4?si=-O2ZF6a_F_JMNAVm