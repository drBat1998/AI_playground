Title: 305 - What is Cellpose algorithm for segmentation?
Author: [[DigitalSreeni]]
Tags: #youtube #python #bioimage_analysis 


# Notes
[[Cellpose]]


``` python
import numpy as np
import matplotlib.pyplot as plt
from cellpose import models, io
from cellpose.io import imread

io.logger_setup()

model = models.CellposeModel(gpu=True)

# list of files
# PUT PATH TO YOUR FILES HERE!
files = ['/media/carsen/DATA1/TIFFS/onechan.tif']

imgs = [imread(f) for f in files]
nimg = len(imgs)

masks, flows, styles = model.eval(imgs)
```
# Links
https://youtu.be/d3RrbeJKNoc?si=GHAkIJGjc1imOVhc