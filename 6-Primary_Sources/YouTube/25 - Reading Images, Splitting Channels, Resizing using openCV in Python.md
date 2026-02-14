Title: 25 - Reading Images, Splitting Channels, Resizing using openCV in Python
Author: [[DigitalSreeni]]
Tags: #youtube #python 


# Notes
``` python
import cv2
from google.colab.patches import cv2_imshow
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread("/content/drive/MyDrive/data/1.png", 1) # 1 for color 0 for gray scale
# BGR not RGB


blue = img[:,:,0]
green = img[:,:,1]
red = img[:,:,2]

#or 

blue, green, red = cv2.split(img)

# merge with cv2
red = cv2.imread("/content/drive/MyDrive/data/B2_01_2_3_Propidium Iodide_001.tif",0)
green = cv2.imread("/content/drive/MyDrive/data/B2_01_1_3_GFP_001.tif",0)
blue  = np.zeros_like(red) 

img_merged = cv2.merge((red, green, blue))
# for some reason merge in RGB not BGR
```
# Links
next: [[26 - Denoising and edge detection using opencv in Python]]
link: https://youtu.be/yj40XoUqo70?si=IXoL9NSRqSdRAJyW