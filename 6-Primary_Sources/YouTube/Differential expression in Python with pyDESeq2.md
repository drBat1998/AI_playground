Title: Differential expression in Python with pyDESeq2
Author: [[Sanbomics]]
Tags: #youtube #python 


# Notes
```python
conda install pydeseq2
```

```python
from pydeseq2.dds import DeseqDataSet
from pydeseq2.ds import DeseqStats

import pandas as pd
```
import data
```python
counts = pd.read_csv('count_table.csv')
```
set gene id  to index
```python
counts = counts.set_index('Geneid')
```
remove genes that doesn't express
```python
counts = counts[counts.sum(axis = 1) > 0]
```
reshape data
```python
counts = counts.T
```
create metadata
```python
metadata = pd.DataFrame(zip(counts.index, ['C','C','C','C', 'RS', 'RS', 'RS', 'RS']),
                        columns = ['Sample', 'Condition'])
```
set metadata index 
```python
metadata = metadata.set_index('Sample')
```
set DDseq
```python
dds = DeseqDataSet(counts=counts,
            metadata=metadata,
            design='Condition')


#design_factors=["batch", "condition"] = ~ batch + condtion
```

initiate ddseq
```python
dds.deseq2()
```
# Links
https://youtu.be/wIvxFEMQVwg?si=iE88nHvdu30e5FPW