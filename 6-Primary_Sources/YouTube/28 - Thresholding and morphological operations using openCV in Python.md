Title: 28 - Thresholding and morphological operations using openCV in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
```python
import cv2
import matplotlib.pyplot as plt
import numpy as np

img = cv2.imread("/content/drive/MyDrive/data/B2_01_2_3_Propidium Iodide_001.tif", 0)


ret,th = cv2.threshold(img,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

kernel = np.ones((3,3),np.uint8)   # 3x3 kernel with all ones. 
erosion = cv2.erode(th,kernel,iterations = 1)  #Erodes pixels based on the kernel defined
dilation = cv2.dilate(erosion,kernel,iterations = 1)  #Apply dilation after erosion to see the effect. 

#Erosion followed by dilation can be a single operation called opening
opening = cv2.morphologyEx(th, cv2.MORPH_OPEN, kernel)  # Compare this image with the previous one

#Closing is opposit, dilation followed by erosion.
closing = cv2.morphologyEx(th, cv2.MORPH_CLOSE, kernel)

#Morphological gradient. This is the difference between dilation and erosion of an image
gradient = cv2.morphologyEx(th, cv2.MORPH_GRADIENT, kernel)

#It is the difference between input image and Opening of the image. 
tophat = cv2.morphologyEx(th, cv2.MORPH_TOPHAT, kernel)

#It is the difference between the closing of the input image and input image.
blackhat = cv2.morphologyEx(img, cv2.MORPH_BLACKHAT, kernel)





```
# Links
next: [[29 - Key points, detectors and descriptors in openCV]]
link: https://youtu.be/WQK_oOWW5Zo?si=MX-I_DmJGedOEJaH