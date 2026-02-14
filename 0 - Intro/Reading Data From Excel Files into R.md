Copying data from Excel and import into R
On Windows system
Open the Excel file containing your data: select and copy the data (ctrl + c)

Type the R code below to import the copied data from the clipboard into R and store the data in a data frame (my_data):
``` R
my_data <- read.table(file = "clipboard", 
                      sep = "\t", header=TRUE)
```
On Mac OSX system
Select and copy the data (Cmd + c)
Use the function pipe(pbpaste) to import the data you’ve copied (with Cmd + c):

```R
my_data <- read.table(pipe("pbpaste"), sep="\t", header = TRUE)
```


Importing Excel files into R using readxl package
Installing and loading readxl package
```R
install.packages("readxl")
library("readxl")
```

```R
# Specify sheet by its name
my_data <- read_excel("my_file.xlsx", sheet = "data")

my_data <- read_excel("my_file.xlsx", na = "---")
```