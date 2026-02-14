R base functions for importing data
read.table() is a general function that can be used to read a file in table format.
read.csv(): for reading “comma separated value” files (“.csv”).
read.csv2(): variant used in countries that use a comma “,” as decimal point and a semicolon “;” as field separators.
read.delim(): for reading “tab-separated value” files (“.txt”). By default, point (“.”) is used as decimal points.
read.delim2(): for reading “tab-separated value” files (“.txt”). By default, comma (“,”) is used as decimal points.

```R
read.csv(file, header = TRUE, sep = ",", dec = ".", ...)
```
header = name of column
sep = what separates columns
dec = is the symbol that used as decimal points.

Reading a file from internet
```R
my_data <- read.delim("https://www.sthda.com/upload/boxplot_format.txt")
```