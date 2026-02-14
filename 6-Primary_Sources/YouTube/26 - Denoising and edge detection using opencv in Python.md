Title: 26 - Denoising and edge detection using opencv in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
``` python
import cv2
from google.colab.patches import cv2_imshow
import matplotlib.pyplot as plt
import numpy as np

img =cv2.imread("/content/drive/MyDrive/data/B2_01_2_3_Propidium Iodide_001.tif", 1)

kernel = np.ones((3,3), np.float32)/9

# filter2D is a custom filter; in this particular case, it is a blur filter.
filt_2d = cv2.filter2D(img, -1, kernel=kernel)


blur_filter = cv2.blur(img, (3,3))

guassian_img = cv2.GaussianBlur(img, (3,3), 0)

# non-linear convolution 
median_blur = cv2.medianBlur(img,3)
biliteral_blur = cv2.bilateralFilter(img, 9, 75,75)
```
Canny edge detection
``` python
edges = cv2.Canny(img, 100, 200)
```

# Links
next: [[27 - CLAHE and Thresholding using opencv in Python]]
link: https://youtu.be/-Qnb8Wv2p1c?si=3QCWJq3YCf3o_shu