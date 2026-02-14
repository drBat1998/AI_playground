Title: 27 - CLAHE and Thresholding using opencv in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 

# Notes
Contrast Limited Adaptive Histogram Equalization (CLAHE) - stratch the histogram with limited contrast
``` python
import cv2
import numpy as np
from matplotlib import pyplot as plt

img = cv2.imread("images/Alloy.jpg", 0)
equ = cv2.equalizeHist(img)

plt.hist(equ.flat, bins=100, range=(0,100))

plt.imshow("Original Image", img)
plt.imshow("Equalized", equ)

# Start by creating a CLAHE object (Arguments are optional).
clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8,8))  #Define tile size and clip limit. 
cl1 = clahe.apply(img)
```
then thresholding
```python
# binary thresholding
ret1,th1 = cv2.threshold(clahe_img,185,200,cv2.THRESH_BINARY)

# Otsu's thresholding, automatically finds the threshold point. 
#Compare wth above value provided by us (185)
ret2,th2 = cv2.threshold(clahe_img,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# If working with noisy images
# Clean up noise for better thresholding
# Otsu's thresholding after Gaussian filtering. Canuse median or NLM for beteer edge preserving
```
# Links
next: [[28 - Thresholding and morphological operations using openCV in Python]]
link: https://youtu.be/XfDkg3z3BCg?si=XEBf4UHm_-iINFRm