Title: DESeq2 workflow tutorial Differential Gene Expression Analysis Bioinformatics 101
Author: [[Bioinformagician]]
Tags: #youtube #bioinfo 


# Notes
```{r} 
# script to get data from airway package
BiocManager::install("airway")
library(airway)

data(airway)
airway

sample_info <- as.data.frame(colData(airway))
sample_info <- sample_info[,c(2,3)]
sample_info$dex <- gsub('trt', 'treated', sample_info$dex)
sample_info$dex <- gsub('untrt', 'untreated', sample_info$dex)
names(sample_info) <- c('cellLine', 'dexamethasone')
write.table(sample_info, file = "sample_info.csv", sep = ',', col.names = T, row.names = T, quote = F)

countsData <- assay(airway)
write.table(countsData, file = "counts_data.csv", sep = ',', col.names = T, row.names = T, quote = F)
```

# script to perform differential gene expression analysis using DESeq2 package
# setwd("~/Desktop/demo/DESeq2_tutorial/data")
```{r}
# load libraries
library(DESeq2)
library(tidyverse)
library(airway)

```


# Step 1: preparing count data 
```{r}
# read in counts data
counts_data <- read.csv('counts_data.csv')
head(counts_data)
```

```{r}
# read in sample info
colData <- read.csv('sample_info.csv')
```

```{r}
# making sure the row names in colData matches to column names in counts_data
all(colnames(counts_data) %in% rownames(colData))
```

```{r}
# are they in the same order?
all(colnames(counts_data) == rownames(colData))
```

# Step 2: construct a DESeqDataSet object
```{r}
dds <- DESeqDataSetFromMatrix(countData = counts_data,
                       colData = colData,
                       design = ~ dexamethasone)
```


```{r}
dds
```
```{r}
# pre-filtering: removing rows with low gene counts
# keeping rows that have at least 10 reads total
keep <- rowSums(counts(dds)) >= 10
dds <- dds[keep,]

dds
```



```{r}
# set the factor level
dds$dexamethasone <- relevel(dds$dexamethasone, ref = "untreated")
```


# NOTE: collapse technical replicates

# Step 3: Run DESeq 
```{r}
dds <- DESeq(dds)
res <- results(dds)

res
```


# Explore Results ----------------
```{r}
summary(res)


res0.01 <- results(dds, alpha = 0.01)
summary(res0.01)
```


```{r}
# contrasts
resultsNames(dds)

# e.g.: treated_4hrs, treated_8hrs, untreated

results(dds, contrast = c("dexamethasone", "treated_4hrs", "untreated"))
```
```{r}
# MA plot
plotMA(res)
```




# Links
https://youtu.be/OzNzO8qwwp0?si=rDl3yJ6rP7xmd1KA